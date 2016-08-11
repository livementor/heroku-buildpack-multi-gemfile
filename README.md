This buildback is always enabled, i.e. when it's added to an app, the app will
always be detected by Heroku as a "multi Gemfile" app, even if it's not.

It will however have no effect if the `BUNDLE_GEMFILE` environment variable is
not defined.

Ideally, we would only enable it when `BUNDLE_GEMFILE` is defined, but
environment variables are not available in `bin/detect` (see [this issue][1]).

If `BUNDLE_GEMFILE` is present, it makes creates the following symlinks :  
`Gemfile` → `$BUNDLE_GEMFILE`  
`Gemfile.lock` → `$BUNDLE_GEMILE.lock`

Note: the symlinks are only created if the source and the target are not already
linked together (in any direction).

[1]: https://github.com/heroku/heroku-buildpack-ruby/pull/351
