# Quarto Science Project
An example of how to organize a science project using Quarto


[Quarto](https://quarto.org/) is a powerful tool to mix text, code, html objects, and bring everything into a unified website. The website runs locally (by default), and allows to bring together information, thoughts and ideas from a patchwork of sources. This Github repository is an attempt to draft the architecture of a science project using quarto.

Using the principle of markup language (*e.g.* Markdown files), Quarto allows to not only display code into a neat visual way, but can execute code cells using Python, R, Julia or else given your machine is equipped with the proper executables and environment. For the gridcell to be executed, it needs to have the language of choice within curly brackets on top of the code block. Plenty of explanation are provided on Quarto's [website](https://quarto.org/docs/get-started/hello/text-editor.html). Quarto has many features. One of them is to compile the `.qmd` files into a website. There is plenty of documentation too on their [website](https://quarto.org/docs/websites/).

Here we will focus on how a science project can benefit from using quarto and how it can be orginzed. 

```
My_project/
	- README.md
	- LICENSE
	- my_science_project/
		- index.qmd
		- jounal.qmd
		- about.qmd
		- myscript.qmd
		- styles.css
	- data/
```



```sh
quarto create project website my_science_project
```

Then create a folder for witholding data:
```sh
mkdir data
```

Create a journal page, bibtex reference file:
```sh
touch my_science_project/journal.qmd

```
The journal page will be used to summarize all activitie into a single page for records.


Quarto can parse bibtex reference given Pandoc is installed.
```sh
touch my_science_project/references.bib
```


Modify the file `_quarto.yml` to your liking
```yml
project:
  type: website

website:
  title: "My Science"
  navbar:
    left:
      - href: index.qmd
        text: Home
      - journal.qmd
      - about.qmd
      

format:
  html:
    theme:
      - cosmo
      - brand
    css: styles.css
    toc: true
    grid:
      body-width: 1200px
    bibliography: references.bib
    bibliographystyle: apa
```

Finally, start exploring the data using `.qmd` files. These files can be added to the index either as links or tabs, to be modified in the  `_quarto.yml`. 

The folder `my_science_project` is a dummy example of what such Quarto project may looks like. Once all is in place, simply run the website locally with `quarto preview my_science_project`.

---

**Advantages**:
- bring everything in one dynamic document
	- notes
	- code
	- references
	- data, etc.
- All files are raw text and can be open and edited with any text editor
- The html website can be shared to anyone
- Forced to do reproducible code. As the code is run everytime, it must be clean and organized
- Modular at your wish within the scope to what Quarto offers (a lot!).

**Limits**:
- A fair amount of manual setup to perform that may be a steep learning curve at first.
- For project with large dataset, think to preprocess data, and store intermediate stage of the data.
- Not suited for heavy processing task. Prefer then simple `.py` files run in their own console 
