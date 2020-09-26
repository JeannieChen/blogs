---
layout: post
title: Programming Languages Influence Network 
subtitle: Force-directed graph using D3.js 
tags: [JavaScript, D3]
css: [/assets/css/2019-09-25-force-directed-graph-layout.css]
js: [/assets/js/2019-09-25-force-directed-graph-layout.js]
ext-js: [//d3js.org/d3.v5.min.js, //d3js.org/d3-dsv.v1.min.js, //d3js.org/d3-fetch.v1.min.js, //d3js.org/d3-color.v1.min.js, //d3js.org/d3-interpolate.v1.min.js, //d3js.org/d3-scale-chromatic.v1.min.js, //unpkg.com/topojson@3, //cdnjs.cloudflare.com/ajax/libs/d3-tip/0.9.1/d3-tip.min.js]
---

This visualization shows the influence relations and the programming paradigams for selected programming languages. Dataset is not complete with an intention to show force-directed graph layout using D3.js. 

Programming languages are displayed as nodes in the form of circles and influence relations are displayed as edges in the form of lines (either solid or dashed). Node sides reflect the number of languages a language has influenced (i.e. outdegree). 

When user double clicks a node, it pins the node's position such that it will not be modified by the grah layout algorithm. Node pinning is an effective interaction technique to help users spatially organize nodes during graph exploration. Pinned nodes will be shown in purple which helps to differentiate from unpinned nodes. Double clicking a pinned node should unfreeze its positon and unmark it. 