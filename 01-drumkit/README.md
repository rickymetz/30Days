# 01 - drumkit

[Demo Link](https://rickymetz.github.io/30Days/01-drumkit/index.html)

## Questions

- How did he know to look for `transitionend`? What do I need to log to see each of those properties
  - >https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers
- Holding down a key will get the on-screen key to be stuck in the 'playing' animation state (shrunk and with a yellow border), why is that?
  - >@ricky - the transform/transition happens on `:active`, but the class is added on `click`.  so if you hold your mouse down for longer than the transition time, the `:active` transition ends before your click handler gets called, so it tries to remove the class before adding.
The issue is that the `click` handler doesn't get called until you release the mouse if you change `onClick` to `onMouseDown`, i think you'll have better luck
- "We'll then pass it the event, ***e***", is `e` reserved for 'events' or is it simply convention?
  -  `e` is a convention. Short hand for `event` which isn't a reserved word but browsers do use it as a global variable. https://stackoverflow.com/questions/10323392/in-javascript-jquery-what-does-e-mean

## Enhancements

- Added on screen click via
  ```<div onmousedown="playSoundClick(this)" data-key="76" class="key">``` and

  ```
  function playSoundClick(d) {
      console.log(d);
      const audio = document.querySelector(`audio[data-key="${d.getAttribute("data-key")}"]`);
      const key = document.querySelector(`div[data-key="${d.getAttribute("data-key")}"]`);
      if (!audio) return;
      audio.currentTime = 0;
      audio.play();
      key.classList.add('playing');
    }
  ```
  I would prefer to use the same function but unsure of how to merge a click and keyboard event.
