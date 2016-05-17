#Day 3

##Extending Bundles
* Use the Shopware media bundle for orientation

#### Search Bundle
* The search bundle is highly abstracted
* To add queries for the search you have to add a new criteria object
* To add conditions for the criteria object you have to add a new condition which implements the ConditionInterface object
* The search needs to know there context. To get the product context use `$contextFactory->createProductsContextInterface()`
* To register a new service, use a custom event
* To extend a current service use the decorator pattern
