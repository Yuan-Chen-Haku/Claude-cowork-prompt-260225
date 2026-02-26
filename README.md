# Interactive Knowledge Work Graph Explorer

[English](README.md) | [中文](README_zh.md)

An interactive, browser-based concentric radial graph visualization tool designed for exploring the Claude Knowledge Work Plugins architecture and the associated Markdown documentation files.

## Overview

This project provides a visually engaging and functional way to browse complex nested directory structures and their embedded Markdown content. Built with HTML, Vanilla CSS, Vanilla JavaScript, and the `force-graph` library, it renders a dynamic graph where:
- The root workspace is fixed firmly at the center.
- Directories flow outwards as distinct concentric rings based on their depth.
- Individual Markdown files appear as leaf nodes branching off from their parent directories.

## Features

### 1. Dynamic Concentric Radial Layout
- **Ring Structure**: Nodes are strictly organized into concentric circles based on their depth in the file system (Depth 0 for root, Depth 1 for top-level folders, etc.).
- **Center Node Focus**: The root node is uniquely styled (black color), fixed precisely in the center of the canvas (`x: 0, y: 0`), and is unclickable to anchor the entire graph visually.
- **Node Coloring**:
  - Root Node (Depth 0): Black (`#000000`)
  - Sub-directories (Depth 1): Red (`#ff0000`)
  - Deeper Directories: Turquoise/Teal
  - Files: Blue
- **Customizable Physics Controls**: A floating control panel allows real-time adjustment of:
  - **Ring Spacing (Radius)**: Controls the distance between concentric circles (50 to 500).
  - **Node Repulsion (Centrality)**: Controls the force separating the nodes from each other (-300 to 0).

### 2. Interactive Exploration & Focus Mode
- **Hover Effects**: Hovering over a node displays its name as a tooltip standard behavior.
- **Click-to-Focus**:
  - Clicking on a file or directory node (except the root) enters a "Focus Mode".
  - The clicked node, its direct parent, and its direct children are brightly highlighted.
  - All other unconnected nodes and links fade out gracefully (opacity drops to `0.45` for nodes and `0.2` for links) to reduce visual clutter.
- **Auto-Framing**: When a node is clicked, the graph automatically calculates the bounding box of the highlighted components and smoothly transitions (pans and zooms) to center them within the left 50% of the screen, ensuring they are not obscured by the content panel.
- **Background Click**: Clicking anywhere on the empty canvas clears the focus mode and returns the graph to its default state.

### 3. Integrated Markdown Content Viewer
- **Slide-out Panel**: When a node is clicked, a frosted glass (backdrop-filter) information panel slides out elegantly from the right side of the screen.
- **Content Rendering**:
  - **Files**: The panel dynamically renders the Markdown content (`node.content`) into formatted HTML using the `marked.js` library.
  - **Directories**: Displays a helpful prompt to click child nodes to view file contents.
- **One-Click Copy**: A built-in "Copy" button (📋) in the panel header allows users to instantly copy the raw Markdown text of the currently viewed file to their system clipboard. Provides a visual green checkmark (✅) confirmation upon success.
- **Dynamic Header**: The panel header updates in real-time to display the file's name (`#doc-title`) and absolute path (`#doc-path`).

### 4. Robust Fallback Mechanisms
- **Script Loading**: Ensures high availability by falling back to alternative CDNs (unpkg -> jsdelivr -> cdnjs) if the primary source fails to load for `force-graph` or `marked`.

## Technologies Used

- **HTML5 & Vanilla CSS**: For structure, styling, and animations (frosted glass panel, control sliders).
- **Vanilla JavaScript**: For logic, state management, and interaction handling.
- **[Force-Graph](https://github.com/vasturiano/force-graph)**: For rendering the webgl-based force-directed graph.
- **[Marked.js](https://marked.js.org/)**: For parsing and rendering Markdown content securely and quickly within the browser.
- **Clipboard API**: Native browser API for the copy-to-clipboard functionality.

## Usage

1. Clone or download the repository.
2. Ensure you have the correctly structured JSON data embedded or loaded into the script. The default implementation expects a `graph-data-json` script tag containing an array of `nodes` and `links`.
3. Open `index.html` in any modern web browser.
4. Interact using your mouse/trackpad!

---
*Created as part of the Claude Knowledge Work Plugins exploration.*
