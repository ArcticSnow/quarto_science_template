# quarto_science_project
An example of how to organize a science project using Quarto


[Quarto](https://quarto.org/) is a powerful tool to mix text, code, html objects, and bring everyhting into a unified website. The website can be run locally, and allows to bring together information, thoughts and ideas from a patchwork of sources. This Github repository is an attempt to draft the architecture of a science project using quarto.

Using the principle of markup language used by Markdown files, Quarto allows to not only display code into a neat visual way, but can execute code cells using Python, R, Julia or else given your machine is equipped with the proper executable and environment. For the gridcell to be executed, it needs have the language of choice within curly brackets on top of the code block. Plenty of explanation are provided on Quarto's [website](https://quarto.org/docs/get-started/hello/text-editor.html). Quarto has many features. One of them is to compile the `.qmd` files into a website. There is plenty of documentation too on their [website](https://quarto.org/docs/websites/).

Here we will focus on how a science project can benefit from usinng quarto and how it can be orginzed. 

```
My_project
	- README.md
	- LICENSE
	- my_sciene_project
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
touch my_science_site/journal.qmd

```
The journal page will be used to summarize all activitie into a single page for records.


Quarto can parse bibtex reference given Pandoc is installed.
```sh
touch my_science_site/references.bib
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

Finally, start explorind the data using `.qmd` files. These files can be added to the index either as link or tabs (modify `_quarto.yml` accordingly. 