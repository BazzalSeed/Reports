## Migration Process

###### repo urls
svn+ssh://matt@dev.locately.com/ebs/repo/siphon/
svn+ssh://matt@dev.locately.com/ebs/repo/caliper/
svn+ssh://matt@dev.locately.com/ebs/repo/aws/
###### procedure (siphon as example)
 **A. Generate users mapping file**

1. navigate to the svn repo and run
```
svn log --xml | grep author | sort -u | perl -pe 's/.*>(.*?)<.*/$1 = /' | tee users.txt
```
2. establish the mapping by finish writing users.txt
```
eg.
dfinkel = Dan Finkel<dfinkel@smg.com>
drew = Drew<drew@smg.com>
eric = Eric<eric@smg.com>
fgruhn = Fred Gruhn<fgruhn@smg.com>
```

**B. Generate Local Git repo from SVN (svn+ssh)**

1.  pull the SVN data from the repository

  ```
    git svn clone --stdlayout --no-metadata --authors-file=users.txt svn://hostname/path dest_dir-tmp

  ```
    in this case
    *  users.txt = users.txt
    * dest_dir-tmp = siphon

2. Likely, the process will error out encountering error user name not found.
   In that case
   * go back to users.txt
   * add in the user mapping as indicated by the error message

3. continue the pulling process
   *  navigate to local git repo and run
   ```
   git svn fetch
   ```
   * if encountered the error described in step2,loop back to step2

**C.Push to Github**

Now  you should have a working local git repo. Unlike SVN, a local repo (working copy) has all the information of the repo. It's a local clone of all distributed information. This is where the power of distributed workflow come from.

The process of pushing local repo to remote on any git service (github in this case) is fairly trivial. Follow the standard procedure described by github

=====

## Tutorials

This section has two parts. Part 1 addresses how we uses git (not github) as our source control technology based on our svn knowledge

##### A.Git to know you
Instead of me writing tutorial, it is probably better for me to gather existing well-written tutorial here

1. [A very good introduction to git](https://www.youtube.com/watch?v=0fKg7e37bQE)
should give you enough knowledge to satisfy our needs for work
2. [From SVN to GIT](https://git-scm.com/course/svn.html) gives you nice comparison between using SVN and GIT



##### B.Github Review Process
Review-board functions ok in our workflow but sometimes rather counter-intuitive especially when the process requires more people involved or live feedback. The new workflow based on github should allow us to collaborate in a much more integrated and intuitive fashion(no need to generate .diff then uploading anymore).

1. [Introduction to team workflow on git](https://www.youtube.com/watch?v=oFYyTZwMyAg&t=453s) should give you enough grounds to use this new workflow
2. [A more in-depth discussion](https://www.youtube.com/watch?v=EwWZbyjDs9c) if you want more detail about the design philosophy
