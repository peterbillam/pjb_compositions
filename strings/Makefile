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
PIECE1 = strings
PIECE2 = strings_parts
PLAY = mvt2

dev : title.a4 title_parts.a4 strings.a4 strings_parts.a4
all : ${A4D}/${PIECE1}.pdf  ${USD}/${PIECE1}.pdf \
 ${A4D}/${PIECE2}.pdf  ${USD}/${PIECE2}.pdf
mp3 : ${MP3D}/${PIECE1}.mp3
dist1:
	upload ${A4D}/${PIECE1}.pdf
	upload ${USD}/${PIECE1}.pdf
dist2:
	upload ${A4D}/${PIECE2}.pdf
	upload ${USD}/${PIECE2}.pdf

${A4D}/${PIECE1}.pdf : p2.a4 ${PIECE1}.a4 ${BACKPAGE}.a4
	groff -ms title | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE1}.pdf : title.a4 p2.a4 ${PIECE1}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE1}.a4 \
	| ${PSCAT} title.a4 p2.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE1}.xml : ${PIECE1}
	${MUSCRIPT} -xml ${PIECE1} > $@
${SRCD}/${PIECE1}.txt : ${PIECE1}
	cp ${PIECE1} $@
${MP3D}/${PIECE1}.mp3 : ${PIECE1}
	${MUSCRIPT} -midi ${PIECE1} \
	 | fluadity - /home/cds/clas/billam/2015_strings.wav
	${NORMALIZE} /home/cds/clas/billam/2015_strings.wav
	lame -h /home/cds/clas/billam/2015_strings.wav $@

${A4D}/${PIECE2}.pdf : p2.a4 ${PIECE2}.a4 ${BACKPAGE}.a4
	sed s/Score/Parts/ title | groff -ms | ${BANNERISE} > title_parts.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} title_parts.a4 p2.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE2}.pdf : title_parts.a4 p2.a4 ${PIECE2}.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE2}.a4 \
	| ${PSCAT} title_parts.a4 p2.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE2}.xml : ${PIECE2}
	${MUSCRIPT} -xml ${PIECE2} > $@
${SRCD}/${PIECE2}.txt : ${PIECE2}
	cp ${PIECE2} $@

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
title_parts.a4 : title
	sed s/Score/Parts/ title | groff -ms | ${BANNERISE} > $@
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
playall : strings
	muscript -midi strings | midisox_lua - -d stat
mvt1.a4 : mvt1
	${MUSCRIPT} mvt1 > $@
	pkill -HUP gv
mvt2.a4 : mvt2
	${MUSCRIPT} mvt2 > $@
	pkill -HUP gv
mvt3.a4 : mvt3
	${MUSCRIPT} mvt3 > $@
	pkill -HUP gv
strings : mvt1 mvt2 mvt3
	chmod 644 $@
	cat mvt1 mvt2 mvt3 > $@
	chmod 444 $@
strings.a4 : strings
	muscript strings > $@
	pkill -HUP gv
strings_parts.a4 : strings_parts
	muscript strings_parts > $@
	pkill -HUP gv
t.mid : t
	${MUSCRIPT} -midi t > $@
	aplaymidi t.mid &
