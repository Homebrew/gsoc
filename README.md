# Homebrew's Google Summer of Code
Homebrew is a package manager for macOS written in Ruby.

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
- [@MikeMcQuaid](https://github.com/mikemcquaid) (mike@mikemcquaid.com)
- [@mistydemeo](https://github.com/mistydemeo) (mistydemeo@gmail.com)
- [@ilovezfs](https://github.com/ilovezfs)
- [@JCount](https://github.com/jcount)
- more to follow

Mentorship happens privately on our Homebrew maintainer's Slack and publicly on GitHub pull requests. Each student and project will be assigned a mentor but all students will work with all mentors.

Check out GitHub's blog post on how to run GSoC on GitHub for the standards expected from maintainers and students:
https://github.com/blog/2312-how-to-run-a-google-summer-of-code-project-on-github

## Pass Requirements

- To be accepted one trivial pull request for your project to Homebrew will need to be merged (this can be far prior to the program)
- To pass the mid-term assessment one non-trivial pull request for your project to Homebrew will need to be merged
- To pass the final assessment more than one non-trivial pull request for your project to Homebrew will need to be reviewed and merged

## Technologies Used and Requirements

Homebrew is written mostly in Ruby (with small amounts of Bash), runs on Apple's macOS operating system and uses Git and GitHub for version control and updates. You do not need to have used any of these before but must have access to a Mac and be willing to learn Ruby, Git and GitHub.

## Ideas
These are suggestions that would make good Google Summer of Code projects. Feel free to open an issue if you wish to discuss or propose your own idea.

### Emit warnings for mistyped options (https://github.com/Homebrew/brew/issues/1860)
Currently providing options that don't exist for Homebrew commands silently ignores them. These should instead print a warning to user. This project will involve adding a new DSL for commands in Homebrew/brew to declare what options they accept and migrating all uses of `ARGV.include?` (and potentially all monkeypatching of `ARGV` itself) to this new DSL and abstraction.

### Cache subdirectories for formulae and versions for speedup (https://github.com/Homebrew/brew/issues/568)
The `HOMEBREW_CACHE` should be rearranged to have a `Cellar`-like hierarchy with subdirectories for formulae and then versions, resources and patches. This should be used to speed up `brew cleanup` so that it can be implemented in Bash and run automatically to clean up now
irrelevant files to free up disk space.

### Add support for metaformulae (https://github.com/Homebrew/brew/issues/2300)
Metaformulae would be those that do not install any files themselves but allow `depends_on` multiple formulae (and casks) to support installing a collection of related software. This would involve creating a new DSL that e.g. doesn't need an `install` method and figuring out both the technical solution for depending on Casks and how to configure the interface so e.g. a normal `brew install` does not install X11 unexpectedly.

### Optimise formula and resource download ordering (https://github.com/Homebrew/brew/issues/1666)
When `brew install`ing multiple formulae with multiple `resource`s the downloads do not happen all at the beginning but are interleaved through the `brew install` process (even with `resource`s within a single formula). This means if a single download fails mid-way through a lengthy build process the user may not notice and have to retry again later. This should be improved so the usability of Homebrew is improved. Similarly, this project could be extended to cover `caveats` and warnings for formulae being output all at the end of multiple `brew install`s for easy reference.

### Simplify bottling (binary package creation) for taps (third-party repositories) (https://github.com/Homebrew/brew/issues/3346)
Using free resources on Travis CI or Circle CI and `brew test-bot` it should be possible to create a documented, supported workflow for creating bottles for taps and have them be e.g. uploaded and published within the usual GitHub PR workflow (so only a "Merge pull request" is required by the tap maintainer). This would simplify the process of running a tap as tap maintainers would not need to support building from source (which is more error prone)

### Better support pinning to a major/minor version with Homebrew Bundle and `@`-versioned formulae
Users of Homebrew Bundle may wish to pin to a particular version of a package without knowing about versioned formulae. These formulae should be used automatically when possible. Inspiration can be taken from RubyGems, a `Brewfile.lock` file could be generated and formulae could be automatically copied into a tap where they could remain at the same version until they are manually updated in future.

### Other Ideas
You can also get inspiration from [open `help wanted` issues on Homebrew/brew](https://github.com/homebrew/brew/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22) and [open `help wanted` issues on Homebrew/homebrew-core](https://github.com/homebrew/homebrew-core/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22). Please discuss any of these with us before submission to maximise your chances of being accepted.
