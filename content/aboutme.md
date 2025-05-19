---
# Page title
title: My page
# Page type - we want a landing page (such as a homepage)
type: landing

# Your landing page sections - add as many different content blocks as you like
sections:
  sections:
  - block: collection
    id: section-1
    content:
      title: Section 1
      subtitle: A subtitle
      text: Add any **markdown** formatted content here
      filters:
        folders:
          - post
    design:
      columns: '2'
      view: showcase
      flip_alt_rows: true
---