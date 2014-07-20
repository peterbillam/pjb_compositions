MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
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
PLAY = g3o_grr

dev : t.mid p2.a4 g3o_gcc.a4 title_gcc.a4 grr.a4 \
 g3o_grr.a4 title_grr.a4 g3o_gvv.a4 title_gvv.a4 titles.jpg
all : \
 ${A4D}/g3o_gcc.pdf  ${USD}/g3o_gcc.pdf  ${MP3D}/g3o_gcc.mp3 \
 ${A4D}/g3o_grr.pdf  ${USD}/g3o_grr.pdf \
 ${A4D}/g3o_gvv.pdf  ${USD}/g3o_gvv.pdf
dist1:
	upload ${A4D}/g3o_gcc.pdf
	upload ${USD}/g3o_gcc.pdf
	upload ${MP3D}/g3o_gcc.mp3
dist2:
	upload ${A4D}/g3o_grr.pdf
	upload ${USD}/g3o_grr.pdf
dist3:
	upload ${A4D}/g3o_gvv.pdf
	upload ${USD}/g3o_gvv.pdf

${A4D}/g3o_gcc.pdf : title_gcc.a4 p2.a4 g3o_gcc.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} g3o_gcc.a4 \
	| ${PSCAT} title_gcc.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/g3o_gcc.pdf : title_gcc.a4 p2.a4 g3o_gcc.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} g3o_gcc.a4 \
	| ${PSCAT} title_gcc.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/g3o_gcc.xml : g3o_gcc
	${MUSCRIPT} -xml g3o_gcc > $@
${SRCD}/g3o_gcc.txt : g3o_gcc
	cp g3o_gcc $@
${MP3D}/g3o_gcc.mp3 : g3o_gcc
	${MUSCRIPT} -midi g3o_gcc | timidity -Ow -o t.wav -
	${NORMALIZE} --peak t.wav
	lame -h t.wav $@
	rm t.wav

${A4D}/g3o_grr.pdf : title_grr.a4 p2.a4 g3o_grr.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} g3o_grr.a4 \
	| ${PSCAT} title_grr.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/g3o_grr.pdf : title_grr.a4 g3o_grr.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} g3o_grr.a4 \
	| ${PSCAT} title_grr.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/g3o_grr.xml : g3o_grr
	${MUSCRIPT} -xml g3o_grr > $@
${SRCD}/g3o_grr.txt : g3o_grr
	cp g3o_grr $@
${MP3D}/g3o_grr.mp3 : g3o_grr
	${MUSCRIPT} -midi g3o_grr | timidity -Ow -o t.wav -
	lame -h t.wav $@
	rm t.wav

${A4D}/g3o_gvv.pdf : title_gvv.a4 p2.a4 g3o_gvv.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} g3o_gvv.a4 \
	| ${PSCAT} title_gvv.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/g3o_gvv.pdf : title_gvv.a4 p2.a4 g3o_gvv.a4 ${FREEBACKPAGE}.a4
	${ADDMESSAGE} g3o_gvv.a4 \
	| ${PSCAT} title_gvv.a4 p2.a4 - ${FREEBACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/g3o_gvv.xml : g3o_gvv
	${MUSCRIPT} -xml g3o_gvv > $@
${SRCD}/g3o_gvv.txt : g3o_gvv
	cp g3o_gvv $@
${MP3D}/g3o_gvv.mp3 : g3o_gvv
	${MUSCRIPT} -midi g3o_gvv | timidity -Ow -o t.wav -
	lame -h t.wav $@
	rm t.wav

g3o_gcc.a4 : g3o_gcc
	${MUSCRIPT} g3o_gcc > $@
g3o_grr.a4 : g3o_grr
	${MUSCRIPT} g3o_grr > $@
g3o_gvv.a4 : g3o_gvv
	${MUSCRIPT} g3o_gvv > $@

t : ${PLAY}
	start_stop ${PLAY} > $@
t.mid : t
	${MUSCRIPT} -midi t > $@
	aplaymidi t.mid &

title_gcc.a4 : title_gcc
	groff -ms title_gcc | ${BANNERISE} > $@
title_grr.a4 : title_grr
	groff -ms title_grr | ${BANNERISE} > $@
title_gvv.a4 : title_gvv
	groff -ms title_gvv | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
titles.jpg : titles.eps
	eps2jpg titles.eps > $@
	display $@
video :
	muscript2video -t /home/pjb/mus/g3o/titles.jpg \
	  -c /home/pjb/mus/blurb/credits.jpg g3o_gcc_video
