#Day 2

##Plugins

####Doctrine
* Shopware use ORM Annotations and Assertions
* To get a repository use `Shopware()->Models()->getRepository('/foo/bar/bums')`
* To get the entity manager use `Shopware()->Models()`
* Always use the doctrine paginator for limiting

```
  $paginator = $this->getQueryPaginator($builder);
  $data = $paginator->getIterator()->getArrayCopy();
  $count = $paginator->count();
```

* To prevent clearing all data on an alter table force the save mode in schema updates `$tool->updateSchema($classes,true);`
* Query builder functions are mostly public to make them hookable
* To extend a query builder just call a further addSelect
* by default no association will be auto loaded. If you want more data you have to modify the query builder

```
    protected function getDetailQuery($id)
    {
       $builder = parent::getDetailQuery($id);
       $builder->leftJoin('association', 'alias');
       $builder->addSelect('alias');
       return $builder;
    }
```

####Backend & ExJs
* Folders are always lowercase file first case upper
* Stores are used to combine the Shopware backend controller and the model
* The Shopware backend grid component is used to define all detail windows
* The Model defines which fields are viewable in the detail window
* The detail window container path will be placed in the model file
* To realize translations using smarty inside of a backend js file use the smarty namespaces in a js comment `//{namespace name=foo/bar}`

##Tips
* to prevent Shopware to render a template e.g. in case of a API module simply use an empty template string
  ```
    public function preDispatch()
    {
        $this->View()->loadTemplate('');
    }
  ```