# Screen Wake Lock

Screen Wake Lock is a browser feature that allows websites to prevent a devices screen from turning off.

References:

- [MDN docs on the Screen Wake Lock API](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Wake_Lock_API)
- [Blog post from Chrome dev blog](https://developer.chrome.com/docs/capabilities/web-apis/wake-lock)
- [Tutorial on bookmarklets]([url](https://www.freecodecamp.org/news/what-are-bookmarklets/))


Basic bookmarklet to keep the screen on:

```
javascript: (() => { navigator.wakeLock.request("screen"); })();
```

Bookmarklet to keep screen on with `alert` messages for success and failure states:

```
javascript: (() => { try { navigator.wakeLock.request('screen'); alert('Success! Your screen will stay until you leave this page.'); } catch (err) { alert(`Sorry, there was a problem: ${err.name}, ${err.message}`); }; })();
```
