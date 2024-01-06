# Screen Wake Lock

Screen Wake Lock is a browser feature that allows websites to prevent a devices screen from turning off.

```
javascript: (() => { alert('hello') })();
```

```
javascript: (() => { navigator.wakeLock.request("screen"); })();
```

```
javascript: (() => { try { navigator.wakeLock.request('screen'); alert('Success! Your screen will stay until you leave this page.'); } catch (err) { alert(`Sorry, there was a problem: ${err.name}, ${err.message}`); }; })();
```
