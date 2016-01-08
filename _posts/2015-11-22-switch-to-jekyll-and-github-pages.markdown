---
layout: post
title:  "How have I switched to Jekyll and GitHub pages"
date:   2015-11-22
categories: other blog
summary: summary
---

I has been planning to switch by blog to [Jekyll](http://jekyllrb.com/) (simple static site generator) and start 
publishing regularly. I've just done first part of this plan ;) Migration was incredibly easy\!

## Switch to Jekyll

What have I done (step by step):

1. [install](http://jekyllrb.com/docs/installation/) required software and Jekyll itself
2. generate blog infrastructure with example contents: `jekyll new myblog`
3. launch generated blog:
``` cd myblog
jekyll serve
```
4. replace or remove example texts and data
5. rewrite my two last year's posts into markdown format and put files in _posts folder
6. refresh browser and see changes

I've encountered only one problem: one of two posts was not generated at once. Why? Because I had different dates in file
name and in file metadata.

Please note that you must follow following convention when giving names to files with your posts:
`yyyy-MM-dd-<title>.markdown`

And the simplest pattern of file contents is: 
```---
layout: post
title:  "<your post's title - could be different than in file name>"
date:   <date - same as if file name>
categories: <category> <subcategory>
---
Your text
```

Given categories will be part of path to generated html file with your post.

After some improvements and styling work blogging is very simple. You must add markdown file with your post - and that's all\!

## Hosting with GitHub Pages

When blog is ready hosting it with GitHub Pages is very simple:

1. on GitHub create git repository with following name:
`<your_username>.github.io`
2. go to folder with blog project
3. init git repository, commit changes
```git init
git add .
git commit -m "<commit_message>"
```
4. add repository created in first step as remote and push
```git remote add origin https://github.com/<your_username>/<your_username>.github.io.git
git push -u origin master
```
5. navigate to: 
`http://<your_username>.github.io`
...and see that it works!