***

## Making an new branch

-> You have to first move into the directory of your github repo. Now run this command to make new branch

```shell
git checkout -b myBranch
```

Now run ->
```shell
git branch
```

You will get this type of output ->
```shell
* main
 myBranch
```

'\*' symbolizes that which current branch you are on.
To change the branch you can do ->
```shell
git checkout myBranch
```

Now your branch will be changed to myBranch from main.And to check this you can run `git branch` and this should return this ->

```shell
main
* myBranch
```

***

## Pushing the data into the branch

-> Now our branch is made.So now we have to do `git add .` to add the files and `git commit -m "commit description"` . Now we have to push it to the branch named myBranch.
So you can simply run ->
```shell
git push origin myBranch
```
#NOTE This will add the data in the myBranch and this should not be shown as main commit and this will not be registered as contribution.

***

## Pushing data from our branch to main branch

-> Firstly we have to change our branch to main.So we can run `git checkout main`.Now our current branch will be changed to main.Now its time to check that our main branch is updated with the current git files,so we can do `git pull origin main`.Now we have to tell myBranch branch to move its data to main,so you can simply do `git merge myBranch`.
Now do `git push origin main` and your data will be successfully pushed to the main branch.