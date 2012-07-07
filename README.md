Heroku Buildpack Octopress
==============================

A fork of the [official Ruby Buildpack][1] with support for generating an [Middleman][2] static site during the build/deploy stage.

Inspired by the [heroku-buildpack-middleman][3] from Andre Arko but updated to work with the new Heroku Bundler method of [specifying a Ruby version][4].

Usage
-----
When creating the Heroku application substitute this buildpack.

```
heroku create --buildpack https://github.com/instinctive3/heroku-buildpack-middleman.git
```
or add this buildpack to your current app
```
heroku config:add BUILDPACK_URL=https://github.com/instinctive3/heroku-buildpack-middleman.git
```

To serve your static site you will need TryStatic from [rack-contrib][5] with the root set to "build".

Flow
----
The buildpack adds the Middleman `build` task after `rake assets:precompile` task in the Ruby language pack.

The Rack language pack is then invoked by the `config.ru` file which runs the Sinatra Static Server to serve the generated files.

Rails 2/3 language packs remain in place but will be ignored.

[1]: https://github.com/heroku/heroku-buildpack-ruby
[2]: http://middlemanapp.com/
[3]: https://github.com/indirect/heroku-buildpack-middleman
[4]: https://devcenter.heroku.com/articles/ruby-versions
[5]: https://github.com/rack/rack-contrib
