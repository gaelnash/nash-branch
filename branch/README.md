 process-data/make_vax_map.sh
@@ -51,10 +51,10 @@ npx mapshaper -i ./src/data/us_counties_albers.json ./src/data/us_states_albers_
    -style stroke=#c2c2c2 stroke-width=1 target=innerlines \
    -o public/vaccinations_county_map.svg target=*

# make a state map of just TX & NM (because we don't have county data for them)
# make a state map of just a few states (because we have incomplete county data for them)
npx mapshaper -i ./src/data/us_states_albers.json -filter '"TX,NM,HI,CO,VA,GA,WV".indexOf(STUSPS) > -1' \
    -rename-layers states_subset \
    -join ./src/data/vaccinations.csv keys=STUSPS,Location target=states_subset\
    -join ./src/data/vaccinations.csv keys=STUSPS,Location fields=Series_Complete_Pop_Pct target=states_subset\
    -classify field=Series_Complete_Pop_Pct color-scheme=PuBuGn breaks=10,20,30,40,50,60,70,80,90 target=states_subset \
    -o format=topojson src/data/vaccinations_states_subset.topojson.json target=*

2 public/build/bundle.css

Some generated files are not rendered by default. Learn more.
46,314 public/build/bundle.js

Large diffs are not rendered by default.
2 public/build/bundle.js.map

Large diffs are not rendered by default.
4 public/index.html
@@ -6,9 +6,9 @@

	<link rel="icon" type="image/png" href="favicon.png">
	<link rel="stylesheet" href="global.css">
	<link rel="stylesheet" href="build/bundle.css?version=1617814582404">
	<link rel="stylesheet" href="build/bundle.css?version=1617815884880">

	<script defer src="build/bundle.js?version=1617814582404"></script>
	<script defer src="build/bundle.js?version=1617815884880"></script>
	</head>

<body></body></html>
2 src/components/smarts/Map.albers.svelte
@@ -1,5 +1,5 @@
<script>
	import { getContext, createEventDispatcher, afterUpdate } from 'svelte';
	import { getContext, createEventDispatcher, afterUpdate, onMount } from 'svelte';
	import { geoPath, geoIdentity } from 'd3-geo';
	import { raise } from 'layercake';
    import { feature } from 'topojson-client';
2 src/data/vaccinations_county_map.topojson.json

Large diffs are not rendered by default.
2 src/data/vaccinations_states_subset.topojson.json

Large diffs are not rendered by default.
0 comments on commit 48c9d12
@gaelnash
Attach files by dragging & dropping, selecting or pasting them.

You’re not receiving notifications from this thread.

    © 2021 GitHub, Inc.
    Terms
    Privacy
    Security
    Status
    Docs

    Contact GitHub
    Pricing
    API
    Training
    Blog
    About

# nash-branch has to programme the easiest way of reducing python language to a appropiate way of requiring skill of converting python 2 and adversing to python 3
