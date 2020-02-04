# Homebrew's Google Summer of Code
Homebrew is a package manager for macOS and Linux written in Ruby and Bash.

## Application Instructions

In your application tell us:

1. Who you are: your name and how we contact you (e.g. email)
2. What idea are you proposing: which of our ideas is it or describe in detail if it's your own
3. How will you implement it: provide a detailed work timeline that breaks the project into one or two week milestones
4. Why you: link to a previous Homebrew pull request you've submitted (this is a requirement to be accepted)

Homebrew is actively seeking to diversify our contributors and especially welcome applications from women from all backgrounds and people of colour.

### Google Summer of Code
Please read and apply via https://summerofcode.withgoogle.com/get-started/.

## Mentors

Mentorship happens privately on our Homebrew maintainer's Slack and publicly on GitHub pull requests. Each student and project will be assigned a mentor but all students will work with all mentors.

Check out GitHub's blog post on how to run GSoC on GitHub for the standards expected from maintainers and students:
https://github.com/blog/2312-how-to-run-a-google-summer-of-code-project-on-github

## Pass Requirements

- To be accepted one trivial pull request for your project to Homebrew will need to be merged (this can be far prior to the program)
- To pass the mid-term assessment one non-trivial pull request for your project to Homebrew will need to be merged
- To pass the final assessment more than one non-trivial pull request for your project to Homebrew will need to be reviewed and merged

## Technologies Used and Requirements

Homebrew is written mostly in Ruby (with small amounts of Bash), runs on the macOS and Linux operating systems and uses Git and GitHub for version control and updates. You do not need to have used any of these before but must have access to a Mac (unless working on Linux-specific features) and be willing to learn Ruby, Git and GitHub.

## 2020 Ideas
These are suggestions that would make good Google Summer of Code projects. Feel free to open an issue if you wish to discuss or propose your own idea.

### Improve integration with Homebrew Cask
#### Skills Required: Ruby, Homebrew usage, Homebrew Cask usage, usability-focused thinking
#### Mentor: @MikeMcQuaid
#### Difficulty: Easy
Although Homebrew and Homebrew Cask have been merged the two projects are not fully integrated. For example, `brew info` and `brew cask info` are separate commands that produce different output. Ideally all of Homebrew's commands that reference a formula would also be able to reference a cask and produce helpful output (although `brew install` and `brew cask install` should remain separate). This will make it easier for users to have casks recommended when there is not a formula (and vice-versa).

Expected outcome: several new `brew` commands should produce helpful output directing the user to casks or just show cask information.

### Add license metadata to Homebrew/homebrew-core formulae
#### Skills Required: Ruby, Homebrew usage, basic understanding of OSS licensing
#### Mentor: @MikeMcQuaid
#### Difficulty: Medium
Homebrew formulae do not have license metadata. For this to be included in Homebrew a `license` DSL would need to be added to Homebrew/brew and all relevant metadata would need to be added for Homebrew/homebrew-core formulae before they could be merged. Additionally, automated tests in `brew audit` should be added to verify this metadata matches what GitHub detects.

Expected outcome: A formula `license` DSL is added and used in homebrew-core. `brew audit` verifies this DSL is correct.

### Add support for type checking using Sorbet
#### Skills Required: Ruby, Homebrew usage, statically typed programming languages
#### Mentor: @mistydemeo, @issyl0
#### Difficulty: Medium
Homebrew is written in Ruby, which uses dynamic typing. The [Sorbet](https://github.com/sorbet/sorbet) project provides a way to enable static type checking in Ruby, which would increase confidence in the quality of its code and provide a useful way to catch subtle bugs. This project would perform an initial setup of Sorbet for Homebrew and work on adding type data to its code.

Expected outcome: Sorbet is installed in Homebrew's development environment, and key parts of the application have type metadata. Documentation has been written about adding types.

Stretch goal: Major portions of Homebrew's core code has type data.

### Automatically create pull requests based on Homebrew/livecheck
#### Skills Required: Ruby, Homebrew usage, Regex
#### Mentor: @SMillerNL, @MikeMcQuaid
#### Difficulty: Medium
Homebrew/livecheck provides various automated ways of detecting formulae updates. A `livecheck` DSL should be added to formulae and migrated from Homebrew/livecheck and `brew livecheck` use this new data. If time permits, a separate application should be built to make use of these checks, verify that the results seem correct and open a pull request with relevant metadata on Homebrew/homebrew-core.

Expected outcome: A formula `livecheck` DSL is added and used by `brew livecheck` from homebrew-core. If time permits, a seperate application should consume this data.

### Modernize haskell formulae build experience
#### Skills Required: Haskell, Cabal, Stack
#### Mentor: @chenrui333
#### Difficulty: Hard
Historically, Homebrew built packages written in Haskell using Cabal. Over time, this has suffered from reproducibility issues, and [many packages no longer build from source](https://github.com/Homebrew/homebrew-core/issues/48604). This project will improve Homebrew's Haskell formulae build experience by switching to a Stack-based workflow.

Expected outcome: Move to a Stack-based build system for Haskell formulae.
Stretch goal: Help an upstream project to adopt the modern build system.

### Optimise formula and resource download ordering
#### Skills Required: Ruby, Homebrew usage, basic HTTP download knowledge
#### Mentor: @MikeMcQuaid
#### Difficulty: Hard
When `brew upgrade`ing or `brew install`ing multiple formulae with multiple `resource`s the downloads do not happen all at the beginning but are interleaved through the `brew install` process (even with `resource`s within a single formula). This means if a single download fails mid-way through a lengthy build process the user may not notice and have to retry again later. This should be improved so the usability of Homebrew is improved. Similarly, this project could be extended to cover `caveats` and warnings for formulae being output all at the end of multiple `brew install`s for easy reference.

Expected outcome: `brew upgrade` and `brew install` do all their downloads before attempting any installations.

### Use [rbelftools](https://github.com/david942j/rbelftools) and [patchelf.rb](https://github.com/david942j/patchelf.rb) to perform binary relocations in Homebrew on Linux
#### Skills Required: Ruby, Homebrew usage, some knowledge of binary formats
#### Mentor: @woodruffw
#### Difficulty: High

As part of the installation process, Homebrew rewrites its compiled binaries to correctly reference their install prefix and Homebrew-managed dependencies. Homebrew on Linux currently uses the GNU `readelf` and `patchelf` utilities to perform that introspection and relocation on ELF binaries. These tools are buggy and integrate poorly, and can be replaced with the Ruby alternatives linked above. This will reduce the number and difficulty of resolving bugs in ELF relocation, as well as improve Homebrew's performance by reducing both external subprocesses and redundant I/O on ELF binaries.

Expected outcome: A refactoring of Homebrew's Linux-specific `keg` and `keg_relocate` interfaces to use `rbelftools` and `patchelf.rb` instead of shelling out to the GNU utilities.

### Other Ideas
You can also get inspiration from [open `help wanted` issues on Homebrew/brew](https://github.com/homebrew/brew/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22) and [open `help wanted` issues on Homebrew/homebrew-core](https://github.com/homebrew/homebrew-core/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22). Please discuss any of these with us before submission to maximise your chances of being accepted.
