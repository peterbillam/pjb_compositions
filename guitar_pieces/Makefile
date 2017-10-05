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

#DEV  = twinkled
#DEV  = waveride
#DEV  = twowheel
DEV  = glooming
#DEV  = dawnpipe
#DEV  = talksoft
#DEV  = bluemoon
#DEV  = pluckier
PIECE = guitar_pieces

#guitar_pieces.ps : guitar_pieces
#	${MUSCRIPT} guitar_pieces > $@
#	pkill -HUP gv
edit :
	vi ${DEV}
	# ${MUSCRIPT} ${DEV} > ${DEV}.ps
	cat twinkled waveride twowheel glooming \
	  dawnpipe talksoft bluemoon pluckier > guitar_pieces
	${MUSCRIPT} guitar_pieces > guitar_pieces.ps
	pkill -HUP gv

all : ${A4D}/guitar_pieces.pdf  ${USD}/guitar_pieces.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/guitar_pieces.pdf
	upload ${USD}/guitar_pieces.pdf
	# upload ${MP3D}/${PIECE}.mp3

${A4D}/${PIECE}.pdf : title.ps ${PIECE}.ps ${BACKPAGE}
	groff -ms title | ${BANNERISE} > title.ps
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

guitar_pieces : twinkled waveride twowheel glooming \
 dawnpipe talksoft bluemoon pluckier
	cat twinkled waveride twowheel glooming \
	  dawnpipe talksoft bluemoon pluckier > $@
sketches.ps : sketches
	${MUSCRIPT} sketches > $@
	pkill -HUP gv
${PIECE}.ps : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@
	pkill -HUP gv
play :
	${MUSCRIPT} -midi ${DEV} | midisox_lua - -d stat
playall :
	${MUSCRIPT} -midi ${PIECE} | midisox_lua - -d stat
title.ps : title
	groff -ms title | ${BANNERISE} > $@
