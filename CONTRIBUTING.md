# Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

If you are interested in creating bindings in a new langauge, and have a chat to one of us on the [pact-dev Google group][pact-dev].

[pact-dev]: https://groups.google.com/forum/#!forum/pact-dev

# Release process

* Bump version and update this changelog
* `bundle exec rake package`
* open `./pkg`
* Draft a new [release](https://github.com/pact-foundation/pact-provider-verifier/releases/new)
  * Set name to `pact-provider-verifier-x.y.z`
  * Upload `.tar.gz` and `.zip` artifacts from `./pkg`
