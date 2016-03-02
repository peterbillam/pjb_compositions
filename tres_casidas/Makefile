MUSCRIPT = /home/pbin/muscript_lua
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
PIECE = tres

dev : title.a4 p2.a4 p3.a4 p21.a4 ${PIECE}.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
	# upload ${MP3D}/${PIECE}.mp3

${A4D}/${PIECE}.pdf : ${PIECE}.a4 ${BACKPAGE}.a4
	${UTF2ISO} title | groff -ms | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 p3.a4 - p21.a4 ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE}.a4 \
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

${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} -a4 ${PIECE} > $@
	pkill -HUP gv
title.a4 : title
	${UTF2ISO} title | groff -ms | ${BANNERISE} > $@
p2.a4 : p2
	${UTF2ISO} p2 | groff -ms | ${BANNERISE} > $@
p3.a4 : p3
	${UTF2ISO} p3 | groff -ms | ${BANNERISE} > $@
p21.a4 : p21
	${UTF2ISO} p21 | groff -ms | ${BANNERISE} > $@
play :
	${MUSCRIPT} -midi ${PIECE} | midisox_lua - -d stat trim 100 fade 0 18 0
playall :
	grep -v 'midi off' ${PIECE} | ${MUSCRIPT} -midi | midisox_lua - -d stat

