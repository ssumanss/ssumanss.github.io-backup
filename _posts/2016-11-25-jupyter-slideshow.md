---
title: Jupyter SlideShow
date: 2016-11-25 9:52
tags: Python, Jupyter
category: Python
slug: jupyter-slideshow
summary: This post will illustrate how to create beautiful slide in jupyter that runs on browser and shared online easily. 
---

## Introduction 

Slides are integral part of engaging presentations. Here we learn how to create slides in jupyter that can be run in your browser. 

## Steps 

1. In a jupyter file first choose slideshow from view menu `view > slideshow` as follows

    ![img](../images/adding_slides.png) 

2. It will add few choices in each cell as follows

    ![img](../images/slide_choices.png) 
    
    The choices are 
    
    - **Slide:** Will create a new slide from the cell. Each new slide appear horizontally. 
    - **Sub-slide:** This will also create new slide but it will transition vertically.
    - **Fragment:** A part of slide appear in each forward. 
    - **Skip:** This will not added in slideshow.
    - **Notes:** 

3. Change the cell setting to `makrdown`. Write the content in markdown.

    ![img](../images/change_to_markdown.png)

## Viewing the slides

The slide is a webpage like others you see often on internet. It uses a javascript library `raveal.js`. To view the file locally we have to download the `reveal.js` library in the same folder. We can use `git` to download. 
    
```shell
git clone https://github.com/hakimel/reveal.js.git
```
Now to view the file in your browser enter the following in the commandline.  

```shell
jupyter-nbconvert  slides.ipynb \
         --reveal-prefix=reveal.js --to slides --post serve
```

It will open a new tab in your browser with slides are open. Use arrow keys to navigate.
     
## Customization 
`Revial.js` comes with some default themes and transitions. To apply a theme say `sheif` and transition `cube` just add `?theme=sherif&transition=cube` in the end of presentation url. 

More advanced Customization is possible through writing your own styple files. 

### Default themes
The framework comes with a few different themes included:

- black: Black background, white text, blue links (default theme)
- white: White background, black text, blue links
- league: Gray background, white text, blue links (default theme - for reveal.js < 3.0.0)
- beige: Beige background, dark text, brown links
- sky: Blue background, thin dark text, blue links
- night: Black background, thick white text, orange links
- serif: Cappuccino background, gray text, brown links
- simple: White background, black text, blue links
- solarized: Cream-colored background, dark green text, blue links

## Refrences:

1. [Presentation slides with Jupyter Notebook](http://echorand.me/presentation-slides-with-jupyter-notebook.html)
2. [Giving presentations with IPython notebook](http://neuroscience.telenczuk.pl/?p=607)
3. [Make your slides with IPython](http://www.damian.oquanta.info/posts/make-your-slides-with-ipython.html)
4. [Jupyter notebook presentation extension](https://docs.continuum.io/anaconda/jupyter-notebook-extensions)
5. [Converting notebook to other format](https://ipython.org/ipython-doc/3/notebook/nbconvert.html)