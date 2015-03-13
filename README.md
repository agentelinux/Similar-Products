Similar Products for Magento
=============

Magento Upsell Product Enhancement with PredictionIO

### Requirements

Must have an instance of PredictionIO server setup and ready to accept data. Please see the docs for information.

## Installation ##

Similar Products for Magento uses [Composer](http://getcomposer.org) and [Magento Composer Installer](https://github.com/magento-hackathon/magento-composer-installer) to handle installation of the module and its dependencies. To install Similar Products for Magento you will need a copy of _composer.phar_ in your path. If you do not have it availble, run the following commands from your terminal.

    $ curl -sS https://getcomposer.org/installer | php
    $ chmod a+x composer.phar

If you are already using Magento Composer Installer and have an existing _composer.json_, add _https://github.com/deved-it/Similar-Products_ to the repositories list and _deved-it/similar-products_ as a required dependency for your project. That's it!

If you do not have an existing Magento Composer Installer _composer.json_ file defined, you can use the following template.

    {
      "repositories": [
          {
            "type":"composer",
            "url":"http://packages.firegento.com"
          },
          {
            "type": "vcs",
            "url": "https://github.com/deved-it/Similar-Products"
          }
      ],
      "require": {
          "magento-hackathon/magento-composer-installer": "*",
          "deved-it/similar-products": "*"
      },
      "extra":{
          "magento-root-dir":"./",
          "magento-force":"true"
      }
    }


To install Similar Products for Magento and its dependencies just run composer.phar.

    $ ./composer.phar install

### Features

* Replace upsell products with products defined by PredictionIO
* Reverts to admin defined upsells when there is no data returned by PredictionIO
* Product View Actions
* Product Sale Actions
* Product Review Actions
* Guest Action Logging
* Import Existing Sales

#### Replacing Upsell Products

Configure the module to make API calls to your instance of PredictionIO, defining the host, port and engine (name and key) and data will be recorded when the user is logged in.

#### Revert to Default Upsells

When the module is disabled or the user is not logged in or PredictionIO has not returned any matching products then the module will silently revert to magento's built in upsell products allowing store admin to set these manually.

#### Product View Actions

When a customer views a product page the module will make an API call to add the product to the PredictionIO server as well as record the action of view

#### Product Sale Actions

When a customer places as an order then the module will get the parent product of the purchased simple product if available and post its ID to PredictionIO as only parent products can show the upsells.

#### Product Review Actions

When a customer reviews a product the module will get the average rating from all available ratings then make an API call to add the product rating to the PredictionIO server as well as record the action of rate

#### Guest Action Logging

Sometimes customers don't login till they get to the checkout so we log the customers actions in the session to post to PredictionIO when the customer logs in.

#### Import Existing Sales

Using the shell script included you can import all exiting sales data i.e Customers, Products and the action of conversion to kick start your data feeds. Just run the following command from your web root-

``php shell/similarity.php --store store1,store2``

Where --store looks for a comma seperated list of store names to import from. If you don't supply `--store` then all stores in your Magento installation will be imported.

#### PredictionIO

* Web: [http://prediction.io]
* Docs: [http://docs.prediction.io/current/]
* Twitter: https://twitter.com/predictionio

#### Authors

* Magento Module was developed by Steven Richardson - https://twitter.com/troongizmo

  [http://prediction.io]: http://prediction.io
  [http://docs.prediction.io/current/]: http://docs.prediction.io/current/
