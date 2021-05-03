# Contributing to flott-motion.org

## Introduction

This file documents the procedures for developing the flott-motion.org website. It targets contributors and maintainers. Contributions, be it in the form of issues or pull requests, are always welcome, so don't be shy!

At this point, this document is far from a comprehensive guide. It will be extended over time. Please open an issue, if anything is unclear, or if you need information not present here.


## Publishing News

You can add a news article to the website by adding a new directory to `content/news/` (technically a single file also works; we use directories, so we can easily add additional files, like images, to an article). Within the article directory, add `index.md`.

### Metadata

Each article has some metadata associated with it. Here's an example:

``` markdown
+++
title = "Announcing Step/Dir"
date  = 2021-01-29

[extra]
author = "hannobraun"
+++
```

`title` and `date` are pretty self-explanatory. Just make sure to update `date` before you publish, in case you started writing the new article at an earlier date.

`author` refers to an author defined in `config.toml`. Add yourself there before adding the article, if you haven't done so already.

### Publicity

If publicity for the news article is desired (which it usually is), post links to the article in the following venues:

- Rust Users forum: https://users.rust-lang.org/  
  Short (1-2 sentences) summary and link to the article. Use the "announcements" category.
- Rust Subreddit: https://www.reddit.com/r/rust/
  Link post with link to the article and a comment with a short explanation and offer to answer any questions.
- This Week in Rust: https://github.com/rust-lang/this-week-in-rust  
  Add link to the article to the "Project/Tooling Updates" section.
- Embedded WG Newsletter: https://github.com/rust-embedded/blog

Please remember to choose a descriptive title when posting to these places. On the Flott website itself, a short title is preferable. Readers from other places lack a lot of context that website visitors have, so using a longer title that better summarizes what the news is about is appropriate.

Monitor the posts you made for 1-2 weeks, and address any comments posted there.
