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

#PIECE = bossa
#PIECE = glooming
#PIECE = twinkle
#PIECE = bossaboogle
PIECE = warmpipe

guitar_pieces.ps : guitar_pieces
	${MUSCRIPT} guitar_pieces > $@
	pkill -HUP gv
edit :
	vi ${PIECE}
	cat twinkle glooming warmpipe > guitar_pieces
	# ${MUSCRIPT} ${PIECE} > ${PIECE}.ps
	${MUSCRIPT} guitar_pieces > guitar_pieces.ps
	pkill -HUP gv

all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
	# upload ${MP3D}/${PIECE}.mp3

${A4D}/${PIECE}.pdf : title.ps ${PIECE}.ps ${BACKPAGE}
	${ADDMESSAGE} ${PIECE}.ps \
	| ${PSCAT} title.ps - ${BACKPAGE} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.ps ${PIECE}.ps ${BACKPAGE}
	${ADDMESSAGE} ${PIECE}.ps \
	| ${PSCAT} title.ps - ${BACKPAGE} \
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

guitar_pieces : twinkle glooming warmpipe
	cat twinkle glooming warmpipe > $@

${PIECE}.ps : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@
play :
	${MUSCRIPT} -midi ${PIECE} | midisox_lua - -d stat
title.ps : title
	groff -ms title | ${BANNERISE} > $@
