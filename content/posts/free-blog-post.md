+++
title = "How to create a host your own blog for free"
date = 2019-06-07T10:27:00+02:00
draft = true
+++

How did I created my blog hosted for free and without ads.

I have used:

1.- Firebase to host my static website for free.

2.- Hugo to create my website.

Detailed steps:

- Create a domain for a static database on firebase.google.com. https://firebase.google.com/docs/hosting

```
sudo npm install -g firebase-tools
cd about-ml-website/
firebase login
firebase init
firebase serve
firebase deploy
```

- Create a website for your blog with Hugo: https://github.com/gohugoio/hugo/releases

```
./hugo version
./hugo new site ml-blog
```

  Congratulations! Your new Hugo site is created in /Users/ana/Documents/software/hugo_0.55.6_macOS-64bit/ml-blog.

  Just a few more steps and you're ready to go:

  1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
  2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
  3. Start the built-in live server via "hugo server".

  Visit https://gohugo.io/ for quickstart guide and full documentation.

```
cd ml-blog
git clone https://github.com/ijsucceed/onepress.git
mv onepress/ themes/
cd ..
cp themes/onepress/exampleSite/config.toml  .
.././hugo server -D
cp themes/onepress/archetypes/* archetypes/
mkdir content/posts
.././hugo new posts/free-blog-post.md 
```


- Before you go crazy with how much content you create, remember to version control your development:
```
git init
git config --global user.name "anamf"
git config --global user.email "anam.martinezf@gmail.com"

for DIR in `ls -p | grep /`; do touch ${DIR}.gitkeep; done #to include empty directories
echo "public" >> .gitignore
git add .
git commit -m 'First commit of your blog site.'