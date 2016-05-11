# Pact Provider Verification

This setup simplifies Pact Provider [verification](https://github.com/realestate-com-au/pact#2-tell-your-provider-that-it-needs-to-honour-the-pact-file-you-made-earlier)
process in any language, wrapping the Ruby implementation into a cross-platform,
binary-like CLI tool.

**Features**:

* Verify Pacts against Pacts published to an http endpoint, such as a [Pact Broker](https://github.com/bethesque/pact_broker)
* Verify local `*.json` Pacts on the file system
* Works with Pact [provider states](https://github.com/realestate-com-au/pact/wiki/Provider-states) should you need them

## Installation

### Native Installation

Download the appropriate [release](https://github.com/pact-foundation/pact-provider-verifier/releases)
for your OS and put somewhere on your `PATH`.

### With Ruby on Mac OSX and Linux

```
gem install pact-provider-verifier
pact-provider-verifier <args>
```

Run `pact-mock-service help` for command line options.

## Examples

See the [examples](examples) directory for a real working API example:

```
cd examples
./test.sh
```

### Simple API

*Steps*:

1. Create an API and a corresponding Docker image for it
1. Publish Pacts to the Pact broker (or create local ones)
1. Run the CLI tool for your OS, passing the appropriate flags:
   * `--pact_urls` - a comma delimited list of pact file urls
   * `--provider_base_url` - the base url of the pact provider (i.e. your API)
1.

### API with Provider States

Execute pact provider verification against a provider which implements the following:

* an http get endpoint which returns pact provider_states by consumer

		{
			"myConsumer": [
				"customer is logged in",
				"customer has a million dollars"
			]
		}

* an http post endpoint which sets the active pact consumer and provider state

		consumer=web&state=customer%20is%20logged%20in

The following environment variables required:

* `pact_urls` - a comma delimited list of pact file urls
* `provider_base_url` - the base url of the pact provider
* `provider_states_url` - the full url of the endpoint which returns provider states by consumer
* `provider_states_setup_url` - the full url of the endpoint which sets the active pact consumer and provider state


## Contributing

See [CONTRIBUTING.md](/CONTRIBUTING.md)

[pact]: https://github.com/realestate-com-au/pact
[releases]: https://github.com/bethesque/pact-mock_service/releases
[javascript]: https://github.com/DiUS/pact-consumer-js-dsl
[pact-dev]: https://groups.google.com/forum/#!forum/pact-dev
[windows]: https://github.com/bethesque/pact-mock_service/wiki/Building-a-Windows-standalone-executable
[install-windows]: https://github.com/bethesque/pact-mock_service/wiki/Installing-the-pact-mock_service-gem-on-Windows
[why-generated]: https://github.com/realestate-com-au/pact/wiki/FAQ#why-are-the-pacts-generated-and-not-static