title:: Archive/Graph/Secret

- This  graph uses a custom secret management service designed by [[@Oli Eugenio]].
- Next to every #Archive/Graph/Secret tag will have an external link to the secrets manager. All the secrets are hidden by a global password, once entered the secrets manager website will display the secrets contents.
- This secret manager is not intended to store critical information, and is mainly used to store minor information you do not want public.
- # Why have a secret manager?
	- This graph employs the use of secrets in such a manner, due to all the notes being publicly available via the Github repo and on its [website](eugenio.software).
	- By having a secret manager system on a public graph, we can use Logseq as a way to act as a contact manager, hiding information like phone numbers from the public, but still allowing that information to be easily retrievable by you the author.
		- In some sense, this adds semi-private functionality to a public Graph
- # How to get the secrets manager?
	- The secret manager is freely available on its GitHub repo, which can be found in [[Projects/Secrets Manager]]. If you would like to host your own instance, feel free to do so.
		- Alternatively, you could use [pastebin](pastebin.com) and create password protected pastes or private pastes and link those instead if you are not able to host your own instance.