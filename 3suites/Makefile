MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
BLURB = /home/pjb/mus/blurb/compositions
FREED = /home/pjb/www/mus/free
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
PIECE1 = 3suites_1
PIECE2 = 3suites_1_alto
PIECE3 = 3suites_1_bass
PIECE4 = 3suites_2
PIECE5 = 3suites_3
PIECE6 = 3suites_1_gtr
TITLE1 = title_1
TITLE2 = title_1_alto
TITLE3 = title_1_bass
TITLE4 = title_2
TITLE5 = title_3
TITLE6 = title_1_gtr
PLAY = 3suites_1_gtr

dev : ${TITLE1}.a4 ${TITLE2}.a4 ${TITLE3}.a4 ${TITLE4}.a4 ${TITLE5}.a4 \
 p2.a4 ${PIECE1}.a4 ${PIECE2}.a4 ${PIECE3}.a4 ${PIECE4}.a4 ${PIECE5}.a4 \
 ${TITLE6}.a4 ${PIECE6}.a4

all : ${A4D}/${PIECE1}.pdf  ${USD}/${PIECE1}.pdf \
	  ${A4D}/${PIECE2}.pdf  ${USD}/${PIECE2}.pdf \
	  ${A4D}/${PIECE3}.pdf  ${USD}/${PIECE3}.pdf \
	  ${A4D}/${PIECE4}.pdf  ${USD}/${PIECE4}.pdf \
	  ${A4D}/${PIECE5}.pdf  ${USD}/${PIECE5}.pdf \
	  ${A4D}/${PIECE6}.pdf  ${USD}/${PIECE6}.pdf
dist1:
	upload ${A4D}/${PIECE1}.pdf
	upload ${USD}/${PIECE1}.pdf
dist2:
	upload ${A4D}/${PIECE2}.pdf
	upload ${USD}/${PIECE2}.pdf
dist3:
	upload ${A4D}/${PIECE3}.pdf
	upload ${USD}/${PIECE3}.pdf
dist4:
	upload ${A4D}/${PIECE4}.pdf
	upload ${USD}/${PIECE4}.pdf
dist5:
	upload ${A4D}/${PIECE5}.pdf
	upload ${USD}/${PIECE5}.pdf
dist6:
	upload ${A4D}/${PIECE6}.pdf
	upload ${USD}/${PIECE6}.pdf

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

${A4D}/${PIECE2}.pdf : ${TITLE2}.a4 p2.a4 ${PIECE2}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} ${TITLE2}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE2}.pdf : ${TITLE2}.a4 p2.a4 ${PIECE2}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} ${TITLE2}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
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

${A4D}/${PIECE3}.pdf : ${TITLE3}.a4 p2.a4 ${PIECE3}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE3}.a4 \
	| ${PSCAT} ${TITLE3}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE3}.pdf : ${TITLE3}.a4 p2.a4 ${PIECE3}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE3}.a4 \
	| ${PSCAT} ${TITLE3}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE3}.xml : ${PIECE3}
	${MUSCRIPT} -xml ${PIECE3} > $@
${SRCD}/${PIECE3}.txt : ${PIECE3}
	cp ${PIECE3} $@
${MP3D}/${PIECE3}.mp3 : ${PIECE3}
	${MUSCRIPT} -midi ${PIECE3} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${A4D}/${PIECE4}.pdf : ${TITLE4}.a4 p2.a4 ${PIECE4}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE4}.a4 \
	| ${PSCAT} ${TITLE4}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE4}.pdf : ${TITLE4}.a4 p2.a4 ${PIECE4}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE4}.a4 \
	| ${PSCAT} ${TITLE4}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE4}.xml : ${PIECE4}
	${MUSCRIPT} -xml ${PIECE4} > $@
${SRCD}/${PIECE4}.txt : ${PIECE4}
	cp ${PIECE4} $@
${MP3D}/${PIECE4}.mp3 : ${PIECE4}
	${MUSCRIPT} -midi ${PIECE4} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${A4D}/${PIECE5}.pdf : ${TITLE5}.a4 p2.a4 ${PIECE5}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE5}.a4 \
	| ${PSCAT} ${TITLE5}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE5}.pdf : ${TITLE5}.a4 p2.a4 ${PIECE5}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE5}.a4 \
	| ${PSCAT} ${TITLE5}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE5}.xml : ${PIECE5}
	${MUSCRIPT} -xml ${PIECE5} > $@
${SRCD}/${PIECE5}.txt : ${PIECE5}
	cp ${PIECE5} $@
${MP3D}/${PIECE5}.mp3 : ${PIECE5}
	${MUSCRIPT} -midi ${PIECE5} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${A4D}/${PIECE6}.pdf : ${TITLE6}.a4 p2.a4 ${PIECE6}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE6}.a4 \
	| ${PSCAT} ${TITLE6}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE6}.pdf : ${TITLE6}.a4 p2.a4 ${PIECE6}.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} ${PIECE6}.a4 \
	| ${PSCAT} ${TITLE6}.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE6}.xml : ${PIECE6}
	${MUSCRIPT} -xml ${PIECE6} > $@
${SRCD}/${PIECE6}.txt : ${PIECE6}
	cp ${PIECE6} $@
${MP3D}/${PIECE6}.mp3 : ${PIECE6}
	${MUSCRIPT} -midi ${PIECE6} | timidity -Ow -c /etc/timidity.cfg -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${TITLE1}.a4 : ${TITLE1}
	groff -ms ${TITLE1} | ${BANNERISE} > $@
${TITLE2}.a4 : ${TITLE1}
	sed 's/flute.*melody/viola or other alto/' ${TITLE1} \
	| groff -ms | ${BANNERISE} > $@
${TITLE3}.a4 : ${TITLE1}
	sed 's/flute.*melody/violoncello or other bass/' ${TITLE1} \
	| groff -ms | ${BANNERISE} > $@
${TITLE4}.a4 : ${TITLE4}
	groff -ms ${TITLE4} | ${BANNERISE} > $@
${TITLE5}.a4 : ${TITLE5}
	groff -ms ${TITLE5} | ${BANNERISE} > $@
${TITLE6}.a4 : ${TITLE1}
	sed 's/4for.*instrument/7transposed for guitar/' ${TITLE1} \
	| groff -ms | ${BANNERISE} > $@

p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > p2.a4

${PIECE1}.a4 : ${PIECE1}
	${MUSCRIPT} ${PIECE1} > $@
	pkill -HUP gv
${PIECE2}.a4 : ${PIECE2}
	${MUSCRIPT} ${PIECE2} > $@
	pkill -HUP gv
${PIECE3}.a4 : ${PIECE3}
	${MUSCRIPT} ${PIECE3} > $@
	pkill -HUP gv
${PIECE4}.a4 : ${PIECE4}
	${MUSCRIPT} ${PIECE4} > $@
	pkill -HUP gv
${PIECE5}.a4 : ${PIECE5}
	${MUSCRIPT} ${PIECE5} > $@
	pkill -HUP gv
${PIECE6}.a4 : ${PIECE6}
	${MUSCRIPT} ${PIECE6} > $@
	pkill -HUP gv

one.mid : one
	${MUSCRIPT} -midi one > $@
one.alto.mid : one.alto
	${MUSCRIPT} -midi one.alto > $@
one.bass.mid : one.bass
	${MUSCRIPT} -midi one.bass > $@
two.mid : two
	${MUSCRIPT} -midi two > $@
three.mid : three
	sed '/pagenum 24/q' three | ${MUSCRIPT} -midi > $@
play : ${PLAY}
	${MUSCRIPT} -midi ${PLAY} | midisox_lua - - stat | aplaymidi -p TiMidity - &
