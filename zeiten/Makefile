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
PIECE1 = gestundete
PIECE2 = wechsel
PIECE3 = grosse
TITLE1 = title_${PIECE1}
TITLE2 = title_${PIECE2}
P2_1 = p2_${PIECE1}
P2_2 = p2_${PIECE2}

dev : ${TITLE1}.a4 ${P2_1}.a4 ${PIECE1}.a4 \
      ${TITLE2}.a4 ${P2_2}.a4 ${PIECE2}.a4 \
      ${PIECE3}.a4
all : \
 ${A4D}/${PIECE1}.pdf  ${USD}/${PIECE1}.pdf \
 ${A4D}/${PIECE2}.pdf  ${USD}/${PIECE2}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE1}.pdf
	upload ${USD}/${PIECE1}.pdf
	upload ${A4D}/${PIECE2}.pdf
	upload ${USD}/${PIECE2}.pdf
	# upload ${MP3D}/${PIECE}.mp3

${A4D}/${PIECE1}.pdf : ${TITLE1}.a4 ${P2_1}.a4 ${PIECE1}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} ${TITLE1}.a4 ${P2_1}.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE1}.pdf : ${TITLE1}.a4 ${P2_1}.a4 ${PIECE1}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} ${TITLE1}.a4 ${P2_1}.a4 - ${BACKPAGE}.a4 \
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

${A4D}/${PIECE2}.pdf : ${TITLE2}.a4 ${P2_2}.a4 ${PIECE2}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} ${TITLE2}.a4 ${P2_2}.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE2}.pdf : ${TITLE2}.a4 ${P2_2}.a4 ${PIECE2}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} ${TITLE2}.a4 ${P2_2}.a4 - ${BACKPAGE}.a4 \
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
	pkill -HUP gv
${PIECE2}.a4 : ${PIECE2}
	${MUSCRIPT} ${PIECE2} > $@
	pkill -HUP gv
${PIECE3}.a4 : ${PIECE3}
	${MUSCRIPT} ${PIECE3} > $@
	pkill -HUP gv
play1 :
	${MUSCRIPT} -midi ${PIECE1} | aplaymidi - &
	# ${MUSCRIPT} -midi ${PIECE1} | midisox - -d trim 33.6 10 &
play2 :
	${MUSCRIPT} -midi ${PIECE2} | aplaymidi - &
play3 :
	${MUSCRIPT} -midi ${PIECE3} | aplaymidi - &
${TITLE1}.a4 : ${TITLE1}
	${UTF2ISO} ${TITLE1} | groff -ms | ${BANNERISE} > $@
${TITLE2}.a4 : ${TITLE2}
	${UTF2ISO} ${TITLE2} | groff -ms | ${BANNERISE} > $@
${P2_1}.a4 : ${P2_1}
	${UTF2ISO} ${P2_1} | groff -ms | ${BANNERISE} > $@
${P2_2}.a4 : ${P2_2}
	${UTF2ISO} ${P2_2} | groff -ms | ${BANNERISE} > $@

letter.a4 : letter
	groff -p -t -e -ms letter > $@
poems.a4 : poems
	groff -p -t -e -ms poems > $@
