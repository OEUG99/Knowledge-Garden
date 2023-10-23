# TODOS:
heading:: 1
	- TODO remove the install.sh as this can be handled by the Dockerfile
	- TODO move AWS classes into the dependencies repo, so other microservices can use them if they like.
	- TODO set up configs for prod and dev, such that AWS secrets are not being used in dev, etc.
	- TODO write docstrings
	- TODO unit testing and intergration testing
	- TODO fix the following:
	  ```
	  ARG AWS_SECRET_KEY_NAME
	  ```
	  such that it states what it is, as in the JWTs ecret  key name
		- Would it make sense just to have 1 secret that has multiple key value pairs per service?
			- If so, we should rename the AWS secret such that it reflects the whole service rather then just JWT
	- TODO Implement a cache for secrets, otherwise when their is slow speeds there is a bottleneck + also you save money!
	- TODO write response for when username is already in use.
	-
- # Docs
  heading:: 1
	- https://reactrouter.com/en/main/start/tutorial
	-