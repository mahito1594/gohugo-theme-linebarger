# Linebarger, a theme for [Hugo](https://gohugo.io)

This is a minimal Hugo theme for myself.
*This is WIP.*

## Main Features

- Generate lists of ~~articles~~/talks from YAML|TOML|JSON,
- Get last modified date from YAML|TOML|JSON file.

### Generate lists from YAML|TOML|JSON
You can do it by using the shortcode `listTalks`.

First, you put the data file containing the information of your talks at `/data/`.
The information should be given in the form:

``` yaml
# Example (YAML): /data/talk.yml
- title: "The title of your talk"
  seminar: "The name of seminar or conference, school and so on"
  seminar_url: "http://seminar.con" # empty allowed
  institute: "The institute where your talk is given"
  city: "The city"
  country: "The country"
  date: YYYY-MM-DD
```

Then, you can call `listTalks` in a markdown file, for example:

``` markdown
{{< listTalks "talks" >}}
```

*Note*: You must put your data file in `/data/` directory.
For example, `/data/talks/2020.yml` causes an error.

### Get modified date from data files
By setting `timestamp` variable in the frontmatter, the date the data file was modified can be got.
The author thank [the weblog article](https://42-design.work/technology/hugo-old-entry-alert/)(Japanese).
Note that this method needs an environmental variable.
I give an example:  in the frontmatter

``` markdown
---
- title: "List of Talks"
- timestamp: "TS_TALKS"
---

Here I put the list of my talks...
```

Then, you build the website by

``` shell
TS_TALKS=$(date -r data/talks.yml) hugo
```

## Credits

- [ress](https://github.com/filipelinhares/ress) (MIT (c) Filipe Linhares)
