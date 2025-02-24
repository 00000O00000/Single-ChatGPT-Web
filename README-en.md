# Single-ChatGPT-Web

[[License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[中文|[English](README-en.md)]

A lightweight, single-file HTML web client for ChatGPT that implements intelligent conversation features using the OpenAI API.

## Features

- Simple chat interface design with support for continuous conversation context.
- Ultra-small single file of only 88KB with zero dependencies (depends on ByteDance CDN's online files for rendering md and tex).
- Markdown format rendering based on `marked.js` and `github-markdown.css` (ByteDance CDN).
- LaTeX formula rendering based on MathJax (ByteDance CDN).
- Embeds images encoded in base64 directly into the HTML file.
- Display adaptation for Deepseek's deep thinking content.
- Responsive layout (supports access from PCs and mobile devices).

## Changelog

This repository was published on Github platform on 2025-02-17.

**1.0**

> 2024-08-13
>
> Webpage released.
>
> The webpage supports rendering Markdown using markdown-it library.

**2.0**

> 2024-09-20
>
> Added support for multiple prompt words and fixed some bugs.
>
> Optimized overall webpage layout.

**3.0**

> 2025-02-17
>
> Added support for temperature settings.
>
> Added display support for Deepseek-R1 deep thinking content (please use an interface supporting reasoning_content for Q&A).
>
> Added LaTeX formula rendering support.
>
> Switched Markdown library to marked.js.
>
> Changed CDN source to ByteDance CDN due to jsDelivery being inaccessible within China.

**4.0**

> 2025-02-24
>
> Added support for streaming responses.
>
> Added streaming display support for Deepseek-R1 deep thinking content.
>
> Optimized webpage display.

## Quick Start

### Prerequisites
#### Obtain BASE_URL and API_KEY for interfaces supporting the official OpenAI protocol.

> This project does not provide an interface proxy service. If you need to use the official OpenAI interface, please set up your own proxy.

You need to acquire a BASE_URL like `https://api.openai.com/v1/chat/completions` and an API_KEY like `sk-xxxxxx`.

Then modify the webpage source code according to the configuration instructions below.

If you do not have an existing third-party interface service provider, you can check out recommended providers by the author [here](Recommend_API_Server.md).

### Usage Steps
1. Clone this repository or download the `index.html` file;

2. Open the `index.html` file in a text editor;

3. Modify the configuration of the file as per the "Configuration Options" section below;

4. Save the file and run it in one of the following ways:
- (Recommended) Simply double-click to open (Note: If the API endpoint is local, you'll need to disable browser CORS cross-origin restrictions)

- Use Python's local server for LAN access (Note: Allow Python through the firewall):
 ```bash
 python3 -m http.server 8000
 ```
 Then visit `http://localhost:8000`

- Provide public network access using a remote virtual host:

  - Upload the configured file to a remote virtual host;
  - Configure domain resolution and directory;
  - Access the configured domain to use.

## Configuration Options

On line 9 of the file, modifiable configuration parameters include:

```javascript
// API Configuration
var api = "https://api.openai.com/v1/chat/completions"; // Your API endpoint
var apikey = "sk-xxxxxxxxxxxxxxxxxxxxxxxxxxx"; // Your API key

var system_prompt = null; // System prompt, can be left empty
var temperature = 0.9 // Model temperature, higher values increase creativity and randomness of output. This setting has no effect on Deepseek-R1.
var stream = false // Whether to use streaming output.
var llm_selection = [
    ["gpt-4o", "OpenAI GPT 4o"],
    ["first-prompt", "Test Prompt"],
]; // Available models configuration for API, first item in each row is the model code, second is what will show in the dropdown menu. Note trailing commas in arrays.

// Webpage Configuration
var isinfo = 1;// Whether to show initial informational message
var webFontFamily = "STZhongSong, Microsoft YaHei, KaiTi";// Global font family for the webpage, separated by English commas, with priority given to earlier fonts.

// Prompt Configuration
var test_prompt = "You are a helpful assistant.";
// Configure prompts, the first column is the name you give the model (the first column content in llm_selection), the second column is the actual model used, the third column is the prompt variable name. Prompts configured here will override system_prompt.
var prompt_model_list = [
    ["first-prompt", "gpt-4o", test_prompt],
]
```

## FAQ

❓ **How to save chat history?**  
The current version does not store any records locally, so closing the browser or refreshing the page will lose history. 
If you need to export chat history, press F12 to open the browser's developer tools, go to the "Console" tab, type "historys", press enter, and copy the returned content. 

## Screenshots

[Project Screenshot](doc/img/screenshot1.png)