MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
BACKPAGE = /home/pjb/mus/blurb/cc_backpage.a4
WARNING = /home/pjb/mus/blurb/mus_free_warning_comp.a4
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE = to_erich_jantsch
PLAY = to_erich_jantsch

dev : ${PIECE}.a4 title.a4
all : dev ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
  #${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf

${A4D}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${BACKPAGE}
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${BACKPAGE}
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE} \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE}.xml : ${PIECE}
	${MUSCRIPT} -xml ${PIECE} > $@
${SRCD}/${PIECE}.txt : ${PIECE}
	cp ${PIECE} $@

${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@
	pkill -HUP gv
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
title.a4 : title
	groff -ms title | ${BANNERISE} > $@
play :
	${MUSCRIPT} -midi ${PLAY} | midisox_lua - -d stat
