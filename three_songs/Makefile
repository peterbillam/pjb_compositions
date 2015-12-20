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
PIECE = songs
PLAY = thomas

dev : title.a4 p2.a4 ${PIECE}.a4 seth.a4
all :  ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf

${A4D}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	groff -ms title | ${BANNERISE} > $@
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${BACKPAGE}.a4 \
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

${PIECE}.a4 : kerouac thomas
	${MUSCRIPT} kerouac thomas > $@
	pkill -HUP gv

kerouac.a4 : kerouac
	/home/pbin/muscript kerouac > $@
	pkill -HUP gv
seth.a4 : seth
	/home/pbin/muscript seth > $@
	pkill -HUP gv
thomas.a4 : thomas
	/home/pbin/muscript thomas > $@
	pkill -HUP gv

kerouac.mid : kerouac
	/home/pbin/muscript_lua -midi kerouac > $@
seth.mid : seth
	/home/pbin/muscript_lua -midi seth > $@
thomas.mid : thomas
	/home/pbin/muscript_lua -midi thomas > $@

play :
	/home/pbin/muscript_lua -midi ${PLAY} | aplaymidi -p TiM - &

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
