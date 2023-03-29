https://github.com/rbenv/rbenv

https://github.com/rbenv/ruby-build

The list of ruby versions available in your machine to install.

```
$ rbenv install -l
```

If the version is not in the list, update the `ruby-build` plugin using `git pull`

```
$ git pull ~/.rbenv/plugins/ruby-build 
```

Install the new version of ruby 

```
$ rbenv install 3.2.1
```

And then set it as local in the project folder

```
$ rbenv local 3.2.1
```

`.ruby-version` will be update.

Finally, reinstall the project gems 

```
$ bundle i
```
