MUSCRIPT = /home/pbin/muscript
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
WAVD = /home/pjb/wav/fanfare
BACKPAGE = /home/pjb/mus/blurb/cc_backpage
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
PIECE = fanfare
PLAY = ${PIECE}

dev : ${PLAY}.a4 title.a4

all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf

dist : 
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf

clean :
	rm title.a4 ${PIECE}.a4

${A4D}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	groff -ms title | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${USD}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
play :
	${MUSCRIPT} -midi ${PLAY} | aplaymidi -p TiMidity -

${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@
	pkill -HUP gv

titles.jpg : titles.eps
	eps2jpg titles.eps > $@
	display $@

wav : ${PIECE}
	muscript -midi ${PIECE} | timidity -Ow -o $@ -

