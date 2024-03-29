# DEPO Delivery Service Bindings for Python

Python wrapper for [DEPO](https://depo.sk)'s application interface. At the moment, it provides easy access to contracted places (input / output) and placing and canceling orders.

Detailed information of DEPO's API can be found at [their website](https://admin.depo.sk/apigility/documentation/Api-v2). If you feel like you need covering additional API methods, please open an issue or create a pull request.

## Setup

You can install this package by using `pip`:

	pip install depo

If you fancy `pipenv` use:

	pipenv install depo

To install from source, run:

	python setup.py install

For the API client to work you would need Python 2.7+ or Python 3.4+.

To install via `requirements` file from your project, add the following for the moment before updating dependencies:

	git+git://github.com/palosopko/depo-python.git#egg=depo

## Usage

First off, you need to require the library and provide authentication information by providing your user name and password do [DEPO's admin interface](https://admin.depo.sk`)

	import depo
	dibuk.api_credentials = ('email', 'password')

**Getting contracted places** is accomplished by calling `depo.Place.all()`. The method returns a list with `depo.Place` objects containing all the relevant details. Please note boolean properties `is_input` and `is_output` – if you are just trying to implement DEPO's service for your customers to get their orders, you will only be interested in the latter.

To **place a new order** you need to run `depo.Order.create()` with code of a place (or `Place` object), recipient's name, phone, email and order's amount, product amount and optionally an order reference. Method returns dictionary with delivery details including reference number under the `number` key.

## Contributing

1.  Check for open issues or open a new issue for a feature request or a bug.
2.  Fork the repository and make your changes to the master branch (or branch off of it).
3.  Send a pull request.

## Development

Run all tests on all supported Python versions:

	make test

Run the linter with:

	make lint

The client library uses Black for code formatting. Code must be formatted with Black before PRs are submitted. Run the formatter with:

	make fmt

## Changelog

### v0.2.0: 30/09/2019

Python 3 compatibility for real, code formatting is covered by Black and various small fixes to make everything better and easier including first test.

### v0.1.1: 04/04/2017

Fixes creating order from place's identifiers sent as unicode.

### v0.1.0: 28/03/2017

Initial version with support for getting pickup places.
