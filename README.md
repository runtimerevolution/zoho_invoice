# Zoho Invoice

[![Build Status](https://travis-ci.org/neovintage/zoho_invoice.png?branch=master)](https://travis-ci.org/neovintage/zoho_invoice)
[![Coverage Status](https://coveralls.io/repos/neovintage/zoho_invoice/ibadge.png?branch=master)][coveralls]

Need to interact with the Zoho Invoice API?  The zoho_invoice gem has your back.

Until the gem reaches 1.0, the interface for interacting with the gem could change.  On top of that the gem does not support the entire API just yet.  Just the minimum number of domain objects to actually create customers and invoices.  This will change over time.

## Installation

Add this line to your application's Gemfile:

    gem 'zoho_invoice'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install zoho_invoice

## Configuration

The Zoho Invoice API service requires that you generate an auth token ahead of time using the API, just once.  Fortunately, the gem can handle that in console for you, all you need is your username and password.
Then you can save the authtoken in your project based on however you do your configuration.

```
homebase $ irb
> require 'zoho_invoice'
 => true
> result = ZohoInvoice::AuthToken.generate_authtoken('dude@example.com', 'thisismysweetpassword')
 => #<struct ZohoInvoice::AuthToken::AuthTokenResult authtoken="blahblahblahnumbersnstuff", cause=nil>
> result.success?
 => true
> result.auth_token
 => "blahblahblahnumbersnstuff"
```

## Usage

```ruby
require 'zoho_invoice'

client = ZohoInvoice::Client.new(:authtoken => 'my authtoken', :apikey => 'my apikey')

invoice = ZohoInvoice::Invoice.new(client, :customer_id => 'asdf')
invoice.save
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
