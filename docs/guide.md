# Guide

!!! info "Customize this entry"
    This guide on how to interact with the documentation

## Frequently Asked Questions (FAQ)

* [How can I get access to the documentation?](#access)
* [How is the wiki organized?](#organization_of_the_wiki)
* [How can I edit pages in the wiki?](#edit_wiki_content)
* [How can I make a wiki entry more beautiful?](#make_the_wiki_beautiful)
* [How can I add pictures or other files?](#add_files)
* [How can I contribute ideas?](#contribute_ideas)

## Access

The docmentation website can be accessed [here]({{ config.site_url }}).
It is based on [MkDocs](https://www.mkdocs.org/), a static website generator for project documentation.
The file structure is rather simple:
The [mkdocs.yml](https://git.mpib-berlin.mpg.de/neurocode/wiki/blob/master/mkdocs.yml) file is a file that tells `mkdocs` how to create the website.
All documentation files are collected inside the `/docs` folder.
The documentation is written using [Markdown syntax](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).
Markdown is just a simple way to format text.
There are several ways how you can add content to the wiki or edit existing content which will be explained in detail below.

## Organization of the wiki repo

The wiki is based on [MkDocs](https://www.mkdocs.org/) which according to their website is

> *[...] a fast, simple and downright gorgeous static site generator that's geared towards building project documentation. Documentation source files are written in Markdown, and configured with a single YAML configuration file.*

What does this mean? :thinking: Basically, our wiki is based on a [bunch of documentation files](https://git.mpib-berlin.mpg.de/neurocode/wiki/docs), written in Markdown.
The files are configured in [a YAML configuration file](https://git.mpib-berlin.mpg.de/neurocode/wiki/blob/master/mkdocs.yml).
The webiste is build automatically after every update in the wiki repository using [continuous integration](https://git.mpib-berlin.mpg.de/neurocode/wiki/blob/master/.gitlab-ci.yml).

## Editing

### Via Browser

#### Create a new file

* Go to the [main page of the repository]({{ config.repo_url }}).
* In the center, you will see a list of files and folders: Click on the `/docs` folder.
* At the top, click on the `+` icon and select `New file`.
* Give your entry a file name. Please make sure to use the file extension `.md` for a Markdown file.
* For example, you want to write an entry about Git, so you can call it `git.md` (you need to make sure, of course, that the file name is not already taken).
* Add your content in the main text field. You can (but don't have to!) use [Markdown syntax](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) for basic formatting of your text.
* Done? Click `Commit changes` at the bottom-left to add your file to the documentation.
* The browser will open up a new page where you can inspect your file.
* Still want to make changes? Just click on `Edit` on the top right and commit the changes.

#### Add a new file to the table of contents

You have just created a new file? Great! :clap:
Now, there is one last step to add your file to the documentation:

* Go to the [the repository main page](https://git.mpib-berlin.mpg.de/neurocode/wiki) again.
* Click on the [mkdocs.yml file](https://git.mpib-berlin.mpg.de/neurocode/wiki/blob/master/mkdocs.yml).
* Click on `Edit` on the right.
* Add a new entry to the navigation:

```yaml
nav:
  - Home: index.md
  - Guide: guide.md
  - Git: git.md # your new entry!
```

To keep all our files organized it's a good idea to have subfolders inside the `/docs` directory. When you add a new entry, please decide in which folder your entry belongs: `/admin`, `/it`, `/science`, etc. When you saved your file in the appropriate folder you need to make sure to also specify that folder when you add your entry to the table of contents in the `mkdocs.yml` file.

That's it. Check out the [wiki website](https://neurocode.mpib.berlin/wiki/) to look at your changes!

If you edit the documentation files, the documentation will automatically update (it might take a moment, though)! :boom:

#### Edit an existing file through the browser

You want to update an already existing entry? Here's how to do it:

* You start on [the repository main page](https://git.mpib-berlin.mpg.de/neurocode/wiki).
* In the center, you will see a list of files and folders: Click on the `/docs` folder. You might need to move to a subdirectory where the entry is stored, e.g., the `/admin` folder. Click on the subfolder, e.g., `/admin`
* Again, in the center, you will see a list of files (most of them will have the `.md` Markdown file extension)
* Click on the file that you want to edit. For example, to edit the main page, click on `index.md`
* In the menu bar on the right, click on `Edit`
* Now you can edit the file as needed (again, you may use [Markdown syntax](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) for formatting and / or the formatting options displayed on the top right of the editing window)
* After you applied all changes, make sure to click on `Commit changes` on the bottom left to save your changes
* Done! :tada: :clap:

Shortcut to editing existing files:

* Start on the wiki page you want to edit
* Click on the pencil icon right next to the title
* This will take you to the corresponding markdown document
* Edit and apply changes. Done!

### Via Git

The wiki is essentially a `git` repository.
That means, that - like any other git repo - you can clone it to your nachine, work on it locally, push changes, etc.

* Go to [the wiki repo page](https://git.mpib-berlin.mpg.de/neurocode/wiki)
* Clone the repo to your local machine using `git clone`
* Now you can edit all the files on your local machine directly in your favorite text editor
* Once you changed the content, add your changes (`git add`), commit them (`git commit`) and push them (`git push`) to the remote repo

#### How to work with mkdocs locally

If you want to see how your changes look on the wiki website
without ```git push``` for each change
**there is a way to look at the changing website on the fly**! This can be done
super easily by entering the **following commands** into your command line.

1. Install ```mkdocs``` package on your local machine
     - ```pip install mkdocs```
     - ??? note "**Pro Tip:** Use a virtual environment to install ```mkdocs```"
           Use ```mkvirtualenv -p $(which python3.8) mkdocs``` to create a virtual environment
2. Change directory to (cloned) Neurocode Wiki
     - ```cd path/to/clones/wiki```
     - This path has to be adjusted to where your local cloned wiki repo is located
3. Use ```mkdocs``` to render the wiki webpage on your local machine
     - ```mkdocs serve```
     - ??? note "An example for a full ```mkdocs serve``` print out"
           ```
           lip-osx-003855:wiki koch$ mkdocs serve
           INFO    -  Building documentation...
           INFO    -  Cleaning site directory
           INFO    -  The following pages exist in the docs directory, but are not included in the "nav" configuration:
           - admin/how-to-use-the-wiki.md
           - random/replay.md
           WARNING -  Documentation file 'admin/python-room-hall-of-fame.md' contains a link to '../img/hof-lion.png' which is not found in the documentation files.
           WARNING -  Documentation file 'admin/python-room-hall-of-fame.md' contains a link to '../img/hof-clemens.png' which is not found in the documentation files.
           WARNING -  Documentation file 'admin/python-room-hall-of-fame.md' contains a link to '../img/hof-lena.jpg' which is not found in the documentation files.
           WARNING -  Documentation file 'it/vpn.md' contains a link to 'it/wiki/docs/it/tools/dnf-sha2.pem' which is not found in the documentation files.
           WARNING -  Documentation file 'science/tutorials/svm-tutorial.md' contains a link to '../img/svm-tutorial-01.png' which is not found in the documentation files.
           [I 201217 11:25:01 server:296] Serving on http://127.0.0.1:8000
           [I 201217 11:25:01 handlers:62] Start watching changes
           [I 201217 11:25:01 handlers:64] Start detecting changes
           ```
     - The printed IP address can be copied and pasted into your browser as an web address
          - ```[I 201217 11:25:01 server:296] Serving on http://127.0.0.1:8000```
          - In this case the IP address would be ```http://127.0.0.1:8000/```

Now all saved changes that you make within your repo are shown on that locally rendered website, without you having to push for each change you make! Pretty handy!

## Make the wiki beautiful

### Using the Material theme

Our wiki is based on [MkDocs](https://www.mkdocs.org/) using the [Material theme](https://squidfunk.github.io/mkdocs-material/) including a range of [great extensions](https://squidfunk.github.io/mkdocs-material/extensions/admonition/). Please see the theme documentation for details how to use the extensions.

For example, you can include boxes like this one:

!!! tip "Example Box"
    Hello, I am an example box! :wave: Read more about me [here](https://squidfunk.github.io/mkdocs-material/extensions/admonition/#tip).

## Add files

You want to include pictures or other file?

!!! danger
	Please, do not simply upload large [binary files](https://www.nayuki.io/page/what-are-binary-and-text-files) like `.pdf`, `.xlsx` to the wiki! The wiki is based on `git` which is generally [not good in handling large binary files](https://robinwinslow.uk/2013/06/11/dont-ever-commit-binary-files-to-git/).
	There are other simple solutions available! Please see the options below:

### Option 1: Use `lip-drop` to link to binary files

https://lip-drop.mpib-berlin.mpg.de/

A very simple solution to make larger files available to wiki users is `lip-drop`.
`lip-drop` is a service provided by the MPIB IT department.
You can simply upload a file to `lip-drop` and paste the link into a wiki entry.
Just make sure that you set the expiration setting to `never`!
Also, it might be nice to disable `Randomize filename` so that the file keeps its (hopefully meaninhful) filename, e.g., `phd_regulations.pdf`.

### Option 2: Save pictures in the `/img` folder

Inside the `/docs` folder there is an additional `/img` folder.
This is where you should place images that should appear in your wiki entry.

Please follow the [instructions on the MkDocs website](https://www.mkdocs.org/user-guide/writing-your-docs/#linking-to-images-and-media) how to link images to the documentation.

Importantly, please **make sure that the image files are as small as possible** so they don't make the Wiki repo too big! Thanks!

### Option 3: Include images from web links

When you want to include images in your Markdown file, it's also possible to **fetch them directly from any web link**.
See [this Markdown cheatsheet for instructions](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images).

So if you want to include an image **think about whether you can get this image from a webaddress directly rather than downloading the file and adding it to the `/img` folder**. That way, we can again ensure that repo does not become too big and cluttered with files. Thanks!

## Contribute ideas

### Overview: Is there an `issue`?

* Do you feel that there is **information still missing** in the documentation?
* Do you have ideas how the **wiki could be further improved**?

**Please share your ideas with everyone else!**

We exchange ideas about the wiki through the [project's GitLab issues board](https://git.mpib-berlin.mpg.de/neurocode/wiki/issues).
Please read about issues in the [GitLab documentation](https://docs.gitlab.com/ee/user/project/issues/).
In short, you can think about GitLab issues as a chat platform for excchanging ideas related to a specific project.
One of the main advantages of Issues is that all ideas and related dicussions are close to the actual content.
That way, not only the content itself but also related ideas can be documented in a transparent, open way.

### Creating an new issue

You have a new idea for the wiki? There is information missing? There is a bug with the website?
You don't have time to fix it yourself, need help or just want to set a reminder?

Just create a new issue!

* Go to the [project's issue board](https://git.mpib-berlin.mpg.de/neurocode/wiki/issues)
* Browse the list of existing issues to check if someone already had a similar idea. Maybe you can just comment on a previous issue?
* If you want to create a new issue, click on the green `New issue` button on the upper right-hand side
* Give your issue a title that nicely summarizes what your idea is about
* Give more information by filling in the details of your idea in the `Description` window
* Optionally, you can assign the issue to someone, by selecting from the `Assignee` list. You can also assign the issue to yourself if you want to work on the issue yourself.
* Optionally, you can set [a milestone](https://docs.gitlab.com/ee/user/project/milestones/). Milestones are broader goals that should be achieved in the project in a certain time period.
* Optionally, you can asssign a set of [labels](https://docs.gitlab.com/ee/user/project/milestones/) to the project. Labels allow you to categorize the issue. For example, your issue could related to a bug in the project (e.g., something is broken) that requires immediate attention or it could be an idea for a small enhancement that has lower priority.
* Optionally, you can set a due date but most of the time, there is really no rush, right?

### Fixing issues

* Go to the [project's issue board](https://git.mpib-berlin.mpg.de/neurocode/wiki/issues)
* Browse the list of open issues on the issue board.
* Just want to add your two cents to an existing issue? Feel free to comment in the issue diretly!
* Once you implemented changes you can also close the open issue to indicate that the issue has been resolved.
