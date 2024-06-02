---
aliases:
  - obsidian-3d-graph
tags:
  - obsidian-plugin
  - obsidian
  - obsidian-md
  - "#open-source"
  - "#data-visualization"
  - "#developer-tools"

  - "#obsidian"
  - "#3d-graph"
  - "#plugin-development"
---
## Obsidian 3D Graph (Yomaru)

![Obsidian 3D graph](https://github.com/HananoshikaYomaru/obsidian-3d-graph/assets/43137033/c8a501e8-c5b6-4622-b5df-2a2335609cae)

A 3D Graph for Obsidian with dozen of features!

see the demo: <https://www.youtube.com/watch?v=w1H-pcM8nOU>

<a href="https://www.buymeacoffee.com/yomaru" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 30px !important;width: 105px !important;" ></a> [![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/hananoshikayomaru)

## Installation

### Through community plugin store

You can install this on community plugin store 😎

### Through BRAT

1. install the BRAT plugin
2. go to the plugin option, add beta plugin, copy and paste the link of this repo.
3. the plugin will automatically appear in the list of installed community plugins, enabled this plugin

### Manual installation

1. cd to `.obsidian/plugins`
2. git clone this repo
3. `cd obsidian-3d-graph && bun install && bun run build`
4. there you go 🎉

## Features

### Global Graph

Use ribbon button or command to open the global graph.

You can do zooming (scroll you wheel), rotating (drag the scene) and panning (`ctrl`/`cmd` and drag the scene) in the graph.

> ⚠️ The underly [3D graph](https://github.com/vasturiano/3d-force-graph) has Performance issue that I don't know how to fix. You can set the max node number limit on the plugin setting. If the total node number on the graph beyond the limit, the graph will not be rendered to protect your computer from hanging.

### Local Graph

In a note, you can run command `Open local 3D graph` to open a local graph. A local graph will only show nodes that connect to this nodes.

In local graph you will have all the features of global graph, plus:

1. depth: you can control the depth of maximum distance of the nodes away from the center node
2. link type: show only inlinks, outlinks or both.

> ✨ Tips: I set the `cmd + L` to open local 3D graph.

### Filter Node on global graph

1. filter by query
2. filter attachment
   1. definition of attachment: any files which are not markdown files
3. filter orphans
   1. definition of orphans: any node that has no links IN THE CURRENT GRAPH

### Group and color nodes on global graph

you can use query to create groups and color nodes on a global graph.

### Label fade

When you are closer to the node, the label will appear. When you move away from the node, the node will fade away.

### Changing display setting

You can change the following:

1. Node size
   1. Node size also scale with degree of connection. The more links a node has, the bigger it is.
2. Link thickness
3. Link distance
4. Node repulsion
5. Distance from Focal. This will affect the label fade. When distance from focal is smaller, node further away from what you are look at will have label with lower opacity.
6. node hover color, node hover neighbour color, link hover color
7. show file extension, show full path on label
8. show center coordination
9. show link arrow
10. don't node move on drag
11. [dag](https://en.wikipedia.org/wiki/Directed_acyclic_graph) mode. See more on [DAG Mode](https://github.com/HananoshikaYomaru/obsidian-3d-graph#dag-mode).
12. embedding graph into note through `3d-graph` code block post processor (working in progress)

> [!CAUTION] The `3d-graph` code block post processor is still in working progress.
> It is definitely not stable yet, use it in your own risk.

### Focus on node

hold `Ctrl`/`cmd` and click on a node will fly and focus on a node. It is the perfect way to navigate on large graph.

### Search and focus

You can search and focus on a node in the graph

### Multiple selection and batch commands

hold `shift` and click on nodes to select multiple nodes. Then right click on one of the selected nodes to open commands. You can run batched commands on the selected nodes.

### DAG mode

You can see DAG(Directed acyclic graph) orientation on a graph. This only has effect when the graph is acyclic.

### Save Setting

You can save, update and restore previous settings.

### Other customization

You can change the style of the graphview by css snippet.

1. open your setting > appearance
2. create a css snippet
3. add the following

```css
body {
  /* change the default node color */
  --graph-node: #00ff00;
  /* change the default link color */
  --graph-line: #ff0000;
}

.graph-3d-view canvas {
  /* change the background color */
  background: white;
}

.graph-3d-view .node-label {
  /* change the default node label color */
  color: #00ff00;
}
```

![](https://share.cleanshot.com/Ld9xzBJ4+)

### Feature roadmap

1. Use dataview as search engine.
2. expose API to make it even more easier for other plugin to integrate.

some other uncertain features are will sit in the github issues but I work on them base on ICE (Impact, confidence, effort)

## Development

1. cd to `.obsidian/plugins`
2. git clone this repo
3. `cd obsidian-3d-graph && bun install && bun run dev`
4. there you go 🎉

for release, just run `bun release` to release patch. You can also add `--minor` or `--major` to change update version.

## Note

1. I have been developing this for free. I try to prioritize the functions before fanciness. I also prioritize my tasks base on ICE (Impact, Confidence, Effort).
2. I have other on-going projects. I need open source helpers. Sponsorship will give me motivation and code contributors are very appreciate. I am open for discussion through <https://cal.com/manlung>.
3. If you have an question or feature request, please open Github issues.

## Say thank you

If you are enjoying this plugin then please support my work and enthusiasm by sponsoring me on Github or buying me a coffee on <https://www.buymeacoffee.com/yomaru>.

<a href="https://www.buymeacoffee.com/yomaru" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 30px !important;width: 105px !important;" ></a> [![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/hananoshikayomaru)

## Acknowledgement

Just want to say thanks to those people. Without them, this repo will not be here.

1. The original repo: <https://github.com/AlexW00/obsidian-3d-graph>
2. The 3d force graph by @vasturiano: <https://github.com/vasturiano/3d-force-graph>
