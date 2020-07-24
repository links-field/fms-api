# fms-api

This project uses [jekyll](https://jekyllrb.com/) with theme [just-the-docs](https://pmarsceill.github.io/just-the-docs/).

---


- To build it locally, `bundle exec jekyll serve`, remember to **comment** remote theme in `_config.yml`, use only `theme: just-the-docs`

```
#remote_theme: pmarsceill/just-the-docs
```

otherwise, the `build` will return errors about converting variables in `scss`

---

- To deploy it github, just point the root to `doc`, remember to use `remote theme` in `_config.yml`.

```
remote_theme: pmarsceill/just-the-docs
```

otherwise github page does not build it with css resource of this theme therefore cannot render the css correctly in the page.
