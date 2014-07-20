MUSCRIPT = /home/pbin/muscript
COMPD = /home/pjb/www/mus/comp
A4D = ${COMPD}/a4
USD = ${COMPD}/us
XMLD = ${COMPD}/xml
SRCD = ${COMPD}/src
MP3D = ${COMPD}/mp3
WAVD = /home/pjb/wav/studies
BACKPAGE = /home/pjb/mus/blurb/cc_backpage
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message
PIECE = studies
STUDIES = 01_finger_exercise 02_scales_323 03_scales_424 04_scales_233 \
  05_scales_2n2 06_contrary_motion 07_three_against_one 08_shimmer \
  09_chords_including_pedal 10_passing_notes 11_crossrhythms \
  12_2x6_3x4_4x3_6x2 13_1n1_line 14_rabbit 15_three_hands \
  16_voice_leading 17_toccata 18_line 19_variations 20_two_pianos
PLAY = 10_passing_notes

# see also ~/mus/arr/piano/exercises.a4 for the basic exercises
# mt_piece needs concluding; good and vigorous
# klavieruebungen:
#   p18 One 

dev : ${PLAY}.a4 ${PIECE}.a4 title.a4

all : ${A4D}/${PIECE}.pdf  ${USD}/${PIECE}.pdf \
  ${A4D}/${PIECE}_01.pdf ${USD}/${PIECE}_01.pdf \
  ${A4D}/${PIECE}_02.pdf ${USD}/${PIECE}_02.pdf \
  ${A4D}/${PIECE}_03.pdf ${USD}/${PIECE}_03.pdf \
  ${A4D}/${PIECE}_04.pdf ${USD}/${PIECE}_04.pdf \
  ${A4D}/${PIECE}_05.pdf ${USD}/${PIECE}_05.pdf \
  ${A4D}/${PIECE}_06.pdf ${USD}/${PIECE}_06.pdf \
  ${A4D}/${PIECE}_07.pdf ${USD}/${PIECE}_07.pdf \
  ${A4D}/${PIECE}_08.pdf ${USD}/${PIECE}_08.pdf \
  ${A4D}/${PIECE}_09.pdf ${USD}/${PIECE}_09.pdf \
  ${A4D}/${PIECE}_10.pdf ${USD}/${PIECE}_10.pdf \
  ${A4D}/${PIECE}_11.pdf ${USD}/${PIECE}_11.pdf \
  ${A4D}/${PIECE}_12.pdf ${USD}/${PIECE}_12.pdf \
  ${A4D}/${PIECE}_13.pdf ${USD}/${PIECE}_13.pdf \
  ${A4D}/${PIECE}_14.pdf ${USD}/${PIECE}_14.pdf \
  ${A4D}/${PIECE}_15.pdf ${USD}/${PIECE}_15.pdf \
  ${A4D}/${PIECE}_16.pdf ${USD}/${PIECE}_16.pdf \
  ${A4D}/${PIECE}_17.pdf ${USD}/${PIECE}_17.pdf \
  ${A4D}/${PIECE}_18.pdf ${USD}/${PIECE}_18.pdf \
  ${A4D}/${PIECE}_19.pdf ${USD}/${PIECE}_19.pdf \
  ${A4D}/${PIECE}_20.pdf ${USD}/${PIECE}_20.pdf

dist :
	upload ${A4D}/${PIECE}.pdf
	upload ${USD}/${PIECE}.pdf
dist01 :
	upload ${A4D}/${PIECE}_01.pdf
	upload ${USD}/${PIECE}_01.pdf
dist02 :
	upload ${A4D}/${PIECE}_02.pdf
	upload ${USD}/${PIECE}_02.pdf
dist03 :
	upload ${A4D}/${PIECE}_03.pdf
	upload ${USD}/${PIECE}_03.pdf
dist04 :
	upload ${A4D}/${PIECE}_04.pdf
	upload ${USD}/${PIECE}_04.pdf
dist05 :
	upload ${A4D}/${PIECE}_05.pdf
	upload ${USD}/${PIECE}_05.pdf
dist06 :
	upload ${A4D}/${PIECE}_06.pdf
	upload ${USD}/${PIECE}_06.pdf
dist07 :
	upload ${A4D}/${PIECE}_07.pdf
	upload ${USD}/${PIECE}_07.pdf
dist08 :
	upload ${A4D}/${PIECE}_08.pdf
	upload ${USD}/${PIECE}_08.pdf
dist09 :
	upload ${A4D}/${PIECE}_09.pdf
	upload ${USD}/${PIECE}_09.pdf
dist10 :
	upload ${A4D}/${PIECE}_10.pdf
	upload ${USD}/${PIECE}_10.pdf
dist11 :
	upload ${A4D}/${PIECE}_11.pdf
	upload ${USD}/${PIECE}_11.pdf
dist12 :
	upload ${A4D}/${PIECE}_12.pdf
	upload ${USD}/${PIECE}_12.pdf
dist13 :
	upload ${A4D}/${PIECE}_13.pdf
	upload ${USD}/${PIECE}_13.pdf
dist14 :
	upload ${A4D}/${PIECE}_14.pdf
	upload ${USD}/${PIECE}_14.pdf
dist15 :
	upload ${A4D}/${PIECE}_15.pdf
	upload ${USD}/${PIECE}_15.pdf
dist16 :
	upload ${A4D}/${PIECE}_16.pdf
	upload ${USD}/${PIECE}_16.pdf
dist17 :
	upload ${A4D}/${PIECE}_17.pdf
	upload ${USD}/${PIECE}_17.pdf
dist18 :
	upload ${A4D}/${PIECE}_18.pdf
	upload ${USD}/${PIECE}_18.pdf
dist19 :
	upload ${A4D}/${PIECE}_19.pdf
	upload ${USD}/${PIECE}_19.pdf
dist20 :
	upload ${A4D}/${PIECE}_20.pdf
	upload ${USD}/${PIECE}_20.pdf

wav : ${WAVD}/01_finger_exercise.wav ${WAVD}/02_scales_323.wav \
  ${WAVD}/03_scales_424.wav ${WAVD}/04_scales_233.wav \
  ${WAVD}/05_scales_2n2.wav ${WAVD}/06_contrary_motion.wav \
  ${WAVD}/07_three_against_one.wav ${WAVD}/08_shimmer.wav \
  ${WAVD}/09_chords_including_pedal.wav ${WAVD}/10_passing_notes.wav \
  ${WAVD}/11_crossrhythms.wav ${WAVD}/12_2x6_3x4_4x3_6x2.wav \
  ${WAVD}/13_1n1_line.wav ${WAVD}/14_rabbit.wav \
  ${WAVD}/15_three_hands.wav ${WAVD}/16_voice_leading.wav \
  ${WAVD}/17_toccata.wav ${WAVD}/18_line.wav \
  ${WAVD}/19_variations.wav ${WAVD}/20_two_pianos.wav
	normalize-audio --batch ${WAVD}/*.wav

clean :
	rm title_*.a4 studies_*.a4

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

klavieruebungen.a4 : klavieruebungen
	${MUSCRIPT} klavieruebungen > $@
	pkill -HUP gv
title.a4 : title
	groff -ms title | ${BANNERISE} > $@
p2.a4 : p2
	groff -ms p2 | ${BANNERISE} > $@
t : ${PIECE}
	/home/pbin/start_stop ${PIECE} > $@
t.a4 : t
	${MUSCRIPT} t > $@
play :
	${MUSCRIPT} -midi ${PLAY} | midisox_lua - -d stat # trim 50 fade 0 20 0
play7 :
	${MUSCRIPT} -midi 07_three_against_one | midisox_lua - -d stat
play8 :
	${MUSCRIPT} -midi 08_shimmer | midisox_lua - -d stat
play9 :
	${MUSCRIPT} -midi 09_chords_including_pedal | midisox_lua - -d stat
play10 :
	${MUSCRIPT} -midi 10_passing_notes | midisox_lua - -d stat
play11 :
	${MUSCRIPT} -midi 11_crossrhythms | midisox_lua - -d stat
play12 :
	${MUSCRIPT} -midi 12_morse_thue | midisox_lua - -d stat

mt_piece.a4 : mt_piece
	${MUSCRIPT} mt_piece > $@
	pkill -HUP gv
two_two.a4 : two_two
	${MUSCRIPT} two_two > $@
	pkill -HUP gv
contrary_motion.a4 : contrary_motion
	${MUSCRIPT} contrary_motion > $@
	pkill -HUP gv
crossrhythms.a4 : crossrhythms
	${MUSCRIPT} crossrhythms > $@
	pkill -HUP gv
voice_leading.a4 : voice_leading
	${MUSCRIPT} voice_leading > $@
	pkill -HUP gv
duet.a4 : duet
	${MUSCRIPT} duet > $@
	pkill -HUP gv
20120703.a4 : 20120703
	${MUSCRIPT} 20120703 > $@
	pkill -HUP gv
20120722.a4 : 20120722
	${MUSCRIPT} 20120722 > $@
	pkill -HUP gv
20120803.a4 : 20120803
	${MUSCRIPT} 20120803 > $@
	pkill -HUP gv
20120805.a4 : 20120805
	${MUSCRIPT} 20120805 > $@
	pkill -HUP gv
20120910.a4 : 20120910
	${MUSCRIPT} 20120910 > $@
	pkill -HUP gv
20120928.a4 : 20120928
	${MUSCRIPT} 20120928 > $@
	pkill -HUP gv
20121001.a4 : 20121001
	${MUSCRIPT} 20121001 > $@
	pkill -HUP gv
${PLAY}.a4 : ${PLAY}
	${MUSCRIPT} ${PLAY} > $@
	pkill -HUP gv
studies : ${STUDIES}
	cat ${STUDIES} > $@
studies.a4 : studies
	${MUSCRIPT} studies > $@
	pkill -HUP gv

titles.jpg : titles.eps
	eps2jpg titles.eps > $@
	display $@
video : titles.jpg
	muscript2video -t /home/pjb/mus/studies/titles.jpg \
	  -c /home/pjb/mus/blurb/credits.jpg 19_variations_video

${WAVD}/01_finger_exercise.wav : 01_finger_exercise
	muscript -midi 01_finger_exercise | timidity -Ow -o $@ -
${WAVD}/02_scales_323.wav : 02_scales_323
	muscript -midi 02_scales_323 | timidity -Ow -o $@ -
${WAVD}/03_scales_424.wav : 03_scales_424
	muscript -midi 03_scales_424 | timidity -Ow -o $@ -
${WAVD}/04_scales_233.wav : 04_scales_233
	muscript -midi 04_scales_233 | timidity -Ow -o $@ -
${WAVD}/05_scales_2n2.wav : 05_scales_2n2
	muscript -midi 05_scales_2n2 | timidity -Ow -o $@ -
${WAVD}/06_contrary_motion.wav : 06_contrary_motion
	muscript -midi 06_contrary_motion | timidity -Ow -o $@ -
${WAVD}/07_three_against_one.wav : 07_three_against_one
	muscript -midi 07_three_against_one | timidity -Ow -o $@ -
${WAVD}/08_shimmer.wav : 08_shimmer
	muscript -midi 08_shimmer | timidity -Ow -o $@ -
${WAVD}/09_chords_including_pedal.wav : 09_chords_including_pedal
	muscript -midi 09_chords_including_pedal | timidity -Ow -o $@ -
${WAVD}/10_passing_notes.wav : 10_passing_notes
	muscript -midi 10_passing_notes | timidity -Ow -o $@ -
${WAVD}/11_crossrhythms.wav : 11_crossrhythms
	muscript -midi 11_crossrhythms | timidity -Ow -o $@ -
${WAVD}/12_2x6_3x4_4x3_6x2.wav : 12_2x6_3x4_4x3_6x2
	muscript -midi 12_2x6_3x4_4x3_6x2 | timidity -Ow -o $@ -
${WAVD}/13_1n1_line.wav : 13_1n1_line
	muscript -midi 13_1n1_line | timidity -Ow -o $@ -
${WAVD}/14_rabbit.wav : 14_rabbit
	muscript -midi 14_rabbit | timidity -Ow -o $@ -
${WAVD}/15_three_hands.wav : 15_three_hands
	muscript -midi 15_three_hands | timidity -Ow -o $@ -
${WAVD}/16_voice_leading.wav : 16_voice_leading
	muscript -midi 16_voice_leading | timidity -Ow -o $@ -
${WAVD}/17_toccata.wav : 17_toccata
	muscript -midi 17_toccata | timidity -Ow -o $@ -
${WAVD}/18_line.wav : 18_line
	muscript -midi 18_line | timidity -Ow -o $@ -
${WAVD}/19_variations.wav : 19_variations
	muscript -midi 19_variations | timidity -Ow -o $@ -
${WAVD}/20_two_pianos.wav : 20_two_pianos
	muscript -midi 20_two_pianos | timidity -Ow -o $@ -

${PIECE}_01.a4 : 01_finger_exercise
	muscript 01_finger_exercise > $@
${A4D}/${PIECE}_01.pdf : ${PIECE}_01.a4 ${BACKPAGE}.a4
	sed 's/XXX/One/' title_XXX | groff -ms - | ${BANNERISE} > title_01.a4
	${ADDMESSAGE} ${PIECE}_01.a4 \
	| ${PSCAT} title_01.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_01.pdf : ${PIECE}_01.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_01.a4 \
	| ${PSCAT} title_01.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_02.a4 : 02_scales_323
	muscript 02_scales_323 > $@
${A4D}/${PIECE}_02.pdf : ${PIECE}_02.a4 ${BACKPAGE}.a4
	sed 's/XXX/Two/' title_XXX | groff -ms - | ${BANNERISE} > title_02.a4
	${ADDMESSAGE} ${PIECE}_02.a4 \
	| ${PSCAT} title_02.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_02.pdf : ${PIECE}_02.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_02.a4 \
	| ${PSCAT} title_02.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_03.a4 : 03_scales_424
	muscript 03_scales_424 > $@
${A4D}/${PIECE}_03.pdf : ${PIECE}_03.a4 ${BACKPAGE}.a4
	sed 's/XXX/Three/' title_XXX | groff -ms - | ${BANNERISE} > title_03.a4
	${ADDMESSAGE} ${PIECE}_03.a4 \
	| ${PSCAT} title_03.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_03.pdf : ${PIECE}_03.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_03.a4 \
	| ${PSCAT} title_03.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_04.a4 : 04_scales_233
	muscript 04_scales_233 > $@
${A4D}/${PIECE}_04.pdf : ${PIECE}_04.a4 ${BACKPAGE}.a4
	sed 's/XXX/Four/' title_XXX | groff -ms - | ${BANNERISE} > title_04.a4
	${ADDMESSAGE} ${PIECE}_04.a4 \
	| ${PSCAT} title_04.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_04.pdf : ${PIECE}_04.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_04.a4 \
	| ${PSCAT} title_04.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_05.a4 : 05_scales_2n2
	muscript 05_scales_2n2 > $@
${A4D}/${PIECE}_05.pdf : ${PIECE}_05.a4 ${BACKPAGE}.a4
	sed 's/XXX/Five/' title_XXX | groff -ms - | ${BANNERISE} > title_05.a4
	${ADDMESSAGE} ${PIECE}_05.a4 \
	| ${PSCAT} title_05.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_05.pdf : ${PIECE}_05.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_05.a4 \
	| ${PSCAT} title_05.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_06.a4 : 06_contrary_motion
	muscript 06_contrary_motion > $@
${A4D}/${PIECE}_06.pdf : ${PIECE}_06.a4 ${BACKPAGE}.a4
	sed 's/XXX/Six/' title_XXX | groff -ms - | ${BANNERISE} > title_06.a4
	${ADDMESSAGE} ${PIECE}_06.a4 \
	| ${PSCAT} title_06.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_06.pdf : ${PIECE}_06.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_06.a4 \
	| ${PSCAT} title_06.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_07.a4 : 07_three_against_one
	muscript 07_three_against_one > $@
${A4D}/${PIECE}_07.pdf : ${PIECE}_07.a4 ${BACKPAGE}.a4
	sed 's/XXX/Seven/' title_XXX | groff -ms - | ${BANNERISE} > title_07.a4
	${ADDMESSAGE} ${PIECE}_07.a4 \
	| ${PSCAT} title_07.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_07.pdf : ${PIECE}_07.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_07.a4 \
	| ${PSCAT} title_07.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_08.a4 : 08_shimmer
	muscript 08_shimmer > $@
${A4D}/${PIECE}_08.pdf : ${PIECE}_08.a4 ${BACKPAGE}.a4
	sed 's/XXX/Eight/' title_XXX | groff -ms - | ${BANNERISE} > title_08.a4
	${ADDMESSAGE} ${PIECE}_08.a4 \
	| ${PSCAT} title_08.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_08.pdf : ${PIECE}_08.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_08.a4 \
	| ${PSCAT} title_08.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_09.a4 : 09_chords_including_pedal
	muscript 09_chords_including_pedal > $@
${A4D}/${PIECE}_09.pdf : ${PIECE}_09.a4 ${BACKPAGE}.a4
	sed 's/XXX/Nine/' title_XXX | groff -ms - | ${BANNERISE} > title_09.a4
	${ADDMESSAGE} ${PIECE}_09.a4 \
	| ${PSCAT} title_09.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_09.pdf : ${PIECE}_09.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_09.a4 \
	| ${PSCAT} title_09.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_10.a4 : 10_passing_notes
	muscript 10_passing_notes > $@
${A4D}/${PIECE}_10.pdf : ${PIECE}_10.a4 ${BACKPAGE}.a4
	sed 's/XXX/Ten/' title_XXX | groff -ms - | ${BANNERISE} > title_10.a4
	${ADDMESSAGE} ${PIECE}_10.a4 \
	| ${PSCAT} title_10.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_10.pdf : ${PIECE}_10.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_10.a4 \
	| ${PSCAT} title_10.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_11.a4 : 11_crossrhythms
	muscript 11_crossrhythms > $@
${A4D}/${PIECE}_11.pdf : ${PIECE}_11.a4 ${BACKPAGE}.a4
	sed 's/XXX/Eleven/' title_XXX | groff -ms - | ${BANNERISE} > title_11.a4
	${ADDMESSAGE} ${PIECE}_11.a4 \
	| ${PSCAT} title_11.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_11.pdf : ${PIECE}_11.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_11.a4 \
	| ${PSCAT} title_11.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_12.a4 : 12_2x6_3x4_4x3_6x2
	muscript 12_2x6_3x4_4x3_6x2 > $@
${A4D}/${PIECE}_12.pdf : ${PIECE}_12.a4 ${BACKPAGE}.a4
	sed 's/XXX/Twelve/' title_XXX | groff -ms - | ${BANNERISE} > title_12.a4
	${ADDMESSAGE} ${PIECE}_12.a4 \
	| ${PSCAT} title_12.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_12.pdf : ${PIECE}_12.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_12.a4 \
	| ${PSCAT} title_12.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_13.a4 : 13_1n1_line
	muscript 13_1n1_line > $@
${A4D}/${PIECE}_13.pdf : ${PIECE}_13.a4 ${BACKPAGE}.a4
	sed 's/XXX/Thirteen/' title_XXX | groff -ms - | ${BANNERISE} > title_13.a4
	${ADDMESSAGE} ${PIECE}_13.a4 \
	| ${PSCAT} title_13.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_13.pdf : ${PIECE}_13.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_13.a4 \
	| ${PSCAT} title_13.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_14.a4 : 14_rabbit
	muscript 14_rabbit > $@
${A4D}/${PIECE}_14.pdf : ${PIECE}_14.a4 ${BACKPAGE}.a4
	sed 's/XXX/Fourteen/' title_XXX | groff -ms - | ${BANNERISE} > title_14.a4
	${ADDMESSAGE} ${PIECE}_14.a4 \
	| ${PSCAT} title_14.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_14.pdf : ${PIECE}_14.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_14.a4 \
	| ${PSCAT} title_14.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_15.a4 : 15_three_hands
	muscript 15_three_hands > $@
${A4D}/${PIECE}_15.pdf : ${PIECE}_15.a4 ${BACKPAGE}.a4
	sed 's/XXX/Fifteen/' title_XXX | groff -ms - | ${BANNERISE} > title_15.a4
	${ADDMESSAGE} ${PIECE}_15.a4 \
	| ${PSCAT} title_15.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_15.pdf : ${PIECE}_15.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_15.a4 \
	| ${PSCAT} title_15.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_16.a4 : 16_voice_leading
	muscript 16_voice_leading > $@
${A4D}/${PIECE}_16.pdf : ${PIECE}_16.a4 ${BACKPAGE}.a4
	sed 's/XXX/Sixteen/' title_XXX | groff -ms - | ${BANNERISE} > title_16.a4
	${ADDMESSAGE} ${PIECE}_16.a4 \
	| ${PSCAT} title_16.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_16.pdf : ${PIECE}_16.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_16.a4 \
	| ${PSCAT} title_16.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_17.a4 : 17_toccata
	muscript 17_toccata > $@
${A4D}/${PIECE}_17.pdf : ${PIECE}_17.a4 ${BACKPAGE}.a4
	sed 's/XXX/Seventeen/' title_XXX | groff -ms - | ${BANNERISE} > title_17.a4
	${ADDMESSAGE} ${PIECE}_17.a4 \
	| ${PSCAT} title_17.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_17.pdf : ${PIECE}_17.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_17.a4 \
	| ${PSCAT} title_17.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_18.a4 : 18_line
	muscript 18_line > $@
${A4D}/${PIECE}_18.pdf : ${PIECE}_18.a4 ${BACKPAGE}.a4
	sed 's/XXX/Eighteen/' title_XXX | groff -ms - | ${BANNERISE} > title_18.a4
	${ADDMESSAGE} ${PIECE}_18.a4 \
	| ${PSCAT} title_18.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_18.pdf : ${PIECE}_18.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_18.a4 \
	| ${PSCAT} title_18.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_19.a4 : 19_variations
	muscript 19_variations > $@
${A4D}/${PIECE}_19.pdf : ${PIECE}_19.a4 ${BACKPAGE}.a4
	sed 's/XXX/Nineteen/' title_XXX | groff -ms - | ${BANNERISE} > title_19.a4
	${ADDMESSAGE} ${PIECE}_19.a4 \
	| ${PSCAT} title_19.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_19.pdf : ${PIECE}_19.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_19.a4 \
	| ${PSCAT} title_19.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

${PIECE}_20.a4 : 20_two_pianos
	muscript 20_two_pianos > $@
${A4D}/${PIECE}_20.pdf : ${PIECE}_20.a4 ${BACKPAGE}.a4
	sed 's/XXX/Twenty/' title_XXX | groff -ms - | ${BANNERISE} > title_20.a4
	${ADDMESSAGE} ${PIECE}_20.a4 \
	| ${PSCAT} title_20.a4 - ${BACKPAGE}.a4 \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
${USD}/${PIECE}_20.pdf : ${PIECE}_20.a4 ${BACKPAGE}.a4
	${ADDMESSAGE} ${PIECE}_20.a4 \
	| ${PSCAT} title_20.a4 - ${BACKPAGE}.a4 \
	| ${A42US} \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

