Notes:
	Doctrine:
		Shopware nutzt die Annotations für ORM Models und Assertions
		Repositories werden über Shopware()->Models()->getRepository('/foo/bar/bums') geholt
		Für Limiting den Doctrine Paginator nutzen
		Der einityManager wird über Shopware()->Models() geholt
		Table update immer im Save Mode $tool->updateSchema($classes,true);
		QueryBuilder sind in Shopware meistens public damit mann die Hooken kann
		Erweiterungen am QueryBuilder mit addSelect holen
		Paginator:
			$paginator = $this->getQueryPaginator($builder);
		        $data = $paginator->getIterator()->getArrayCopy();
		        $count = $paginator->count();

		Assosiations werden nicht automatisch mitgeladen. Man muss sich die selber holen
		protected function getDetailQuery($id)
	           {
	               $builder = parent::getDetailQuery($id);
	               $builder->leftJoin('association', 'alias');
	               $builder->addSelect('alias');
	               return $builder;
	           }		


	Backend & ExtJs:
		Ordner weden immer klein geschirebn und DateiNamen immer FCUp
		Stores verbinden Backendcobtroller und Model
		Das Grid definert das Windows für details 
		Das Model definert, wie die Felder in dem Detail window aussehen soll
		{s wird von smarty geparsed { s nicht
		Im Model wird der DetailWindow Conatainer angegeben
		Namespaces für Übersetzungen werden in ExtJs mit //{namespace name=foo/bar} definiert 
	
	Tipps:
		Um zu verhindern, das Shopware in einem Modul ein Template erstellt gibt es folgendes "Feature"
		public function preDispatch(){ $this->View()->loadTemplate(''); } setzt das Template auf einen leeren String
	