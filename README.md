# Note

This is a pure fork of the original passport-instagram module, it just changes the oAuth endpoints to use the newer graph API, since the older one is deprecated.

## Install

```shell
$ npm install passport-instagram-graph-api
```

## Usage

#### Configure Strategy

The Instagram authentication strategy authenticates users using a Instagram
account and OAuth 2.0 tokens.  The strategy requires a `verify` callback, which
accepts these credentials and calls `done` providing a user, as well as
`options` specifying a client ID, client secret, and callback URL.

```js
passport.use(new InstagramStrategy({
    clientID: INSTAGRAM_CLIENT_ID,
    clientSecret: INSTAGRAM_CLIENT_SECRET,
    callbackURL: "http://127.0.0.1:3000/auth/instagram/callback"
  },
  function(accessToken, refreshToken, profile, done) {
    User.findOrCreate({ instagramId: profile.id }, function (err, user) {
      return done(err, user);
    });
  }
));
```

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'instagram'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

```js
app.get('/auth/instagram',
  passport.authenticate('instagram'));

app.get('/auth/instagram/callback', 
  passport.authenticate('instagram', { failureRedirect: '/login' }),
  function(req, res) {
    // Successful authentication, redirect home.
    res.redirect('/');
  });
```

## Examples

For a complete, working example, refer to the [login example](https://github.com/jaredhanson/passport-instagram/tree/master/examples/login).

## Tests

```shell
$ npm install --dev
$ make test
```

[![Build Status](https://secure.travis-ci.org/jaredhanson/passport-instagram.png)](http://travis-ci.org/jaredhanson/passport-instagram)

## Credits

  - [Jared Hanson](http://github.com/jaredhanson)

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2011-2013 Jared Hanson <[http://jaredhanson.net/](http://jaredhanson.net/)>


