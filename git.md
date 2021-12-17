To download and install git, you can go to [this link](https://git-scm.com/).

Once you have git installed on your computer, you then need to do a little bit of setup in your terminal  👇

```bash
git config --global user.name "Sebastien Saunier"
git config --global user.email "seb@lewagton.org"
```

This step helps answer the "**Who made the change?**" question that we were talking about in the previous section. When using git, the two lines above will tell your teamates who made a certain edit to the current document/project. Now we can move on to learning our first basic git commands 🎉

## Basic Commands

So first things first, lets create a new folder:

```bash
mkdir new_project # you can change new_project to whatever you want to call your porject. We will call in new_project for the rest of the course
```

The `mkdir` command stands for `make directory` . It is the command for making a new folder on your computer from the terminal. If you want to learn more about terminal commands, click [here](https://dev.to/burningion/introduction-to-the-terminal-ak7)

Now that we have created our new folder, we need to go into it. To do this we need to use the `cd` command which stands for `change directory`. So to change into our `new_project` folder, we run the following:

```bash
cd new_project
```

And finally we need to tell git that we want to track this folder with git. To do that you need to run the command below 👇:

```bash
git init
```

This command creates a hidden folder in the `new_project` folder called `.git`. The `.` in the name is not a typo! It means that it is a hidden folder! You don't need to look in this `.git` folder, you just need to know that as long as it exists, git will track all the changes that happen inside your `new_project` folder!

We developers usually work with a lot of different files and it's hard to keep track of all the files we've touched. Luckily for us, `git` is here to help is. And we can do this with the following command:

```bash
git status
```

This command will show us which files we have touched and will sort these files by different categories. Right now you should see something that looks similar to this👇

<figure style="width: 100%">
  <img alt="Screenshot 2019-11-19 at 12.13.16.png" src="https://wagon-rc3.s3.eu-west-1.amazonaws.com/6CgZTTtpkkQWsRUzUvbqnCCK" />
<figcaption>We have a clean git status, as we havent changed anything yet!
</figcaption>
</figure>

The picture above represents the message that `git` displays when we run `git status`. Let's talk about what is being displayed. First, `git` tells us that on the `master` branch (we will talk about branches in a minute), and we have a clean working tree. This makes sense as we have no files in our project, so nothing has changed! So lets add a new file and add some content 👇

```bash
touch index.html
```

```html
<!-- index.html -->
 <!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    <h1>Welcome to Le Wagon!</h1>
  </body>
</html>
```

Now, lets save that file and run `git status` again. Now you should see somthing like this:

<figure style="width: 100%">
  <img alt="Screenshot 2019-11-19 at 17.33.55.png" src="https://wagon-rc3.s3.eu-west-1.amazonaws.com/gggp9LS1GiGA1gG72HBranCy" />
<figcaption>Now we have some output
</figcaption>
</figure>

Now git is telling us that we have an **Untracked File**. This means that git sees a new file that it doesnt have a record of. So if we want git to track this file we need to **Commit** it. Think of a commit like a snapshot. It's a snapshot of your project at a specific point in time. Committing files in `git` is a 2-step process:
1. We need to tell to `git` which files we want to save. This answers the **"What Changed?"** question. This is done using the `add` command.
2. We need to answer the **"Why it was modified?"** question. This is done using the `commit` command.
Here is how it goes 👇

```bash
git add index.html
git commit --message "created basic html file"
```

In the code above, we asked git to save the file `index.html` and we added a meaningful message to explain what changed. And if you run `git status` again, you should see that it is clean again.

Now lets **edit** our HTML file 👇

```html
<!-- index.html -->
 <!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    <h1>Welcome to Le Wagon's Git & Github workshop!</h1>
  </body>
</html>
```

When you make this change and save, you will see slightly different output!

<figure style="width: 100%">
  <img alt="Screenshot 2019-11-19 at 18.01.27.png" src="https://wagon-rc3.s3.eu-west-1.amazonaws.com/vrApBuWooGPooTcK7Mj8drq3" />
<figcaption>Notice it doesn't say the file is untracked...
</figcaption>
</figure>

Now git is telling us that there are changes in that file that have not been committed. And while running `git status` is great to check which files were modified, we want to be able to do more. We would like to see what exactly changed in each file. Once again, `git` got us covered 😄. With the `diff` command we can see exactly what changed in each file

```bash
git diff
git diff index.html
```

This will show us the exact changes in that file 👇

<figure style="width: 100%">
  <img alt="Screenshot 2019-11-19 at 18.04.29.png" src="https://wagon-rc3.s3.eu-west-1.amazonaws.com/1TCnjVqGquWPXSiafJMWuTCx" />
<figcaption>Note: Git doesn't have the notion of changing a line. We removed the old version, and added a new one!
</figcaption>
</figure>

So now that we can see exactly what changed since our last commit, we need to follow the **2 step process** again for committing a change.

```bash
git add index.html
git commit -m "changed the text of the header on the home page"
```

Finally, after we have made many commits on a project, we may want to see the full history of our project. We can do this with the `log` command.

```bash
git log
```

Which will output 👇

<figure style="width: 100%">
  <img alt="Screenshot 2019-11-19 at 18.11.37.png" src="https://wagon-rc3.s3.eu-west-1.amazonaws.com/cVY4Ld75afoJXYSrV9x9gQjv" />
<figcaption>Each commit is displayed with the Author, the time, and the message of the commit
</figcaption>
</figure>
