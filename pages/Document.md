exclude-from-graph-view:: true

- # List of Documents
	- The following is a list to the highlight pages for each document synced via readwise.
	- {{query (namespace [[Document]])}}
	  query-properties:: [:page :updated-at]
	  query-sort-by:: updated-at
	  query-sort-desc:: true
	-