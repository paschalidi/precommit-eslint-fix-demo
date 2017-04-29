Small repo to demo an issue I am having with a git pre-commit hook that automatically fixes linting issues via `eslint --fix`.
The pre-commit hook works fine if I stage the changes (e.g. `git add filename`) before commiting,
but fails when committing a file directly (e.g. `git commit -m "Test" filename`).
I don't normally do this, but it seems to be the default behaviour of IntelliJ.

To reproduce the issue:
1. Copy the `pre-commit` file into your git hooks directory `cp pre-commit .git/hooks/.`
1. Remove the semicolon from the last line of `index.js` and save.
1. Run `git commit -m "Test" index.js`.
1. The file is fixed *(semicolon added)* and committed.
1. If I run `git status` the same file is both staged and not staged.
1. If I run `git diff` the staged file is GOOD *(has semicolon)* and the not staged file is BAD *(NO semicolon)*.

The only way I've been able to resolve this issue is by using a post-commit hook to `git reset` the files that were committed.
I'm definitely NOT a Git Guru, so if anyone has experience with this or can help in any way it will be greatly appreciated.

To use the post-commit method:
1. Copy the `post-commit` file into your git hooks directory `cp post-commit .git/hooks/.`
1. Follow steps 2. and 3. from above.
1. Now everything should be as expected.

CREDIT: the pre-commit file was based on a [pre-commit gist](https://gist.github.com/broofa/730fab6ceb1686f4a1fa9977b791b1b5) by @broofa.
