# Welcome to My Note for Meeting

Containing note for meeting, talks, weekly report, etc.

This note is now build with [MkDocs](http://www.mkdocs.org/).

## To install and build this note

* Install MkDocs

```shell
pip install mkdocs
```

* Python-Markdown is needed for correct rendering math equation. Please consider installing [my fork](https://github.com/chaonan99/python-markdown-math) of this extension (I am used to `$XXX$` for inline math and `$$XXX$$` for stand alone).

```shell
git clone https://github.com/chaonan99/python-markdown-math.git
cd python-markdown-math
python setup.py build
python setup.py install
```

* Use mkdocs' server to view the note (in paper dir)

```shell
mkdocs serve
```

Here are some useful mkdocs command.

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">chaonan99's note</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://chaonan99.github.io" property="cc:attributionName" rel="cc:attributionURL">Haonan Chen</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
