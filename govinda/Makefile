MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
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
PIECE = govinda
PLAY = govinda

dev : nacht.a4 de_profundis.a4 ${PIECE}.a4 title.a4 p2.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
dist : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
mp3 : ${MP3D}/${PIECE}.mp3

${A4D}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${FREEBACKPAGE}.a4
	utf2iso title | groff -ms | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
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

${PIECE} : de_profundis nacht
	cat de_profundis nacht > $@
${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@

nacht.a4 : nacht
	${MUSCRIPT} nacht > $@
	pkill -HUP gv
nacht_high.a4 : nacht_high
	${MUSCRIPT} nacht_high > $@
	pkill -HUP gv
nacht_low.a4 : nacht_low
	${MUSCRIPT} nacht_low > $@
	pkill -HUP gv
nacht_mixed.a4 : nacht_mixed
	${MUSCRIPT} nacht_mixed > $@
	pkill -HUP gv
de_profundis.a4 : de_profundis
	${MUSCRIPT} de_profundis > $@
	pkill -HUP gv
${WAVD}/02.wav : 2
	${MUSCRIPT} -midi 2 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon02.mp3 : ${WAVD}/02.wav
	lame -h ${WAVD}/02.wav $@
	upload $@

play :
	${MUSCRIPT} -midi ${PLAY} | aplaymidi - &
	# ${MUSCRIPT} -midi ${PLAY} | midisox_pl - -d trim 128 &
title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	utf2iso p2 | groff -ms | ${BANNERISE} > $@
