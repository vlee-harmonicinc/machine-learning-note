This is some machine learning note, mainly is neural network. It is not comprehensive, just some topics I interested in.  
Not finished yet  
It was written in google doc as a personal note. But it become inconvenient when the doc become longer. So I decided to re-organize it.  
I have not read all papers. I just drop a short note when I read it from related work or reference list. I hope I will have time to read it someday :P  

# Requirement
`pip3 install sphinx sphinx-autobuild sphinx_rtd_theme recommonmark jieba sphinx_markdown_tables`  
sphinx: build rst to html  
sphinx_rtd_theme: readthedoc theme  
recommonmark: sphinx extension for markdown  
jieba: chinese search engine  
sphinx_markdown_tables: render table

# Build
## config
This section should be skipped since it already generated, but if you want to config your own page, run
`sphinx-quickstart`  
## build html
`make html`
## server
`cd build/html`
`python3 -m http.server`