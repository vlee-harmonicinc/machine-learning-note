This notes breifly mark some paper to keep track of the development on some machine learning topics that I interest in and understand the main contribution of each paper. 


To be honest, for most of paper, I haven't read every sections of it. Some of paper haven't been read at all, just mark some link. Please correct me in git issue/pull request if I wrote something wrong.

## Requirements
`pip3 install sphinx sphinx-autobuild sphinx_rtd_theme recommonmark jieba sphinx_markdown_tables`  
sphinx: build rst to html  
sphinx_rtd_theme: readthedoc theme  
recommonmark: sphinx extension for markdown  
jieba: chinese search engine  
sphinx_markdown_tables: render table

## Build
### config
This section should be skipped since it already generated, but if you want to config your own page, run
`sphinx-quickstart`  
### build html
`make html`
### host HTTP server
`cd build/html`
`python3 -m http.server`