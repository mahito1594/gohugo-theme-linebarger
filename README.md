# Linebarger, a theme for [Hugo](https://gohugo.io)

This is a minimal Hugo theme for myself.
*This is WIP.*

## Main Features

- KaTeX integration
- Generate lists of articles/talks from YAML|TOML|JSON,
- Get last modified date from YAML|TOML|JSON file.

### [KaTeX](https://katex.org)
When the page variable `katex` is `true`, KaTeX is loaded for math typesetting.
To typeset math formula, you enclose `$` or `\\(` & `\\)` for inline equations.
For display equations, you use `$$` or `\\[` & `\\]`.

### Generate lists from YAML|TOML|JSON
You can do it by using the shortcodes `listPapers`/`listTalks`.

#### List of articles
First of all, you put the data file which contains the information of your publications at `/data`.
The information should be given in the form:

``` yaml
# Example (YAML): /data/papers.yml
- title: "The Title of Your Publication"
  jount_work: ["Co-Author 1", "Co-Author 2", ...]
  archivePrefix: "arXiv"
  eprint: YYMM.?????
  primaryClass: "math.AG"
  published: false # set to false if it is nothing but a preprint
```

*WIP*: I will add other entries (e.g., `journal`, `volume`, `year` and so on), which are based on ones of BibTeX.

After put the data file, you can call the shortcode `listPapers`, for example:

``` markdown
{{< listPapers "papers" >}}
```

#### List of talks
Similarly, you put the data file containing the information of your talks at `/data/`.
The information should be given in the form:

``` yaml
# Example (YAML): /data/talk.yml
- title: "The title of your talk"
  seminar: "The name of seminar or conference, school and so on"
  seminar_url: "http://seminar.con" # empty allowed
  institute: "The institute where your talk is given" # optional
  city: "The city" # optional
  country: "The country" # optional
  date: YYYY-MM-DD
  note: "note" # optional
  file: "path/to/file.pdf" # optional, put the file at /static/path/to/file.pdf for example.
```

See the [Hugo Doc](https://gohugo.io/content-management/static-files/) where you should put the static file.
Then, you can call `listTalks` in a markdown file, for example:

``` markdown
{{< listTalks "talks" >}}
```

*Note*: You must put your data file in `/data/` directory.
For example, `/data/talks/2020.yml` causes an error.

### Get modified date from data files
By setting `timestamp` variable in the frontmatter, the date the data file was modified can be got.
Synopsis is `timestamp: "/data/file.suffix"` (YAML example).  Note that you must give the suffix.

I give an example:  in the frontmatter

``` markdown
---
title: "List of Talks"
timestamp: "/data/talks.yml"
---

Here I put the list of my talks...
```

## Credits

- [ress](https://github.com/filipelinhares/ress) (MIT (c) Filipe Linhares)
