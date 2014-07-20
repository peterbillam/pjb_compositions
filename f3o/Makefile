MUSCRIPT = /home/pbin/muscript
NORMALIZE = /usr/bin/normalize-audio
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
FREEBACKPAGE = /home/pjb/mus/blurb/cc_backpage.a4
WARNING = /home/pjb/mus/blurb/mus_free_warning_comp.a4
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
UTF2ISO = /home/pbin/utf2iso
PIECE = f3o
PLAY = f3o_2

# Must create practice .mid files, and/or .mp3 files, at different tempi,
# also with and without metronome clicks,
# also with f1 missing for flute 1 to practice with; likewise f2 and f3
# say 3 tempi * 2 metronome? * 3 flutes = 18 different midi or mp3 files :-)
# Perhaps individual parts, meaning fewer pages and/or better page-turns ?
# Must give muscript the long shake ~~~~~~~~-style trill, for the Variations
dev : f3o_1.a4 f3o_1_parts.a4 f3o_2.a4 f3o_3.a4 f3o title.a4 titles.jpg
all : f3o.a4 ${MP3D}/f3o_1.mp3 ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf
mid : f3o_1_f1_fast_click.mid f3o_1_f2_fast_click.mid f3o_1_f3_fast_click.mid \
 f3o_1_f1_med_click.mid f3o_1_f2_med_click.mid f3o_1_f3_med_click.mid \
 f3o_1_f1_slow_click.mid f3o_1_f2_slow_click.mid f3o_1_f3_slow_click.mid \
 f3o_1_f1_fast.mid f3o_1_f2_fast.mid f3o_1_f3_fast.mid \
 f3o_1_f1_med.mid f3o_1_f2_med.mid f3o_1_f3_med.mid \
 f3o_1_f1_slow.mid f3o_1_f2_slow.mid f3o_1_f3_slow.mid
mp3 : ${MP3D}/f3o_1_f1_fast_click.mp3 \
 ${MP3D}/f3o_1_f2_fast_click.mp3 \
 ${MP3D}/f3o_1_f3_fast_click.mp3 \
 ${MP3D}/f3o_1_f1_med_click.mp3 \
 ${MP3D}/f3o_1_f2_med_click.mp3 \
 ${MP3D}/f3o_1_f3_med_click.mp3 \
 ${MP3D}/f3o_1_f1_slow_click.mp3 \
 ${MP3D}/f3o_1_f2_slow_click.mp3 \
 ${MP3D}/f3o_1_f3_slow_click.mp3 \
 ${MP3D}/f3o_1_f1_fast.mp3 \
 ${MP3D}/f3o_1_f2_fast.mp3 \
 ${MP3D}/f3o_1_f3_fast.mp3 \
 ${MP3D}/f3o_1_f1_med.mp3 \
 ${MP3D}/f3o_1_f2_med.mp3 \
 ${MP3D}/f3o_1_f3_med.mp3 \
 ${MP3D}/f3o_1_f1_slow.mp3 \
 ${MP3D}/f3o_1_f2_slow.mp3 \
 ${MP3D}/f3o_1_f3_slow.mp3
dist:
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
	# upload ${MP3D}/${PIECE}.mp3
distmp3 :
	upload ${MP3D}/f3o_1_f1_fast_click.mp3
	upload ${MP3D}/f3o_1_f2_fast_click.mp3
	upload ${MP3D}/f3o_1_f3_fast_click.mp3
	upload ${MP3D}/f3o_1_f1_med_click.mp3
	upload ${MP3D}/f3o_1_f2_med_click.mp3
	upload ${MP3D}/f3o_1_f3_med_click.mp3
	upload ${MP3D}/f3o_1_f1_slow_click.mp3
	upload ${MP3D}/f3o_1_f2_slow_click.mp3
	upload ${MP3D}/f3o_1_f3_slow_click.mp3
	upload ${MP3D}/f3o_1_f1_fast.mp3
	upload ${MP3D}/f3o_1_f2_fast.mp3
	upload ${MP3D}/f3o_1_f3_fast.mp3
	upload ${MP3D}/f3o_1_f1_med.mp3
	upload ${MP3D}/f3o_1_f2_med.mp3
	upload ${MP3D}/f3o_1_f3_med.mp3
	upload ${MP3D}/f3o_1_f1_slow.mp3
	upload ${MP3D}/f3o_1_f2_slow.mp3
	upload ${MP3D}/f3o_1_f3_slow.mp3

${A4D}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${FREEBACKPAGE}
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${FREEBACKPAGE} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}.pdf : title.a4 ${PIECE}.a4 ${FREEBACKPAGE}
	${ADDMESSAGE} ${PIECE}.a4 \
	| ${PSCAT} title.a4 - ${FREEBACKPAGE} \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=letter -sOutputFile=$@ -
${XMLD}/${PIECE}.xml : ${PIECE}
	${MUSCRIPT} -xml ${PIECE} > $@
${SRCD}/${PIECE}.txt : ${PIECE}
	cp ${PIECE} $@

f3o : f3o_1 f3o_1_parts
	chmod 664 $@
	cat f3o_1 f3o_1_parts > $@
	chmod 444 $@
f3o_1.a4 : f3o_1
	${MUSCRIPT} f3o_1 > $@
	pkill -HUP gv
f3o_1.mid : f3o_1
	muscript -midi f3o_1 > $@
f3o_1_click.mid : f3o_1
	perl -pe 's/^#=9/=9/' f3o_1 | muscript -midi > $@
f3o_1_f1_fast_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 1 2 9
f3o_1_f2_fast_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 0 2 9
f3o_1_f3_fast_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 0 1 9
f3o_1_f1_med_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 1 2 9 tempo 0.9
f3o_1_f2_med_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 0 2 9 tempo 0.9
f3o_1_f3_med_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 0 1 9 tempo 0.9
f3o_1_f1_slow_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 1 2 9 tempo 0.81
f3o_1_f2_slow_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 0 2 9 tempo 0.81
f3o_1_f3_slow_click.mid : f3o_1_click.mid
	midisox_lua f3o_1_click.mid $@ mixer 0 1 9 tempo 0.81
f3o_1_f1_fast.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 1 2
f3o_1_f2_fast.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 0 2
f3o_1_f3_fast.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 0 1
f3o_1_f1_med.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 1 2 tempo 0.9
f3o_1_f2_med.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 0 2 tempo 0.9
f3o_1_f3_med.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 0 1 tempo 0.9
f3o_1_f1_slow.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 1 2 tempo 0.81
f3o_1_f2_slow.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 0 2 tempo 0.81
f3o_1_f3_slow.mid : f3o_1.mid
	midisox_lua f3o_1.mid $@ mixer 0 1 tempo 0.81

${MP3D}/f3o_1_f1_fast_click.mp3 : f3o_1_f1_fast_click.mid
	timidity -Ow -o t.wav f3o_1_f1_fast_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f2_fast_click.mp3 : f3o_1_f2_fast_click.mid
	timidity -Ow -o t.wav f3o_1_f2_fast_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f3_fast_click.mp3 : f3o_1_f3_fast_click.mid
	timidity -Ow -o t.wav f3o_1_f3_fast_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f1_med_click.mp3 : f3o_1_f1_med_click.mid
	timidity -Ow -o t.wav f3o_1_f1_med_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f2_med_click.mp3 : f3o_1_f2_med_click.mid
	timidity -Ow -o t.wav f3o_1_f2_med_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f3_med_click.mp3 : f3o_1_f3_med_click.mid
	timidity -Ow -o t.wav f3o_1_f3_med_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f1_slow_click.mp3 : f3o_1_f1_slow_click.mid
	timidity -Ow -o t.wav f3o_1_f1_slow_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f2_slow_click.mp3 : f3o_1_f2_slow_click.mid
	timidity -Ow -o t.wav f3o_1_f2_slow_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f3_slow_click.mp3 : f3o_1_f3_slow_click.mid
	timidity -Ow -o t.wav f3o_1_f3_slow_click.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f1_fast.mp3 : f3o_1_f1_fast.mid
	timidity -Ow -o t.wav f3o_1_f1_fast.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f2_fast.mp3 : f3o_1_f2_fast.mid
	timidity -Ow -o t.wav f3o_1_f2_fast.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f3_fast.mp3 : f3o_1_f3_fast.mid
	timidity -Ow -o t.wav f3o_1_f3_fast.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f1_med.mp3 : f3o_1_f1_med.mid
	timidity -Ow -o t.wav f3o_1_f1_med.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f2_med.mp3 : f3o_1_f2_med.mid
	timidity -Ow -o t.wav f3o_1_f2_med.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f3_med.mp3 : f3o_1_f3_med.mid
	timidity -Ow -o t.wav f3o_1_f3_med.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f1_slow.mp3 : f3o_1_f1_slow.mid
	timidity -Ow -o t.wav f3o_1_f1_slow.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f2_slow.mp3 : f3o_1_f2_slow.mid
	timidity -Ow -o t.wav f3o_1_f2_slow.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav
${MP3D}/f3o_1_f3_slow.mp3 : f3o_1_f3_slow.mid
	timidity -Ow -o t.wav f3o_1_f3_slow.mid
	normalize t.wav
	lame -h t.wav $@
	rm t.wav

f3o_1.wav : f3o_1.mid
	timidity -Ow -o f3o_1.wav f3o_1.mid
	normalize f3o_1.wav
${MP3D}/f3o_1.mp3 : f3o_1.wav
	lame -h f3o_1.wav $@
f3o_1_parts.a4 : f3o_1_parts
	${MUSCRIPT} f3o_1_parts > $@
	pkill -HUP gv

f3o_2.a4 : f3o_2
	${MUSCRIPT} f3o_2 > $@
	pkill -HUP gv
f3o_3.a4 : f3o_3
	${MUSCRIPT} f3o_3 > $@
	pkill -HUP gv
${PIECE}.a4 : ${PIECE}
	${MUSCRIPT} ${PIECE} > $@
	pkill -HUP gv
${PLAY}.mid : ${PLAY}
	${MUSCRIPT} -midi ${PLAY} > $@
	# | midiecho -c 0 -e 1,2 -d 400,400 -s 5,5 - > ${PLAY}.mid
play : ${PLAY}.mid
	midisox_lua ${PLAY}.mid -d stat # trim 199.5
play1 :
	muscript -midi f3o_1 | midisox_lua - -d stat # trim 169 20 # 190 25
play2 :
	muscript -midi f3o_2 | midisox_lua - -d stat # trim 90
play3 :
	muscript -midi f3o_3 | midisox_lua - -d stat
playa :
	muscript -midi a | midisox_lua - -d stat
playb :
	muscript -midi b | midisox_lua - -d stat
playc :
	muscript -midi c | midisox_lua - -d stat

to_be_echoed.a4 : to_be_echoed
	${MUSCRIPT} to_be_echoed > $@
	pkill -HUP gv
play_t :
	muscript -midi to_be_echoed |midiecho -c 0 -e 1,2 -d 400,400 -s 1,1 |aplaymidi - &

title.a4 : title
	groff -ms title | ${BANNERISE} > $@
	pkill -HUP gv

a.a4 : a
	${MUSCRIPT} a > $@
	pkill -HUP gv
c.a4 : c
	${MUSCRIPT} c > $@
	pkill -HUP gv
titles.jpg : titles.eps
	eps2jpg titles.eps > $@
	display $@
video :
	muscript2video -t /home/pjb/mus/f3o/titles.jpg \
	  -c /home/pjb/mus/blurb/credits.jpg f3o_video
