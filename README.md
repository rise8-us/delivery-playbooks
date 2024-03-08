# Rise8 Delivery Playbooks

## Contribute

### Find the Content

All delivery playbook content are located [here](docs/content/).

### Add New Content

All the content is written in markdown, here's a [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) to help you navigate the syntax.

Create a new file by clicking the 'add file' button on the Github UI. Name the file, add the content, and then click the 'Commit Changes' button. Create a new branch and make a name for it that describes what you're adding (e.g. test-driven-development-play) - this will create a pull request. After creating the pull request, have at least one teammate review it before it is merged.

When the pull request is merged, a process will be triggered that will push the new changes onto the site.

### Modify Existing Content

In order to modify existing content, click on the file you want to change and select the button with a pencil icon. You can make all the necessary edits and then follow the same process as the [add new content section](#add-new-content) in order to create and merge a pull request.

### Test Changes Locally

Before you make a pull request and merge your changes, you may want to view the website with your changes on your local computer. If that's the case you'll need to do the following steps in your terminal:

> Before you do any of the following steps, you need to connect your local computer to your Github account. Follow [these instructions](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git) in order to get that done.

```shell
# install
brew install mkdocs
brew install mkdocs-material
# clone the repository
git clone https://github.com/rise8-us/delivery-playbooks.git
cd deliver-playbooks
# run dev server
mkdocs serve
```

## More Information

[Kanban Board Link](https://github.com/orgs/rise8-us/projects/19)

[Delivery Playbook Slack Channel](https://rise8.enterprise.slack.com/archives/C067QLN18JF)

[Playbook FigJam](https://www.figma.com/file/sDkxzbFYqEkv8NCRjcBLqr/Rise-8-Practice-Guides?type=whiteboard&node-id=0%3A1&t=3tZyk6zd03LC9S8Z-1)
