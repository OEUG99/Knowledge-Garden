tags:: [[Programming]] [[JavaScript]] [[NextJS]]
- https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes
  documentation::
- Dynamic routes are useful for when you do not know the exact segment name ahead of time and want to create routes from dynamic data.
- ## Convention
  heading:: 2
	- Dynamic segments can be created by wrapping a folder's name in square brackets: `[folderName]`. For example, `[id]` or `[slug]`.
	- Dynamic segments can be accessed from [[NextJS/useRouter]]