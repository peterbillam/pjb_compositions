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
WAVD = /home/pjb/wav/canon
BACKPAGE = /home/pjb/mus/blurb/cc_backpage
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE = canon
PLAY = canon

dev : 1.a4 2.a4 3.a4 4.a4 5.a4 6.a4 7.a4 8.a4 9.a4 9a.a4 10.a4 11.a4 12.a4 \
 ${PIECE} title.a4 p2.a4
all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
 # ${MP3D}/${PIECE}.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
wav : ${WAVD}/01.wav ${WAVD}/02.wav ${WAVD}/03.wav ${WAVD}/04.wav \
	  ${WAVD}/05.wav ${WAVD}/06.wav ${WAVD}/07.wav ${WAVD}/08.wav \
	  ${WAVD}/09.wav ${WAVD}/10.wav ${WAVD}/11.wav ${WAVD}/12.wav
mp3 : ${MP3D}/canon01.mp3 ${MP3D}/canon02.mp3 ${MP3D}/canon03.mp3 \
	  ${MP3D}/canon04.mp3 ${MP3D}/canon05.mp3 ${MP3D}/canon06.mp3 \
	  ${MP3D}/canon07.mp3 ${MP3D}/canon08.mp3 ${MP3D}/canon09.mp3 \
	  ${MP3D}/canon10.mp3 ${MP3D}/canon11.mp3 ${MP3D}/canon12.mp3

${FREED}/${PIECE}.pdf : ${PIECE}.a4 ${BACKPAGE}.a4
	groff -ms title | ${BANNERISE} > title.a4
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${BACKPAGE}.a4 \
	| ${A42US} -c \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

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

${PIECE} : 1 2 3 4 5 6 7 8 9 10 11 12
	cat 1 2 3 4 5 6 7 8 9 10 11 12 > $@
${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@

1.a4 : 1
	${MUSCRIPT} 1 > $@
play1 :
	${MUSCRIPT} -midi 1 | aplaymidi - &
${WAVD}/01.wav : 1
	${MUSCRIPT} -midi 1 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon01.mp3 : ${WAVD}/01.wav
	lame -h ${WAVD}/01.wav $@
	upload $@

2.a4 : 2
	${MUSCRIPT} 2 > $@
play2 :
	${MUSCRIPT} -midi 2 | aplaymidi - &
${WAVD}/02.wav : 2
	${MUSCRIPT} -midi 2 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon02.mp3 : ${WAVD}/02.wav
	lame -h ${WAVD}/02.wav $@
	upload $@

#3 : make3
#	perl make3 > $@
3.a4 : 3
	${MUSCRIPT} 3 > $@
play3 :
	${MUSCRIPT} -midi 3 | aplaymidi - &
${WAVD}/03.wav : 3
	${MUSCRIPT} -midi 3 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon03.mp3 : ${WAVD}/03.wav
	lame -h ${WAVD}/03.wav $@
	upload $@

#4 : make4
#	perl make4 > $@
4.a4 : 4
	${MUSCRIPT} 4 > $@
play4 :
	${MUSCRIPT} -midi 4 | aplaymidi - &
${WAVD}/04.wav : 4
	${MUSCRIPT} -midi 4 | timidity -Ow -o $@ -
	normalize-audio --peak $@
canon4.mp3: 4
	${MUSCRIPT} -midi 4 | timidity -Ow -o 4.wav -
	normalize-audio 4.wav
	lame -h 4.wav canon4.mp3
	split -b 200000 canon4.mp3
	# now use pftp to  mput x*  to public_html/mus/arr/mp3/
	# and     ssh -p 2223 pjb3265@loki.webcity.com.au
	# to do   cd ~/public_html/mus/comp/mp3 ; cat x* > canon4.mp3
${MP3D}/canon04.mp3 : ${WAVD}/04.wav
	lame -h ${WAVD}/04.wav $@
	upload $@

#5 : make5
#	perl make5 > $@
5.a4 : 5
	${MUSCRIPT} 5 > $@
play5 :
	${MUSCRIPT} -midi 5 | aplaymidi - &
${WAVD}/05.wav : 5
	${MUSCRIPT} -midi 5 | timidity -Ow -o $@ -
	normalize-audio --peak $@
canon5.mp3: 5
	${MUSCRIPT} -midi 5 | timidity -Ow -o 5.wav -
	normalize-audio 5.wav
	lame -h 5.wav canon5.mp3
	split -b 200000 canon5.mp3
	# now use pftp to  mput x*  to public_html/mus/arr/mp3/
	# and     ssh -p 2223 pjb3265@loki.webcity.com.au
	# to do   cd ~/public_html/mus/comp/mp3 ; cat x* > canon5.mp3
${MP3D}/canon05.mp3 : ${WAVD}/05.wav
	lame -h ${WAVD}/05.wav $@
	upload $@

#6 : make6
#	perl make6 > $@
6.a4 : 6
	${MUSCRIPT} 6 > $@
play6 :
	${MUSCRIPT} -midi 6 | aplaymidi - &
${WAVD}/06.wav : 6
	${MUSCRIPT} -midi 6 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon06.mp3 : ${WAVD}/06.wav
	lame -h ${WAVD}/06.wav $@
	upload $@

#7 : make7
#	perl make7 > $@   # all superseded by t7 :-)
7.a4 : 7
	${MUSCRIPT} 7 > $@
play7 :
	sed  's/^#=/=/' 7 | ${MUSCRIPT} -midi | aplaymidi - &
${WAVD}/07.wav : 7
	sed  's/^#=/=/' 7 | ${MUSCRIPT} -midi | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon07.mp3 : ${WAVD}/07.wav
	lame -h ${WAVD}/07.wav $@
	upload $@

8.a4 : 8
	${MUSCRIPT} 8 > $@
play8 :
	${MUSCRIPT} -midi 8 | aplaymidi - & # | midisox - - trim 60
${WAVD}/08.wav : 8
	${MUSCRIPT} -midi 8 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon08.mp3 : ${WAVD}/08.wav
	lame -h ${WAVD}/08.wav $@
	upload $@

#9 : make9
#	perl make9 > $@
9.a4 : 9
	${MUSCRIPT} 9 > $@
play9 :
	${MUSCRIPT} -midi 9 | aplaymidi - &  # midisox_pl - -d trim 110
9a.a4 : 9a
	${MUSCRIPT} 9a > $@
play9a :
	${MUSCRIPT} -midi 9a | aplaymidi - &
9b.a4 : 9b
	${MUSCRIPT} 9b > $@
play9b :
	${MUSCRIPT} -midi 9b | aplaymidi - &
${WAVD}/09.wav : 9
	${MUSCRIPT} -midi 9 | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon09.mp3 : ${WAVD}/09.wav
	lame -h ${WAVD}/09.wav $@
	upload $@

#10 : make10
#	perl make10 > $@
10.a4 : 10
	${MUSCRIPT} 10 > $@
play10 :
	${MUSCRIPT} -midi 10 | aplaymidi - & # midisox - -d trim 135.5 & #
${WAVD}/10.wav : 10
	${MUSCRIPT} -midi 10| timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon10.mp3 : ${WAVD}/10.wav
	lame -h ${WAVD}/10.wav $@
	upload $@

#11 : make11
#	perl make11 > $@
11.a4 : 11
	${MUSCRIPT} 11 > $@
	pkill -HUP gv
play11 : 11
	sed 's/^#=/=/' 11 | ${MUSCRIPT} -midi | aplaymidi - & # midisox_pl - -d trim 0 139 & #
${WAVD}/11.wav : 11
	sed 's/^#=/=/' 11 | ${MUSCRIPT} -midi | timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon11.mp3 : ${WAVD}/11.wav
	lame -h ${WAVD}/11.wav $@
	upload $@

12.a4 : 12
	${MUSCRIPT} 12 > $@
play12 :
	${MUSCRIPT} -midi 12 | aplaymidi - &
${WAVD}/12.wav : 12
	${MUSCRIPT} -midi 12| timidity -Ow -o $@ -
	normalize-audio --peak $@
${MP3D}/canon12.mp3 : ${WAVD}/12.wav
	lame -h ${WAVD}/12.wav $@
	upload $@

play : canon
	sed 's/^#=/\=/' ${PLAY} | ${MUSCRIPT} -midi | aplaymidi -p 128 - &
	# ${MUSCRIPT} -midi ${PLAY} | midisox - -d trim 34 &
title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@

mt.a4 : mt
	${MUSCRIPT} mt > $@
playmt :
	${MUSCRIPT} -midi mt | aplaymidi - &

4_titles.jpg : 4_titles.eps
	eps2jpg 4_titles.eps > $@
	display $@
11_titles.jpg : 11_titles.eps
	eps2jpg 11_titles.eps > $@
	display $@
video : 11_titles.jpg
	muscript2video -t 11_titles.jpg \
	  -c /home/pjb/mus/blurb/credits.jpg 11_video

