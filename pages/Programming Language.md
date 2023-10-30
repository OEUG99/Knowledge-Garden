# Navigation:
	- {:title "Pages with a programming language tag"
	  query-sort-by:: block
	  query-table:: false
	  query-sort-desc:: true
	  query-properties:: [:page]
	   :query [:find (pull ?p [*])
	           :where
	           [?p :block/properties {"tags" ?tags}]
	           [(= ?tags "programming language")]]}
-
-
-
-