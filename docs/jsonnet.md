## jsonnet-bundler

### Load a library from a local directory

This can be useful for local development and testing of libraries, for example:

```diff
 {
   "version": 1,
   "dependencies": [
     {
       "source": {
-        "git": {
-          "remote": "https://github.com/example/jsonnet-libs.git",
-          "subdir": ""
+        "local": {
+          "directory": "../../jsonnet-libs"
         }
-      },
-      "version": "main"
+      }
     }
   ]
 }
```
