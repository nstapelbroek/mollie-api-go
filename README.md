# Mollie API Golang client

## Actions

[![Testing](https://github.com/VictorAvelar/mollie-api-go/actions/workflows/main.yml/badge.svg)](https://github.com/VictorAvelar/mollie-api-go/actions/workflows/main.yml)
[![Linter](https://github.com/VictorAvelar/mollie-api-go/actions/workflows/golangci-lint.yml/badge.svg)](https://github.com/VictorAvelar/mollie-api-go/actions/workflows/golangci-lint.yml)
[![CodeQL](https://github.com/VictorAvelar/mollie-api-go/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/VictorAvelar/mollie-api-go/actions/workflows/codeql-analysis.yml)

## Scrutinizer CI

[![Build Status](https://scrutinizer-ci.com/g/VictorAvelar/mollie-api-go/badges/build.png?b=master)](https://scrutinizer-ci.com/g/VictorAvelar/mollie-api-go/build-status/master)
[![Code Coverage](https://scrutinizer-ci.com/g/VictorAvelar/mollie-api-go/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/VictorAvelar/mollie-api-go/?branch=master)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/VictorAvelar/mollie-api-go/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/VictorAvelar/mollie-api-go/?branch=master)

## Go ecosystem

[![Go Reference](https://pkg.go.dev/badge/github.com/VictorAvelar/mollie-api-go/v4/mollie.svg)](https://pkg.go.dev/github.com/VictorAvelar/mollie-api-go/v4/mollie)
[![Go Report Card](https://goreportcard.com/badge/github.com/VictorAvelar/mollie-api-go/v3)](https://goreportcard.com/report/github.com/VictorAvelar/mollie-api-go/v3)
[![OpenSSF Best Practices](https://bestpractices.coreinfrastructure.org/projects/3522/badge)](https://bestpractices.coreinfrastructure.org/projects/3522)

Accepting [iDEAL](https://www.mollie.com/payments/ideal/), [Apple Pay](https://www.mollie.com/payments/apple-pay), [Bancontact](https://www.mollie.com/payments/bancontact/), [SOFORT Banking](https://www.mollie.com/payments/sofort/), [Creditcard](https://www.mollie.com/payments/credit-card/), [SEPA Bank transfer](https://www.mollie.com/payments/bank-transfer/), [SEPA Direct debit](https://www.mollie.com/payments/direct-debit/), [PayPal](https://www.mollie.com/payments/paypal/), [Belfius Direct Net](https://www.mollie.com/payments/belfius/), [KBC/CBC](https://www.mollie.com/payments/kbc-cbc/), [paysafecard](https://www.mollie.com/payments/paysafecard/), [Giftcards](https://www.mollie.com/payments/gift-cards/), [Giropay](https://www.mollie.com/payments/giropay/), [EPS](https://www.mollie.com/payments/eps/) and [Przelewy24](https://www.mollie.com/payments/przelewy24/) online payments without fixed monthly costs or any punishing registration procedures. Just use the Mollie API to receive payments directly on your website or easily refund transactions to your customers.

## Requirements

To use the Mollie API client, the following things are required:

- Get yourself a free [Mollie account](https://www.mollie.com/signup). No sign up costs.
- Now you're ready to use the Mollie API client in test mode.
- Follow [a few steps](https://www.mollie.com/dashboard/?modal=onboarding) to enable payment methods in live mode, and let us handle the rest.
- Up-to-date OpenSSL (or other SSL/TLS toolkit)

For leveraging [Mollie Connect](https://docs.mollie.com/oauth/overview) (advanced use cases only), it is recommended to be familiar with the OAuth2 protocol.

## Install

```sh
go get -u github.com/VictorAvelar/mollie-api-go/v4/mollie
```

## Usage

### Testing using API tokens

#### Using the config helper

```go
// Create a configuration object with idempotency enabled.
config := mollie.NewAPITestingConfig(true)
```

#### Using the NewConfig method

```go
// Create a configuration object with idempotency enabled.
config := mollie.NewConfig(true, mollie.ApiTokenEnv)

_ := config.ToggleIdempotency()
```

### Testing using Organization access tokens

#### Using the config helper for org tokens

```go
// Create a configuration object with idempotency enabled.
config := mollie.NewOrgTestingConfig(true)
```

#### Using the NewConfig method for org tokens

```go
// Create a configuration object with idempotency enabled.
config := mollie.NewConfig(true, mollie.OrgTokenEnv)

_ := config.ToggleIdempotency()
```

### Create an API client

```go
// build your desired config
client, err := mollie.NewClient(config)
if err != nil {
    log.Fatal(err)
}
// perform operations with the API.
```

## Upgrade guide

If you want to upgrade from v2 -> v3, the list of breaking and notable changes can be found in the [docs](docs/v3-upgrade.md).

## :warning: Notice for v3.4 & v3.5

These versions contain breaking changes in the `mollie.NewConfig` method, the  number of parameters
increased thus breaking any previous implementation and requiring manual changes when updating.

The issue is patched for v3.6 which also includes a bunch of helper methods in the `mollie.Config` struct
to make the usage and changes in the values more manageable.

## API parity

Checks to the API changelog are performed constantly to ensure API parity and compatibility, however it might happen that not all the changes are implemented right away.

For checking all the related tasks you can check the issues labeled with the [API parity](https://github.com/VictorAvelar/mollie-api-go/labels/API%20parity) label.
