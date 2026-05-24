# tinyphraser


This is tinyphraser:
Tinyphraser is a simple website where you can upload your email or any message, then ask it to be rephrased or modified. 

The best part is that nothing leaves your device, absolutely nothing, not a cookie, log, or request for ANY ai api.

# how it works
its just html and javascript. the heavy lifting is done by a library called webllm which lets you run a small language model directly in the browser using webgpu. first time you open it, it downloads and caches the model. after that its instant.
if you want to see what webllm is capable of theres a live demo at the link above, but honestly you dont need to know any of that to use this.

Ok enough of the general stuff

# usage
 
**before you start:** you need [node.js](https://nodejs.org) installed. grab the LTS version if you dont have it.
 
1. open a terminal in the project folder
2. scaffold vite (this is just the dev server, it wont touch your files)
```bash
npm create vite@latest . -- --template vanilla
```
 
3. install webllm
```bash
npm install @mlc-ai/web-llm
```
 
4. start it
```bash
npm run dev
```
 
5. open `http://localhost:5173` in **chrome or edge**  firefox doesnt support webgpu yet so it wont work there
first load will take a while depending on your connection, the model is a few gb. after its cached it opens instantly.
 
# file structure
here is a beginner file strucutre (just for now)
├── index.html
├── style.css
├── src/
│   ├── main.js           
│   ├── engine.js        
│   ├── chat.js          
│   ├── rephraser.js   
│   └── ui.js             
├── components/
│   ├── emailInput.js     
│   ├── chatWindow.js     
│   ├── controls.js      
│   └── loadingBar.js   
├── prompts/
│   └── templates.js      
├── assets/
│   └── favicon.ico
└── package.json   

# notes
 
- tested on chrome 124+, edge 124+
- needs a gpu that supports webgpu (most modern laptops and desktops are fine)
- model downloads once and caches in the browser, clearing site data will re-trigger the download
- if it feels slow on first inference thats normal, it warms up after the first message