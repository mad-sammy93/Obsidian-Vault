conky.text = [[
${offset 0}${voffset 10}${font Metropolis Black:size=12}${time %A. %d %B %Y}${font Cantarell:size=1}
${offset 0}${voffset 15}${color}${font League Spartan:bold:size=35}${execi 100 cat ~/.cache/weather.json | jq '.main.temp' | awk '{print int($1+0.5)}'}° ${execi 100 cat ~/.cache/weather.json | jq -r '.weather[0].description' | sed -e 's/\(.*\)/\U\1/'}${font Cantarell:size=1}
${execi 300 ~/.config/conky/Graffias/scripts/weather.sh}\
${offset 0}${voffset 25}${color1}${font Carlito:size=11}Local time in ${execi 100 cat ~/.cache/weather.json | jq -r '.name'}  is ${time %H.%M}. Today Max temperature is
${offset 0}${voffset 4}${color1}${font Carlito:size=11}${execi 100 cat ~/.cache/weather.json | jq '.main.temp_max' | awk '{print int($1+0.5)}'}°C with wind speed ${execi 100 (cat ~/.cache/weather.json | jq '.wind.speed')}km/h and ${execi 100 (cat ~/.cache/weather.json | jq '.main.humidity')}% humidity
${offset 41}${voffset 70}${font Metropolis Black:size=9}CPU   ${cpu cpu0}%${goto 196}RAM    ${memperc}%
${offset 0}${voffset 40}${font Material:size=9}${if_running mocp} ${font Carlito:size=11}${moc_state} :${else}${font Material:size=9} ${font Carlito:size=11}No music played${endif}
${offset 0}${voffset 5}${font Metropolis black:size=15}${if_running mocp}${moc_artist}${else}${font}
${offset 0}${voffset 2}${font Carlito:size=11}${if_running mocp}${moc_song}${else}
${image  ~/.config/conky/Graffias/res/oval.png -s 132x40 -p 0,200}
${image ~/.config/conky/Graffias/res/ring.png -s 132x40 -p 150,200}
]]