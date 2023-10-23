exclude-from-graph-view:: true

- # Currently Reading:
  heading:: 1
	- {{query (and (page-property category [[Book]]) (page-property status Reading))}}
	  query-sort-by:: updated-at
	  query-table:: true
	  query-sort-desc:: true
	  query-properties:: [:cover :status :title :author :link :start :created-at :abbreviated-title :updated-at :page :category]
	-