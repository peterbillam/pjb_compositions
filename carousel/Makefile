FD = /home/pjb/www/softgoods
SD = /home/pjb/www/mus/samples
FD = /home/pjb/www/softgoods
MUSCRIPT = /home/pbin/muscript
BLURB = /home/pjb/mus/blurb/compositions
FREEBACKPAGE = /home/pjb/mus/blurb/freebackpage
FREED = /home/pjb/www/mus/free
BANNERISE = /home/pbin/bannerise
A42US = /home/pbin/a42us
PSCAT = /home/pbin/pscat
ADDMESSAGE = /home/pbin/add_free_message

dev : overture.mid vs1.mid
all : cast.a4 libretto.a4 references.a4 title_libretto.a4 \
 vs1.a4 vs2.a4 vs3.a4 overture.a4 mailout_eu.a4 mailout_non_eu.a4 \
 ${FD}/carousel_libretto.a4 ${FD}/carousel_libretto.us \
 ${FREED}/carousel_samples.pdf ${FREED}/carousel_libretto.pdf

# the words
title_libretto.a4 : title_libretto
	groff -ms title_libretto | ${BANNERISE} > $@
title_libretto_free.a4 : title_libretto_free
	groff -ms title_libretto_free | ${BANNERISE} > $@
cast.a4 : cast
	groff -ms cast > $@
libretto.a4 : cast bp libretto
	groff -ms cast bp libretto > $@
references.a4 : references
	groff -ms references > $@
${FD}/carousel_libretto.a4 : title_libretto.a4 ruby_mugshot.a4 \
 libretto.a4 selfportrait.a4 references.a4
	${PSCAT} title_libretto.a4 ruby_mugshot.a4 libretto.a4 \
	selfportrait.a4 references.a4 > $@
${FD}/carousel_libretto.us : title_libretto.a4 ruby_mugshot.a4 \
 libretto.a4 selfportrait.a4 references.a4
	${A42US} title_libretto.a4 > /tmp/libretto
	${A42US} -e ruby_mugshot.a4 >> /tmp/libretto
	${A42US} libretto.a4 >> /tmp/libretto
	${A42US} -e selfportrait.a4 >> /tmp/libretto
	${A42US} references.a4 >> /tmp/libretto
	${PSCAT} /tmp/libretto > $@
	rm /tmp/libretto
${FREED}/carousel_libretto.pdf : title_libretto_free.a4 ruby_mugshot.a4 \
 libretto.a4 selfportrait.a4 references.a4
	${PSCAT} title_libretto_free.a4 ruby_mugshot.a4 libretto.a4 \
	selfportrait.a4 references.a4 \
	| ${A42US} -c \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -

# vocal score, voice and piano
overture.a4 : overture
	${MUSCRIPT} overture > $@
vs1.a4 : vs1
	${MUSCRIPT} vs1 > $@
vs2.a4 : vs2
	${MUSCRIPT} vs2 > $@
vs3.a4 : vs3
	${MUSCRIPT} vs3 > $@

# midi files
overture.mid : overture
	${MUSCRIPT} -midi overture > $@
vs1.mid : vs1
	${MUSCRIPT} -midi vs1 > $@
vs2.mid : vs2
	${MUSCRIPT} -midi vs2 > $@
vs3.mid : vs3
	${MUSCRIPT} -midi vs3 > $@

# the sample scenes, for the mailout
samples.a4 : samples
	${MUSCRIPT} samples > $@
freebackpage.a4 : freebackpage
	groff -ms freebackpage | ${BANNERISE} > $@
freebackpage : ${FREEBACKPAGE}
	./make_freebackpage ${FREEBACKPAGE} > $@
mailout_eu.a4 : mailout_eu
	groff -ms mailout_eu > $@
mailout_non_eu.a4 : mailout_non_eu
	groff -ms mailout_non_eu > $@
# run ./extract_samples manually after editing vs1 vs2 or vs3 ...
title_samples_free.a4 : title_samples_free
	groff -ms title_samples_free | ${BANNERISE} > $@
${FREED}/carousel_samples.pdf : title_samples_free.a4 samples.a4 \
 freebackpage.a4
	${ADDMESSAGE} samples.a4 \
	| ${PSCAT} title_samples_free.a4 - freebackpage.a4 \
	| ${A42US} -c \
	| /usr/bin/gs -q -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=$@ -
