MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
BLURB = /home/pjb/mus/blurb/compositions
FREED = /home/pjb/www/mus/free
COMPD = /home/pjb/www/mus/comp
ARRD  = /home/pjb/www/mus/arr
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
FREEBACKPAGE = /home/pjb/mus/blurb/cc_backpage
WARNING = /home/pjb/mus/blurb/mus_free_warning_arr.a4
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE1 = divisions
PIECE2 = carr
TITLE1 = title
TITLE2 = title_carr
PLAY = carr
# perl carr2score | muscript -midi | midisox_lua - - pitch 1:-1200 vol 1:+15 2:-20 | aplaymidi -p TiM - &
# perl carr2score | muscript -midi | aplaymidi -p Roland - &

dev : title.a4 title_carr.a4 p2.a4 ${PIECE1}.a4 ${PIECE2}.a4

all : ${A4D}/${PIECE1}.pdf  ${USD}/${PIECE1}.pdf \
	${ARRD}/a4/${PIECE2}.pdf  ${ARRD}/us/${PIECE2}.pdf \
	${ARRD}/xml/${PIECE2}.xml  ${ARRD}/src/${PIECE2}.txt
dist1:
	upload ${A4D}/${PIECE1}.pdf
	upload ${USD}/${PIECE1}.pdf
dist2:
	upload ${ARRD}/a4/${PIECE2}.pdf
	upload ${ARRD}/us/${PIECE2}.pdf
	upload ${ARRD}/xml/${PIECE2}.xml
	upload ${ARRD}/src/${PIECE2}.txt


${FREED}/${PIECE1}.pdf : title.a4 p2.a4 ${WARNING} ${PIECE1}.a4 ${FREEBACKPAGE}.a4
	groff -ms title | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} title.a4 ${WARNING} p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} -c \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${FREED}/${PIECE2}.pdf : title_carr.a4 ${WARNING} p2.a4 ${PIECE2}.a4 ${FREEBACKPAGE}.a4
	groff -ms title_carr | ${BANNERISE} > title_carr.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} title_carr.a4 ${WARNING} p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} -c \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${A4D}/${PIECE1}.pdf : ${TITLE1}.a4 p2.a4 ${PIECE1}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} ${TITLE1}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE1}.pdf : ${TITLE1}.a4 p2.a4 ${PIECE1}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} ${TITLE1}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE1}.xml : ${PIECE1}
	${MUSCRIPT} -xml ${PIECE1} > $@
${SRCD}/${PIECE1}.txt : ${PIECE1}
	cp ${PIECE1} $@
${MP3D}/${PIECE1}.mp3 : ${PIECE1}
	${MUSCRIPT} -midi ${PIECE1} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${ARRD}/a4/${PIECE2}.pdf : ${TITLE2}.a4 p2.a4 ${PIECE2}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} ${TITLE2}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${ARRD}/us/${PIECE2}.pdf : ${TITLE2}.a4 p2.a4 ${PIECE2}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} ${TITLE2}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${ARRD}/xml/${PIECE2}.xml : ${PIECE2}
	${MUSCRIPT} -xml ${PIECE2} > $@
${ARRD}/src/${PIECE2}.txt : ${PIECE2}
	cp ${PIECE2} $@
${ARRD}/mp3/${PIECE2}.mp3 : ${PIECE2}
	${MUSCRIPT} -midi ${PIECE2} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${PIECE1}.a4 : ${PIECE1} ${MUSCRIPT}
	${MUSCRIPT} ${PIECE1} > $@
${PIECE2}.a4 : ${PIECE2} ${MUSCRIPT}
	${MUSCRIPT} ${PIECE2} > $@
play :
	${MUSCRIPT} -midi ${PLAY} | aplaymidi - &

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
title_carr.a4 : title_carr
	groff -ms title_carr | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
