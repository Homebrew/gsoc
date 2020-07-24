# Homebrew's Google Summer of Code
Homebrew is a package manager for macOS and Linux written in Ruby and Bash.

## Application Instructions

In your application tell us:

1. Who you are: your name and how we contact you (e.g. email).
2. What idea are you proposing: the name of the idea you've chosen, or a full description of your own project idea.
3. How will you implement it: provide a detailed work timeline that breaks the project into one or two week milestones.
4. Why you: link to a previous Homebrew pull request you've submitted (this is a requirement to be accepted).

Homebrew is actively seeking to diversify our contributors and especially welcome applications from women from all backgrounds and people of colour.

### Google Summer of Code
Please read and apply via https://summerofcode.withgoogle.com/get-started/.

## Mentors
Mentorship happens privately on our Homebrew maintainers' Slack and publicly on GitHub pull requests. Each student and project will be assigned a mentor but all students will work with all mentors.

Check out GitHub's blog post on how to run GSoC on GitHub for the standards expected from maintainers and students:
https://github.com/blog/2312-how-to-run-a-google-summer-of-code-project-on-github

## Pass Requirements

- To be accepted, one trivial pull request for your project to Homebrew will need to be merged (this can be far prior to the program).
- To pass the mid-term assessment, one non-trivial pull request for your project to Homebrew will need to be merged.
- To pass the final assessment, more than one non-trivial pull request for your project to Homebrew will need to be reviewed and merged.

## Technologies Used and Requirements

Homebrew is written mostly in Ruby (with small amounts of Bash), runs on the macOS and Linux operating systems and uses Git and GitHub for version control and updates. You do not need to have used any of these before but must have access to a Mac (unless working on Linux-specific features) and be willing to learn Ruby, Git and GitHub.

## 2020 Ideas
These are suggestions that would make good Google Summer of Code projects. Feel free to open an issue if you wish to discuss or propose your own idea.

### Improve integration with Homebrew Cask
#### Skills Required: Ruby, Homebrew usage, Homebrew Cask usage, usability-focused thinking
#### Mentor: @MikeMcQuaid, @chenrui333
#### Difficulty: Easy
Although Homebrew and Homebrew Cask have been merged the two projects are not fully integrated. For example, `brew info` and `brew cask info` are separate commands that produce different output. Ideally all of Homebrew's commands that reference a formula would also be able to reference a cask and produce helpful output (although `brew install` and `brew cask install` should remain separate). This will make it easier for users to have casks recommended when there is not a formula (and vice-versa).

Expected outcome: several new `brew` commands should produce helpful output directing the user to casks or just show cask information.

----

### Create more GitHub Actions for Homebrew
#### Skills Required: JavaScript (or another GitHub Actions language), Homebrew usage, GitHub Actions
#### Mentor: @MikeMcQuaid,
#### Difficulty: Medium
Homebrew uses GitHub Actions on (almost) all repositories within the Homebrew organisation (for example: Homebrew/brew, Homebrew/homebrew-bundle, Homebrew/homebrew-aliases). There's a lot of repetition between these that could be improved with dedicated GitHub Actions. Additionally, repeated actions like "run brew style" could have annotations to improve their output.

Expected outcome: More actions are added to the Homebrew/actions repository to support Homebrew or tap workflows.

### Other Ideas
You can also get inspiration from [open `help wanted` issues on Homebrew/brew](https://github.com/homebrew/brew/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22) and [open `help wanted` issues on Homebrew/homebrew-core](https://github.com/homebrew/homebrew-core/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22). Please discuss any of these with us before submission to maximise your chances of being accepted.
