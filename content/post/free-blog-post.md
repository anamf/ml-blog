+++
title = "How to create a host your own blog for free"
date = 2019-06-07T10:27:00+02:00
draft = false
+++

How did I created my blog hosted for free and without ads.

I have used:

1. Firebase to host my static website for free.

2. Hugo to create my website.

Detailed steps:

1. Create a domain for a static database on firebase.google.com. https://firebase.google.com/docs/hosting

```
sudo npm install -g firebase-tools
cd about-ml-website/
firebase login
firebase init
firebase serve
firebase deploy
```

2. Create a website for your blog with Hugo: https://github.com/gohugoio/hugo/releases

```
#Download Hugo (optionally:)
sudo mv software/hugo_0.55.6_macOS-64bit/hugo /usr/local/bi
./hugo version
./hugo new site ml-blog

  Congratulations! Your new Hugo site is created in /Users/ana/Documents/software/hugo_0.55.6_macOS-64bit/ml-blog.

  Just a few more steps and you're ready to go:

  1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
  2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
  3. Start the built-in live server via "hugo server".

  Visit https://gohugo.io/ for quickstart guide and full documentation.
cd ml-blog
git clone https://github.com/ijsucceed/onepress.git
mv onepress/ themes/
cd ..
cp themes/onepress/exampleSite/config.toml  .
cp themes/onepress/archetypes/* archetypes/
#copy everything in the exampleSite folder into the corresponding directory.
mkdir content/posts
.././hugo new posts/free-blog-post.md 
.././hugo server -D #to check your content on localhost, e.g. http://localhost:50927
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
#Create your repository on GitHub
git remote add origin https://github.com/anamf/mymlblog.git
git push -u origin master
```

- Finally, to build our site and generating all the html files simply run:
```
rm -r public
../.hugo & firebase deploy
```
 You will be able to find all the html files under the public directory.


#Consider the possibility to use GitHub pages, instructions here: https://dev.to/dgavlock/creating-a-hugo-site-on-github-pages-3cjo