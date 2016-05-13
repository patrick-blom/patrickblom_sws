#DAY 1

##Configurations
* The default configuration is located under `engine/Shopware/Configs/Default.php`
* During the development you should disable caching and enable ExceptionThrowing in your shop config
```
    'front' => array(
        'noErrorHandler' => true,
        'throwExceptions' => true
        ),
    'template' => array(
        'forceCompile' => true
        );

```
##Plugins
####Global
* To define requirements between plugins use `$this->assertRequiredPluginsPresent(array('plugin_id1','plugin_id2'))` in the plugin bootstrap
* If there is no update function defined in the bootstrap file the install method will be called on an update
* Before a controller dispatch the preDispatch event will be fired
* After a controller dispatch the postDispatch event will be fired
* To define template vars use `$this->View()->assign('foo','bar')` or `$this->View()->foo = bar`
* In Shopware the following controller types are present
  * Frontend
  * Backend
  * Widget
  * API

####Backend
* Every .js file will be parsed by smarty
* controllers are always lowercase
* Always place a space character between { and the following sign in js objects. Otherwise smarty tries to parse these tags and dies an evil death
* Use smarty blocks to extend data models
* Menu items icons will be controlled by CSS classes
* To realize a dropdown you have to implement a custom store. There is the possibility to override the field definitions
* The default backend modules are stored under `themes/Backend/ExtJs/backend/base/application`

##Events
* Prefer events instead of hooks
* To subscribe on a Event `$this->subscribeEvent(Event, Callback, position)`
  * The position could be positive or negative
* Shopware knows the following event types
  * Notify: only informative
  * NotifyUntil: informants and stops the process if something !null is return
  * Filter: can manipulate data

##Hooks
* Hooks got always an argument from type Enlight_Hook_HookArgs
* Every Class is hookable
* Shopware knows the following hook types
  * before: will be call before the execution of a method
  * after: will be call after the execution of a method
  * replace: will replace the entire method

##API
* To use the article number as article id set the url param `useNumberAsId=1`
* To get a nice result during the development set the url param `pretty=1`
* API updates are allways incremental
* Use the Shopware paginator in case of ManyToMany or ManyToOne Resources
