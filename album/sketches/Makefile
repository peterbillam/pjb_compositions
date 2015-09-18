PIECE=konkerado
# sometimes web remember web3 web2 web4
ALL=20150505 20150630

dev : ${PIECE}.a4

edit :
	${EDITOR} ${PIECE}
	muscript ${PIECE} > ${PIECE}.a4
	pkill -HUP gv
	muscript -midi ${PIECE} | midisox_py - -d stat

play :
	muscript -midi ${PIECE} | midisox_py - -d stat

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

