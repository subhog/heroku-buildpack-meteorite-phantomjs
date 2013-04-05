# Heroku buildpack: Meteorite with Phantomjs

This build pack allows you to easily deploy meteor apps to heroku using [meteorite](http://github.com/oortcloud/meteorite). It's easy to use different branches of meteor and any smart package you can lay your hands on.

This version includes Phantomjs to allow the spiderable package to function correctly.

## Usage

```bash
heroku create --stack cedar --buildpack https://github.com/cwaring/heroku-buildpack-meteorite-phantomjs.git
```

Then `git push` to heroku as usual.

## NOTES

You need to set the `ROOT_URL` environment variable:

```bash
heroku config:add ROOT_URL=your.domain.com
```

If you are not running this as a fresh buildpack you will need to setup the environment paths correctly:

```bash
heroku config:add LD_LIBRARY_PATH=/usr/local/lib:/usr/lib:/lib:/app/vendor/phantomjs/lib
heroku config:add PATH=bin:.meteor/heroku_build/bin:node_modules/.bin:/usr/local/bin:/usr/bin:/bin:/app/vendor/phantomjs/bin
```

You can specify meteor settings by setting the `METEOR_SETTINGS` environment variable:

```bash
heroku config:add METEOR_SETTINGS='{"key":"value"}'
```


You need to have a verified account so the buildpack can add a `mongohq:sandbox` addon.
