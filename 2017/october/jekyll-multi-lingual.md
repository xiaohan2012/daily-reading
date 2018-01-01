# how to use this plugin

https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin#7-example-website

# hints

- `language.yml`: contains the lingual-independent names
  - use `{% t global.{key_name} %}` to get the translation
- include translated file: `{% tf pagename/blockname.md %}` to get the translated file
- translate link `{% tl team fr %}`
  - https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin#53-permalinks-and-translating-links
- links to other languages: https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin/blob/master/example/_includes/post.html


# learned

- to use the strings in `{lang}.yml`, remeber to wrap `{% t ... %}`, `{{ }}` won't give anything. 
  - if you want to use `{{ }}`, define them in `_config.yml`
  - I think `{% t .. %}` tells jeykll to look for strings in `{lang}.yml`

# flags

http://193.166.24.212:4000/cn/

# misc

- change `lang=""` in `_layouts/default.html`	


