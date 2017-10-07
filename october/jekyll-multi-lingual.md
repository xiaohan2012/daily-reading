# how to use this plugin

https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin#7-example-website

# hints

- `language.yml`: contains the lingual-independent names
  - use `{% t global.{key_name} %}` to get the translation
- include translated file: `{% tf pagename/blockname.md %}` to get the translated file
- translate link `{% tl team fr %}`
  - https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin#53-permalinks-and-translating-links
- 