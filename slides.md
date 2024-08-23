---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Advanced browser feature
info: |
 ## advanced browser feature course @Univ Rennes
  Master @istic

  Learn more at [istic](https://istic.univ-rennes.fr/)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# Polyglot programming in the context of advanced web engineering

Or why Web platform browsers are awesome ? 


<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/barais/web.advanced" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>


---

# Why Web platform browsers are awesome ? 


- Web Worker
- Service Worker
- WebAssembly
- OPFS
- ...

---

# Web Worker

<div style="display:inline-block; color:black;border: 3px solid #ffd800; margin-bottom: 25px; border-radius: 10px; background-color: #FFF1AD; box-shadow: 13px 15px 6px #2b2626; border-top: 30px solid #ffd800;">

  <div id="texts">
    <p style="color:black; margin-top: 10px;margin-left: 10px; margin-bottom: 10px;  font-size: 120%;">
 <img src="https://istic.univ-rennes.fr/sites/istic.univ-rennes.fr/files/styles/focal_point_scale_and_crop_200x200/public/interlocutors/Barais_6.jpg" width="25" style="float: left; margin-right: 10px;" />Could you explain me what is a <b>Web worker</b> in the context of web technologies?
   </p>
    <p style="color:black; margin-top: 10px;margin-left: 10px; margin-bottom: 10px;  font-size: 120%;">
<img src="https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_400/https://ainewsbase.com/wp-content/uploads/2023/01/0RCoGXO_400x400.jpg" width="25" style="float: left; margin-right: 10px;" />A <b>web worker</b> is a JavaScript script that runs in the background, independently of other scripts, without affecting the performance of the page. This allows for long-running scripts that do not interfere with the user interface, and also allows for the <b>concurrent execution</b> of multiple scripts, leading to a more responsive and faster web page. Web workers are supported by most modern web browsers, and they can be used for tasks such as processing large amounts of data, running complex calculations, or listening for server-sent events.
   </p>
  </div>
</div>

---
layout: center
---

# Web worker

![](/WebWorker.png)

---

# Web Worker


- from UI thread


```ts
if (typeof Worker !== 'undefined') {
  // Create a new
  const worker = new Worker(new URL('./app.worker', import.meta.url));
  worker.onmessage = ({ data }) => {
    console.log(`page got message: ${data}`);
  };
  worker.postMessage('hello');
} else {
  // Web workers are not supported in this environment.
  // You should add a fallback so that your program still executes correctly.
}
```

- Web worker

```ts
addEventListener('message', ({ data }) => {
  const response = `worker response to ${data}`;
  postMessage(response);
});
```


---

# Service Worker


<div style="display:inline-block; color:black;border: 3px solid #ffd800; margin-bottom: 25px; border-radius: 10px; background-color: #FFF1AD; box-shadow: 13px 15px 6px #2b2626; border-top: 30px solid #ffd800;">

  <div id="texts">
    <p style="color:black; margin-top: 10px;margin-left: 10px; margin-bottom: 10px;  font-size: 120%;">
 <img src="https://istic.univ-rennes.fr/sites/istic.univ-rennes.fr/files/styles/focal_point_scale_and_crop_200x200/public/interlocutors/Barais_6.jpg" width="25" style="float: left; margin-right: 10px;" />Could you explain me what is a <b>service worker</b> in the context of web technologies?
   </p>
    <p style="color:black; margin-top: 10px;margin-left: 10px; margin-bottom: 10px;  font-size: 120%;">
<img src="https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_400/https://ainewsbase.com/wp-content/uploads/2023/01/0RCoGXO_400x400.jpg" width="25" style="float: left; margin-right: 10px;" />A <b>service worker</b> is a script that runs in the background, separate from a web page, and <b>acts as a proxy</b> between a web page and the network. This allows service workers to <b>intercept and handle network requests</b>, including programmatically managing a cache of responses.

Service workers enable features such as offline support, background sync, push notifications and improve the performance of web apps by intercepting network requests and serving responses from a local cache, instead of going to the network. Service workers are supported by most modern web browsers and are a key technology for building <b>Progressive Web Applications</b> (PWAs). PWAs are web apps that can be installed on a user's device and run offline, similar to native mobile apps.

   </p>
  </div>
</div>

---


# WebAssembly

> WebAssembly (abbreviated Wasm) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable compilation target for programming languages, enabling deployment on the web for client and server applications.

- **Efficient and fast** The Wasm <a href="https://webassembly.org/docs/semantics/">stack machine</a> is designed to be encoded in a size- and load-time-efficient <a href="https://webassembly.org/docs/binary-encoding/">binary format</a>. WebAssembly aims to execute at native speed by taking advantage of <a href="https://webassembly.org/docs/portability/#assumptions-for-efficient-execution">common hardware capabilities</a> available on a wide range of platforms.
- **Safe** WebAssembly describes a memory-safe, sandboxed <a href="https://webassembly.org/docs/semantics/#linear-memory">execution environment</a> that may even be implemented inside existing JavaScript virtual machines. When <a href="https://webassembly.org/docs/web/">embedded in the web</a>, WebAssembly will enforce the same-origin and permissions security policies of the browser. 
- **Open and debuggable** WebAssembly is designed to be pretty-printed in a <a href="https://webassembly.org/docs/text-format/">textual format</a> for debugging, testing, experimenting, optimizing, learning, teaching, and writing programs by hand. 
- **Part of the open web platform** WebAssembly is designed to maintain the versionless, feature-tested, and backwards-compatible <a href="https://webassembly.org/docs/web/">nature of the web</a>. WebAssembly modules will be able to call into and out of the JavaScript context and access browser functionality through the same Web APIs accessible from JavaScript.

---

# OPFS

- The Origin Private File System (OPFS, part of the File System Access API) is augmented with a new surface that brings very performant access to data. This new surface differs from existing ones by offering in-place and exclusive write access to a file’s content. This change, along with the ability to consistently read unflushed modifications and the availability of a synchronous variant on dedicated workers, significantly improves performance and unblocks new use cases.

- Release with Chrome 109 one week ago.

---

# Web worker, web assembly, OPFS, WEBGL

- You can do thread,
- You can compile C code to WASM
- You have access to a real efficient FS. 

- Ready to run advanced application within the browser  <uim-rocket /> <uim-rocket class="text-3xl text-red-400 mx-2" /> <uim-rocket class="text-3xl text-orange-400 animate-ping" />



- A short demo with [correctExam](https://correctexam.github.io/corrigeExamFront/)

---
layout: two-cols
---

# Web worker and web assembly

<div style="center">
<img src="/01-01-why-768x313.png" width="900"/><img>
</div>

::right::


<v-click>
<div style="center">
<img src="/01-02-user-and-dev.png" width="450"/><img>
</div>
</v-click>

---
layout: two-cols
---

# Web worker and web assembly


- **Step 1**

<div style="center">
<img src="/02-01-js-interop-01-768x575.png" width="400"/><img>
</div>



::right::

<v-click>

- **Step 2**

<div style="center">
<img src="/02-01-js-interop-02-768x575.png" width="400"/><img>
</div>
</v-click>

---
layout: two-cols
---

# What's happen in the real life

<div style="center">
<img src="/02-03-number-mismatch-768x619.png" width="400"/><img>
</div>


::right::

<v-click>
<div style="center">
<img src="/02-05-number-conversion-768x619.png" width="400"/><img>
</div>
</v-click>


<v-click>
<div style="center">
<img src="/02-04-mapping-book-768x376.png" width="400"/><img>
</div>
</v-click>
---
layout: two-cols
---

<style>
 .center1 {
  align-items: center;
  text-align: center;
   width: 100%;
    display: flex;
    justify-content: center;
  }
</style>

# Classical FFI problems

- need a stub/skeleton

<div>
<img src="/02-07-js-glue-768x735.png" width="300"/><img>
</div>

<v-click>
<div class="center1">
<img src="/04_wasm_bindgen_02-768x453.png" width="200"/><img>
</div>
</v-click>

::right::


<v-click>
<div style="center">
<img src="/01-03-star-diagram-768x606.png" width="400"/><img>
</div>
</v-click>



---


# Rust to the rescue

- https://rustwasm.github.io/book/why-rust-and-webassembly.html

---
layout: cover
---

# Time For Demo


---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
