# 01 - drumkit

## Questions

- How did he know to look for `transitionend`? What do I need to log to see each of those properties
- Holding down a key will get the on-screen key to be stuck in the 'playing' animation state (shrunk and with a yellow border), why is that?
- "We'll then pass it the event, ***e***", is `e` reserved for 'events' or is it simply convention?

## Enhancements

- Added on screen click via
  ```<div onClick="playSoundClick(this)" data-key="76" class="key">``` and

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
  I would prefer to use the same function but unsure of how to merge a click and keyboartd event.
