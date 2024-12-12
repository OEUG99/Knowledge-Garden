# Same-Origin Policy (SOP)
	- ## What is SOP?
		- SOP is a fundamental security feature implemented by web browsers to protect users from malicious websites trying to steal or manipulate sensitive data.
		- It restricts how documents loaded from one origin can interact with another origin.
		- This policy is crucial for protecting sensitive data like cookies or session/auth tokens.
	- ## What defines an Origin?
		- An origin is defined by three components:
		  1. **Scheme (Protocol)** - `http`, `https`, `ftp`, etc.
		  2. **Host (Domain)**
		  3. **Port**
	- ## Restrictions of SOP
		- SOP restricts the following:
			- DOM Access
			- Cookies
			- AJAX Requests
			- Local Storage / Session Storage
	- ## Bypassing SOP
		- **CORS** can be used to allow other origins to access resources.
		- Proxy servers and `nginx` can be used to make it seem like it’s all the same origin.