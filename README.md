# fms-api

This project uses [jekyll](https://jekyllrb.com/) with theme [just-the-docs](https://pmarsceill.github.io/just-the-docs/).

---
## New environment first-time setup:


### Environment setup (macOS)

[https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma]

[https://superuser.com/questions/886132/where-is-the-zshrc-file-on-mac]

1. install chruby ruby-install
```
brew install chruby ruby-install
```
2. install ruby 
> install latest version
```
ruby-install
``` 

3. add source into ~/.zchrc and set
`chruby [version]` to switch to the ruby version you'd like to use
(instead of using macos ruby)

4. install jekyll
```
gem install bundler jekyll
```

### First Execution

1. `cd docs`
2. `bundle update`
3. `bundle install`

Next to Get started


---

## Get started
- To build it locally, 
```
bundle exec jekyll serve
```
remember to _comment_ remote theme in `_config.yml`, use only `theme: just-the-docs`

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
