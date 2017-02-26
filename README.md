# Spree Drop Ship

[![Build Status](https://travis-ci.org/spree-contrib/spree_drop_ship.png)](https://travis-ci.org/spree-contrib/spree_drop_ship)
[![Code Climate](https://codeclimate.com/github/spree-contrib/spree_drop_ship.png)](https://codeclimate.com/github/spree-contrib/spree_drop_ship)
[![Coverage Status](https://coveralls.io/repos/spree-contrib/spree_drop_ship/badge.png?branch=master)](https://coveralls.io/r/spree-contrib/spree_drop_ship)
[![Dependency Status](https://gemnasium.com/spree-contrib/spree_drop_ship.png?travis)](https://gemnasium.com/spree-contrib/spree_drop_ship)

What is drop shipping?

"Drop shipping is a supply chain management technique in which the retailer does not keep goods in stock, but instead transfers customer orders
and shipment details to either the manufacturer or a wholesaler, who then ships the goods directly to the customer." - [wikipedia](http://en.wikipedia.org/wiki/Drop_shipping)

So the main goal with spree_drop_ship is to link products to suppliers and forward orders to the appropriate suppliers.

Once an order is placed for a product that belongs to a supplier a shipment is created for the product's supplier.
This shipment is then sent to the supplier (via Email by default). The supplier then follows a link to the shipment
within the email where they are prompted to confirm the shipment.

Spree Drop Ship used with [Spree Marketplace](https://github.com/jdutil/spree_marketplace) allows handling payments to your suppliers via ACH direct deposits.  
This is still currently a work in progress, and any input is welcome.
.

Upgrading
---------

It's been update to run on latest version of **Ruby on Rails 5.0.1** and **Spree 3.2.0** and I'll keep updating it for future versions.  

Installation
------------

Here's how to install spree_drop_ship into your existing spree site AFTER you've installed Spree:

Add the following to your Gemfile:

    gem 'spree_drop_ship', github: 'priom/spree_drop_ship'

Make your bundle happy:

    bundle install

Now run the generator:

    rails g spree_drop_ship:install

Then migrate your database if you did not run during installation generator:

    bundle exec rake db:migrate

And reboot your server:

    rails s

You should be up and running now!

Sample Data
-----------

If you'd like to generate sample data, use the included rake tasks:

```shell
rake spree_sample:load               # Loads sample data into the store
rake spree_sample:suppliers          # Create sample suppliers and randomly link to products
rake spree_sample:drop_ship_orders   # Create sample drop ship orders
```

Demo
----

You can easily use the spec/dummy app as a demo of spree_drop_ship. Just `cd` to where you develop and run:

```shell
git clone git://github.com/priom/spree_drop_ship.git
cd spree_drop_ship
bundle install
bundle exec rake test_app
cd spec/dummy
rake db:migrate db:seed spree_sample:load spree_sample:suppliers spree_sample:drop_ship_orders
rails s
```

Testing
-------

Be sure to bundle your dependencies and then create a dummy test app for the specs to run against.

```shell
bundle
bundle exec rake test_app
bundle exec rspec spec
```

Todo
----

- Stock Items should automatically be set to backorderable false if the variant doesnt belong to the stock locations supplier.
- Must allow suppliers to edit their stock location addresses & require it.
- Return Authorization UI
- Better documentation
- related products should only allow suppliers own products to be related

Contributing
------------

In the spirit of [free software](http://www.fsf.org/licensing/essays/free-sw.html), **everyone** is encouraged to help improve this project.

Here are some ways *you* can contribute:

* by using prerelease versions
* by reporting [bugs](https://github.com/spree-contrib/spree_drop_ship/issues)
* by suggesting new features
* by [translating to a new language](https://github.com/spree-contrib/spree_drop_ship/tree/master/config/locales)
* by writing or editing documentation
* by writing specifications
* by writing code (*no patch is too small*: fix typos, add comments, clean up inconsistent whitespace)
* by refactoring code
* by resolving [issues](https://github.com/spree-contrib/spree_drop_ship/issues)
* by reviewing patches

Donating
--------

Bitcoin donations may be sent to: 1L6akT6Aus9r6Ashw1wDtLg7D8zJCVVZac

Copyright (c) 2012-2014 Jeff Dutil, released under the [New BSD License](https://github.com/spree-contrib/spree_drop_ship/tree/master/LICENSE).
