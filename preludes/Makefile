MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
BLURB = /home/pjb/mus/blurb/compositions
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
FREEBACKPAGE = /home/pjb/mus/blurb/cc_backpage
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE = preludes
WAVDIR=/home/cds/clas/billam/2003_preludes

dev : ${PIECE}.a4 title.a4 p2.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf

${A4D}/${PIECE}.pdf : ${PIECE}.a4 ${FREEBACKPAGE}.a4
	groff -ms title | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE}.xml : ${PIECE}
	${MUSCRIPT} -xml ${PIECE} > $@
${SRCD}/${PIECE}.txt : ${PIECE}
	cp ${PIECE} $@
${MP3D}/${PIECE}.mp3 : ${PIECE}
	${MUSCRIPT} -midi ${PIECE} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${PIECE} : prelude_1 prelude_2 prelude_3
	chmod 644 $@
	cat prelude_1 prelude_2 prelude_3 > $@
	chmod 444 $@
${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} -a4 ${PIECE} > $@
	pkill -HUP gv
${PIECE}.mid : ${PIECE}
	${MUSCRIPT} -midi ${PIECE} > $@
title.a4 :
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
play :
	${MUSCRIPT} -midi ${PIECE} | midisox_lua - -d stat
play1 :
	${MUSCRIPT} -midi prelude_1 | midisox_lua - -d stat
play2 :
	${MUSCRIPT} -midi prelude_2 | midisox_lua - -d stat
play3 :
	${MUSCRIPT} -midi prelude_3 | midisox_lua - -d stat
wav : ${WAVDIR}/prelude_1.wav ${WAVDIR}/prelude_2.wav ${WAVDIR}/prelude_3.wav
${WAVDIR}/prelude_1.wav : prelude_1
	${MUSCRIPT} -midi prelude_1 | fluadity - $@
	${NORMALIZE} --peak $@
${WAVDIR}/prelude_2.wav : prelude_2
	${MUSCRIPT} -midi prelude_2 | fluadity - $@
	${NORMALIZE} -a -15dBFS $@
${WAVDIR}/prelude_3.wav : prelude_3
	${MUSCRIPT} -midi prelude_3 | fluadity - $@
	${NORMALIZE} --peak -a -8dBFS $@

preludes_titles.jpg : preludes_titles.eps
	eps2jpg preludes_titles.eps > $@
	display $@
video : preludes_titles.jpg
	muscript2video -t preludes_titles.jpg \
	  -c /home/pjb/mus/blurb/credits.jpg preludes_video
