## Replace the current process with a shell command

Replace the current process with an irb session:

```ruby
Kernel.exec("irb")
```

If the file is a script, you can replace the current process with the same script running in a Docker container:

```ruby
Kernel.exec("docker run [IMAGE] #{0}")
```

h/t to https://github.com/jbranchaud/til/blob/master/ruby/replace-the-current-process-with-an-external-command.md
