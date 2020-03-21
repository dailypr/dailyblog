---
title: "Hugo - Getting Started"
date: 2020-03-21
tags: [hugo]
---

Getting Started - Hugo 
---
Beginning... 
1. git clone https://github.com/dailypr/dailyblog.git  
2. start from empty space  
3. hugo new site dailyblog  
4. cd dailyblog  
5. git submodule add https://github.com/PippoRJ/hugo-refresh.git themes/hugo-refresh  
6. rm config.toml  
7. curl -O https://raw.githubusercontent.com/PippoRJ/hugo-refresh/master/exampleSite/config.yaml  
8. write post  
9. modify config  
10. hugo server and check locally  
11. rm -rf public  
12. git submodule add -b master https://github.com/dailypr/dailypr.github.io.git public  
13. hugo -D   
14. cd public  and push to git  ( git remote -v )  
> ➜  public git:(master) git remote -v
> origin	https://github.com/dailypr/dailypr.github.io.git (fetch)
> origin	https://github.com/dailypr/dailypr.github.io.git (push)
15. cd ..  and push to git ( git remote -v )  
> ➜  dailyblog git:(master) ✗ git remote -v
> origin	https://github.com/dailypr/dailyblog.git (fetch)
> origin	https://github.com/dailypr/dailyblog.git (push)

---
Add New Post
1. add post
2. hugo server and check locally 
3. rm -rf ~/Documents/0_git/dailyblog/dailyblog/public/
4. rm -rf ~/Documents/0_git/dailyblog/.git/modules/dailyblog/public/
5. git rm --cached public
6. git submodule add -b master https://github.com/dailypr/dailypr.github.io.git public
7. hugo -D 
8. cd public  and push to git  ( git remote -v ) 
9. cd ..  and push to git ( git remote -v )  
