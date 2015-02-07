PIECE=20150203
ALL=20141020 20140912 20141001 20141002 \
 20140914 20140920 \
 20140909 20140910 20141009 \
 20141020 20141001 20141004 20140918

dev : ${PIECE}.a4

edit :
	vi ${PIECE}
	muscript ${PIECE} > ${PIECE}.a4
	pkill -HUP gv
	muscript -midi ${PIECE} | midisox_lua - -d stat

play :
	muscript -midi ${PIECE} | midisox_lua - -d stat

${PIECE}.a4 : ${PIECE}
	muscript ${PIECE} > $@
	pkill -HUP gv

all :  ${ALL}
	cat ${ALL} > $@

all.a4 : all
	muscript all > $@
	pkill -HUP gv

playall : all all.a4
	muscript -midi all | midisox_lua - -d stat

