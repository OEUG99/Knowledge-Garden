# 👾 Development Blog:
	- {{query (page-property category [[Development Blog]] ) (order-by updated-at desc)}}
- # 📝 Personal Blog:
	- {{query (page-property category Blog) (order-by updated-at desc)}}
	  query-properties:: [:title :page :created-at :updated-at]