MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
BACKPAGE = /home/pjb/mus/blurb/cc_backpage
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE1 = quintet_score
PIECE2 = quintet_parts
PLAY = quintet_score

dev : title.a4 ${PIECE1}.a4 ${PIECE2}.a4
all : \
 ${A4D}/${PIECE1}.pdf  ${USD}/${PIECE1}.pdf \
 ${A4D}/${PIECE2}.pdf  ${USD}/${PIECE2}.pdf
 # ${MP3D}/${PIECE1}.mp3
dist:
	upload ${A4D}/${PIECE1}.pdf
	upload ${USD}/${PIECE1}.pdf
	upload ${A4D}/${PIECE2}.pdf
	upload ${USD}/${PIECE2}.pdf
	# upload ${MP3D}/${PIECE1}.mp3

${A4D}/${PIECE1}.pdf : title.a4 ${PIECE1}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE1}.pdf : title.a4 ${PIECE1}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE}.a4 \
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

${A4D}/${PIECE2}.pdf : title2.a4 ${PIECE2}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} title2.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE2}.pdf : title2.a4 ${PIECE2}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} title2.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE2}.xml : ${PIECE2}
	${MUSCRIPT} -xml ${PIECE2} > $@
${SRCD}/${PIECE2}.txt : ${PIECE2}
	cp ${PIECE2} $@
${MP3D}/${PIECE2}.mp3 : ${PIECE2}
	${MUSCRIPT} -midi ${PIECE2} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${PIECE1}.a4 : ${PIECE1}
	${MUSCRIPT} ${PIECE1} > $@
${PIECE2}.a4 : ${PIECE2}
	${MUSCRIPT} ${PIECE2} > $@

flute.a4 : flute
	${MUSCRIPT} flute > $@
trombone.a4 : trombone
	${MUSCRIPT} trombone > $@
piano.a4 : piano
	${MUSCRIPT} piano > $@
bass.a4 : bass 
	${MUSCRIPT} bass > $@
perc.a4 : perc
	${MUSCRIPT} perc > $@
t.mid : quintet_score
	start_stop quintet_score | ${MUSCRIPT} -midi > $@
	aplaymidi $@ &

piano-duo.a4 : piano-duo
	${MUSCRIPT} piano-duo > $@

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
title2.a4 : title
	sed 's/This score/These parts/' title | groff -ms | ${BANNERISE} > $@

