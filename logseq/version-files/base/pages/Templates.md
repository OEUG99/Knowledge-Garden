exclude-from-graph-view:: true

- <% time %> |  [[Templates]]
  template:: Note
  collapsed:: true
	- # Topic
	  heading:: 1
		-
-
- <% time %>
  template:: Daily
  collapsed:: true
	- # Topic
	  heading:: 1
-
- # Table of Contents:
  template:: NamespaceTOC
  heading:: 1
	- {{query    (and (namespace <% current page %>) (sort-by title asc))}}
	  query-sort-by:: block
	  query-table:: false
	  query-sort-desc:: true
	  query-properties:: [:title]
-
- # Books
  template:: Book
  template-including-parent:: false
  heading:: 1
- exclude-from-graph-view:: true
  abbreviated-title::
  start::
  cover:: ![Image](    ){:height 172, :width 98}
  type:: [[Book]]
  title::
  author::
  year::
  status::
  source-url:: [Goodreads]( )
  end::
  location::
  tags::
	- ## Content
	  heading:: 2
-
- exclude-from-graph-view:: true
  template:: exclude from graph
-
- # Leetcode
  heading:: 1
	- topic:: [[Leetcode]]
	  pattern::
	  theme::
	  template:: Leetcode
	  source-url::
-
- # Court Case
  topic:: []
  amendment:: []
  template:: Case Briefing
  heading:: 1
  collapsed:: true
	- ## Facts:
	  heading:: 2
	- ## Legal Issues
	  heading:: 2
	- ## Holding:
	  heading:: 2
	- ## Reasoning:
	  heading:: 2
- # Daily Page
  template:: Daily Page
  template-including-parent:: false
  heading:: 1
	- <%time%>
		- [[]]
		  topic:: []
		  tags::
			-
- # Daily Note
  template:: Daily Note
  heading:: 1
	- <%time%>  |
- # Daily Schedule:
  template:: Schedule
  heading:: 1
	- {{renderer :smartblock, Daily Note, Journal Entry, true}} | {{renderer :smartblock, Daily Page, Page Entry, true}} | {{renderer :smartblock, Article Summary, Article Summary, false}}
	-
- # Article Summary
  template:: Article Summary
  heading:: 1
	- <%time%>
		- # Article Name
		  read-date:: <%today%>
		  published-date::
		  author::
		  publication::
		  source-url::
		  archive-source-url::
		  tags::
		  heading:: 1
			- ## Summary
			  heading:: 2
			- ## Key Points
			  heading:: 2
			- ## Reflections
			  heading:: 2
			- ## Questions
			  heading:: 2