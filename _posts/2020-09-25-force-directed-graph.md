---
layout: post
title: Force-directed graph layout
subtitle: D3 visulization
tags: [JavaScript, D3]
css: [/assets/css/2020-09-25-force-directed-graph-layout.css]
js: [/assets/js/2020-09-25-force-directed-graph-layout.js]
ext-js: [//d3js.org/d3.v5.min.js, //d3js.org/d3-dsv.v1.min.js, //d3js.org/d3-fetch.v1.min.js, //d3js.org/d3-color.v1.min.js, //d3js.org/d3-interpolate.v1.min.js, //d3js.org/d3-scale-chromatic.v1.min.js, //unpkg.com/topojson@3, //cdnjs.cloudflare.com/ajax/libs/d3-tip/0.9.1/d3-tip.min.js]
---

Adding node labels: Show a node label (the node name, i.e., the source) on the top right of each node. If a node is dragged, its label must move with it.

Styling edges: Style the edges based on the “value” field in the links array. Assign the following styles:

If the value of the edge is equal to 0, the edge should be black, thin, and dashed.

If the value of the edge is equal to 1, the edge should be green, thick, and solid.

Scale the radius of each node in the graph based on the degree of the node (you may try linear or squared scale, but you are not limited to these choices).

Note: Regardless of which scale you decide to use, you should avoid extreme node sizes (e.g., nodes that are mere points, barely visible, or of huge sizes. Failure to do so will result in a poor quality visualization.

The degree of each node should be represented by varying colors. Pick a meaningful color scheme (hint: color gradients). The number of color gradations is up to you, but it must be visually evident that the nodes with higher degree are colored a darker/deeper color and the nodes with lesser degree are colored lighter.

When you double click a node, it pins the node’s position such that it will not be modified by the graph layout algorithm (note: pinned nodes can still be dragged around by the user but they will remain at their positions otherwise). Node pinning is an effective interaction technique to help users spatially organize nodes during graph exploration.

Mark pinned nodes to visually distinguish them from unpinned nodes, e.g., pinned nodes are shown in a different color, border thickness or visually annotated with an “asterisk” (\*), etc.

Double clicking a pinned node should unpin (unfreeze) its position and unmark it.