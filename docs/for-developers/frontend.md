---
sidebar_position: 2
---

# Frontend

This is a part of Ratio project.

## Structure

```
src/
  components/           - generic, reusable components applicable to every page/view
    comments/           - related components (comments/, list/ ...)
    ...
    list/
    ...
  contexts/             - React.js contexts
    ...
  hooks/                - React.js hooks
    ...
  intl/                 - internationalisation
    locales/            - available languages
      en/
      ru/
    ...
  layout/               - components representing common layout blocks, e.g. Navbar, Footer etc
    ...
  styles/               - styled components and CSS-related constants
    ...
  utils/                - utilities and small reusable functions
    ...
  views/                - components specific to some page/view/module
    tasks/
    users/
    ...
```
