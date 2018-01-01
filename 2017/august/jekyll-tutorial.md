# directory purposes

- `_layouts`: the glue that glues different pieces
- `_includes`: the common pieces such as header, footer, etc
- `_site`: where generated content is, no need to touch


# using layout

```
---
layout: layout-file-name
---
```
`layout-file-name` can be `post`, `page` for example


# adding directories to build

add to `_config.yml`

```
include:
  - _{dir-name}
```

# assinging url

by:

```
permalink: /{name}/
```
