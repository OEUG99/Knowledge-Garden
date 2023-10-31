tags:: #GIT

- To create secret section in Logseq that does not appear in your git repo, you first need to create a `.gitignore` file in your graph's root directory. Inside this file, add the following:
  ```
  pages/secret*
  ```
- Then you want to create a namespace called [[Secret]], this namespace will store all your secrets.
- NOTE: Secrets should only remain as plain text, as assets in Logseq are stored in the `assets` folder, not the pages folder. It is also worth mentioning, that these secrets can not be accessed on other devices.