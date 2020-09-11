## Safe Navigation Operator

Introduced in Ruby 2.3.0. Allows you navigate a call chain without having to check if the attribute is present on each object.

```ruby
account&.owner&.address
```

h/t https://mitrev.net/ruby/2015/11/13/the-operator-in-ruby/

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
