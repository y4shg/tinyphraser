# tinyphraser

paste an email. rephrase it. nothing leaves your device :)

no api calls, no logs, no cookies, no backend. the model runs entirely in your browser using your own gpu. you could disconnect from the internet after the first load and it would still work fine.

---

# what is tinyphraser?

tinyphraser is a lightweight browser app that lets you paste any email or message and have it rephrased or rewritten in a different tone   professional, casual, concise, friendly, assertive, whatever you need.

the difference from every other "ai writing tool" is that there is no server involved at any point. not for the model, not for your text, not for anything. your email never leaves the tab.

---

# why does this exist?

most ai writing tools send your text to an external api. that means your emails, your words, your context  all of it hits a server somewhere. for most people thats fine. for some its not.

tinyphraser is for the second group. you know people who work with sensitive content, people who just dont want their drafts logged somewhere, or people who want something that works offline.

---

# how does it work?

its just html and javascript. the heavy lifting is a library called [webllm](https://webllm.mlc.ai/) which lets you run a small language model directly in the browser using webgpu   a modern browser api that gives javascript access to your gpu.

first time you open the app it downloads the model and caches it locally. after that it loads instantly and works with no connection.

if you want to see what webllm is capable of theres a live demo at the link above, but you dont need to understand any of that to use this. its basically just a way to run a model in the browser.

---

# usage

**requirements:**
- [node.js](https://nodejs.org) (LTS version is fine)
- chrome 113+ or edge 113+   firefox does not support webgpu yet
- a gpu that supports webgpu (most machines from the last 5 years are fine)

**setup:**

1. open a terminal in the project folder

2. scaffold vite   this just sets up the dev server, it wont overwrite your files
```bash
npm create vite@latest . -- --template vanilla
```
say yes if it asks about anything

3. install webllm
```bash
npm install @mlc-ai/web-llm
```

4. start the dev server
```bash
npm run dev
```

5. open `http://localhost:5173`

thats it. first load will take a few minutes depending on your connection since the model is a few gb. after its cached it opens in seconds.

---

# file structure

```
├── index.html
├── style.css
├── src/
│   ├── main.js           # boots the app, wires everything together
│   ├── engine.js         # loads the webllm model, handles download progress
│   ├── chat.js           # multi-turn chat history and message state
│   ├── rephraser.js      # rephrase logic and tone modes
│   └── ui.js             # all dom manipulation lives here
├── components/
│   ├── emailInput.js     # the paste zone textarea
│   ├── chatWindow.js     # renders the chat thread
│   ├── controls.js       # tone selector pills and buttons
│   └── loadingBar.js     # model download progress indicator
├── prompts/
│   └── templates.js      # system prompt templates for each tone
├── assets/
│   └── favicon.ico
└── package.json
```

---

# features


**chat**

after rephrasing you can keep chatting about the email. ask it to shorten a specific part, change the subject line, make it less blunt, whatever. it keeps the context of the whole rephrased output.

**fully offline after first load**

the model downloads once and gets cached by the browser. clearing site data will re-trigger the download, everything else is local.

---

# notes

- tested on chrome 124+ and edge 124+
- first inference after loading can feel slow   the model warms up after the first message and gets faster
- works best with shorter emails, very long walls of text may produce slower output
- clearing browser cache will force a fresh model download
- if the page crashes on load, your browser or gpu may not support webgpu  try chrome if you arent already

---

# tech used

| thing | what its doing |
|---|---|
| [webllm](https://github.com/mlc-ai/web-llm) | running the model in browser via webgpu |
| [vite](https://vitejs.dev/) | dev server and module bundling |
| vanilla js | everything else |
| webgpu | gpu access from the browser |

no frameworks, no component libraries, no build pipeline beyond vite. kept intentionally small.

---

> this project was built because i wanted something like this to exist and it didnt. if you find it useful, thats great. if something is broken open an issue.