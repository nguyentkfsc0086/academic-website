---
title: Blogs
summary: My journal
type: landing

cascade:
  - _target:
      kind: page
    params:
      show_breadcrumb: true

sections:
  - block: collection
    id: Blogs
    content:
      title: Blogs
      filters:
        folders:
          - blogs
    design:
      view: article-grid
      columns: 2
---