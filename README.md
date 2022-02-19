# Build static web sites with hugo

## Install Hugo
https://gohugo.io/getting-started/installing/

## Make a web site and Creatw git repository
```
hugo new site [repository name]
```
```
git init
```

## Install a theme

theme list and demo
https://themes.gohugo.io/

```
git submodule add [theme repository] themes/[theme name]
```

## Create a new contents
```
hugo new content/post/[]/index.md
```

## Compile
```
hugo
```

## Launch a localhost server 
```
hugo server
```

if launching including drafts
```
hugo server -D
```
