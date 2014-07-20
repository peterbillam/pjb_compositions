PLAY = 20140616
dev : ${PLAY}.ps
${PLAY}.ps : ${PLAY}
	muscript ${PLAY} > $@
	pkill -HUP gv
play :
	muscript -midi ${PLAY} | midisox_lua - - | aplaymidi -p TiM - &
stat :
	muscript -midi ${PLAY} | midisox_lua - -n stat
