# tinyphraser


This is tinyphraser:
Tinyphraser is a simple website where you can upload your email or any message, then ask it to be rephrased or modified. 

The best part is that nothing leaves your device, absolutely nothing, not a cookie, log, or request for ANY ai api.

How it works: 
This project runs on html and javascript. 
The library webllm is what helps the most, its a simple web api to hook up the webgpu and run a lightweight model. If you want, you can see a crude example of what is possible -->
https://webllm.mlc.ai/

But i'd rather not delve into the specifics of that. TLDR: its basically just a way to run a model in the web.

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