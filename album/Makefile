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
PIECE = album
PLAY = well_i_never

dev : title.a4 p2.a4 p3.a4 album.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
mp3 : ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf

${A4D}/${PIECE}.pdf : p2.a4 p3.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	groff -ms title | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 p3.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 p2.a4 p3.a4 ${PIECE}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 p2.a4 p3.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE}.xml : ${PIECE}
	${MUSCRIPT} -xml ${PIECE} > $@
${SRCD}/${PIECE}.txt : ${PIECE}
	cp ${PIECE} $@
${MP3D}/${PIECE}.mp3 : ${PIECE}
	${MUSCRIPT} -midi ${PIECE} \
	 | fluadity - /home/cds/clas/billam/2015_album.wav
	${NORMALIZE} /home/cds/clas/billam/2015_album.wav
	lame -h /home/cds/clas/billam/2015_album.wav $@

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
p3.a4 : p3
	groff -ms p3 | ${BANNERISE} > $@
play :
	muscript -midi ${PLAY} | midisox_lua - -d stat # trim 60 fade 0 20 0
playall :
	muscript -midi ${PIECE} | midisox_lua - -d stat
edit :
	vi ${PLAY}
	make play dev
album: sometimes konkerado web only_the_glories well_i_never remember the_spell
	chmod 644 $@
	cat sometimes konkerado web only_the_glories \
	  well_i_never remember the_spell > $@
	chmod 444 $@
album.a4 : album
	muscript album > $@
	pkill -HUP gv
t.mid : t
	${MUSCRIPT} -midi t > $@
	aplaymidi t.mid &
