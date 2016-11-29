### Migration Process
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


### Tutorials
##### Git to know you
##### Github Review Process
