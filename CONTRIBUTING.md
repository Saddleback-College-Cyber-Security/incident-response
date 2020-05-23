<!-- This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA. -->

# How to contribute

<!-- TODO: this file probably needs to be structured better. and more things added -->

[**Incident Response Home**](./README.md)

## Learning Git

For those who are new to git/github, I *highly* recommend taking a look at [this link](https://learngitbranching.js.org/). It contains a web app for learning git, that starts as simple as making your first commit an progresses all the way to complicated things like merge conflicts and complex branching.

For those looking to skip straight into using git, it can be downloaded and installed [here](https://git-scm.com/downloads). Graphical options for git are available, however most developers opt to use the command line version instead. The tutorial mentioned above uses the command line tool.

## Committing

When adding new documents, please place them in a reasonable location based on their relevancy to the designated directory names.

- All documents require a table of contents. This could be as simple as a [return to Home](./services/graylogs/security/graylogs_modsecurity.md) or as complex as [listing every header in the document](./tools/command_line_nix.md).
- All topics require an entry in the [main Table of Contents](./README.md).
- All topics should have their own branch, so make a new one or move to an existing one for different topics. **Commits directly to master *WILL NOT* be accepted**. This means you'll have to create a pull request for your changes to show on master.

Generally speaking, the name of commits don't have a set structure. Just explaining what the commit does should be enough.

>If a document is getting to the point where is it pretty large feel free to break it up into smaller documents based on topic. Make sure to put them in their own directory and add a `README.md` that contains a table of contents. Use [Graylogs](./services/graylogs/README.md) as an example

## Issues and, Pull Requests

To contribute, unless you are a part of the Saddleback-College-Cyber-Security organization, you will have to fork this repository to make changes. Afterward, just create a pull request and wait for a response. There are some [templates](./.github/TEMPLATES) that have been created for this. Please use and follow them.

---

Thanks, Jacob Still and the Maintainers of Saddleback-College-Cyber-Security
