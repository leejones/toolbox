## jsonnet-bundler

### Load a library from a local directory

This can be useful for local development and testing of libraries, for example

```diff
 {
   "version": 1,
   "dependencies": [
     {
-      "git": {
-        "remote": "https://github.com/example/jsonnet-repo.git",
-         "subdir": ""
+      "source": {
+        "local": {
+          "directory": "../../jsonnet-repo"
         }
       },
       "version": "main"
     }
   ]
 }
```
