MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
BACKPAGE = /home/pjb/mus/blurb/cc_backpage.a4
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE = rounds

dev : title.a4 p2.a4 ${PIECE}.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
	# upload ${MP3D}/${PIECE}.mp3
energymp3: ${MP3D}/energy.mp3

${A4D}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${BACKPAGE}
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${BACKPAGE} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${BACKPAGE}
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${BACKPAGE} \
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

${MP3D}/energy.mp3 : energy
	${MUSCRIPT} -midi energy | timidity -Ow -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@
play :
	${MUSCRIPT} -midi ${PIECE} | aplaymidi - &

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
