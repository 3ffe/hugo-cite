# hugo-cite customization

This is a fork of hugo-cite from [loup-brun/hugo-cite](https://github.com/loup-brun/hugo-cite). While the original repo seems to be no longer maintained, this fork works well with the latest hugo version (0.16). Changes made:

1. Replaced deprecated `echoParam` with `index .Params`.
2. Replaced deprecated `getJSON` with `resources.Get` and `transform.Unmarshal`.
3. Deleted the code block enclosed in `<dt>` in `themes/hugo-cite/layouts/partials/bibliography-list.html`, for removing the citation key in front of each entry in bibliography list, added numerical counter in `[n]` format.

## How to use 
1. Install the theme with git submodule
```shell
git submodule add --depth=1 https://github.com/3ffe/hugo-cite themes/hugo-cite
```

2. Use `pandoc` to convert your `.bib` file into CSL-JSON required by this theme. The command is 
```shell
pandoc ref.bib -t csljson -o bib.json
```
The two files are placed inside the `assets/` folder. 

3. In your markdown page front matter, you specify your bib file location as
```
bibFile: bib.json
```
No `assets/` path prefix is needed.

4. To uninstall the theme, run the following two commands:
```shell
# remove hugo-cite submodule
git rm themes/hugo-cite
# clean up git record
rm -rf .git/modules/themes/hugo-cite
```