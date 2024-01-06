# Screen Wake Lock

Screen Wake Lock is a browser feature that allows websites to prevent a device's screen from turning off. This can be useful for cases like when you have a cooking recipe open on your phone and don't want the screen to dim or turn off.

References:

- [MDN docs on the Screen Wake Lock API](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Wake_Lock_API)
- [Blog post from Chrome dev blog](https://developer.chrome.com/docs/capabilities/web-apis/wake-lock)

## Bookmarklet

- [Tutorial on bookmarklets](https://www.freecodecamp.org/news/what-are-bookmarklets/))

### How to add the bookmarklet on iOS

1. In Safari, press and hold the book icon.
2. Tap **Add Bookmark**.
3. For the name, enter `Keep Screen On`.
4. Tap **Save**. (note: you can't edit the URL yet)
5. Copy a bookmarklet snippet from below.
6. Tap the book icon.
7. Find the bookmark you just created. Press and hold it.
8. Tap **Edit**.
9. Paste the snippet into the URL field.
10. Tap **Save**.

Now your bookmarklet is ready to use! Next time you're on a webpage and you want to keep the screen on, tap the book icon to open your bookmarks and tap the **Keep Screen On** bookmark.

### Bookmarklet Snippets

Basic bookmarklet to keep the screen on:

```
javascript: (() => { navigator.wakeLock.request("screen"); })();
```

Bookmarklet to keep screen on with `alert` messages for success and failure states:

```
javascript: (() => { try { navigator.wakeLock.request('screen'); alert('Success! Your screen will stay until you leave this page.'); } catch (err) { alert(`Sorry, there was a problem: ${err.name}, ${err.message}`); }; })();
```
