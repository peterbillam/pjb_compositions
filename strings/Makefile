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
PIECE = strings
PLAY = mvt2

dev : ${PLAY}.a4 title.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf

${A4D}/${PIECE}.pdf : title.a4 p2.a4 ${PIECE}.a4 ${BACKPAGE}.a4
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

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
play :
	muscript -midi ${PLAY} | midisox_lua - -d stat trim 157 fade 0 40 0
play1 :
	muscript -midi mvt1 | midisox_lua - -d stat
play2 :
	muscript -midi mvt2 | midisox_lua - -d stat
play3 :
	muscript -midi mvt3 | midisox_lua - -d stat # trim 210
playall :
	muscript -midi mvt1 mvt2 mvt3 | midisox_lua - -d stat
mvt1.a4 : mvt1
	${MUSCRIPT} mvt1 > $@
	pkill -HUP gv
mvt2.a4 : mvt2
	${MUSCRIPT} mvt2 > $@
	pkill -HUP gv
mvt3.a4 : mvt3
	${MUSCRIPT} mvt3 > $@
	pkill -HUP gv
encore.a4 : encore
	${MUSCRIPT} encore > $@
	pkill -HUP gv
strings : mvt1 mvt2 mvt3
	chmod 644 $@
	cat mvt1 mvt2 mvt3 > $@
	chmod 444 $@
strings.a4 : strings
	muscript strings > $@
	pkill -HUP gv
t.mid : t
	${MUSCRIPT} -midi t > $@
	aplaymidi t.mid &
