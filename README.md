Small repo to demo an issue with IntelliJ and [lint-staged](https://github.com/okonet/lint-staged) when using the auto-fix functionality.

To reproduce the issue:
1. Remove the semicolon from the last line of [index.js](https://github.com/samit4me/lint-staged-demo/blob/96c9789093b616aec82fc0f6f37cb2773fa6792a/index.js#L11) and save.
1. Run `git commit -m "Test" index.js`.
1. The file is fixed *(semicolon added)* and committed.
1. If I run `git status` the same file is both staged and not staged.
1. If I run `git diff` the staged file is GOOD *(has semicolon)* and the not staged file is BAD *(NO semicolon)*.

These staged and not staged files can be cleaned up via `git reset` and maybe that could be added as a "postcommit" using [husky](https://github.com/typicode/husky) but I'm not sure if this is a good idea and I'm definitely NOT a Git Guru, so if anyone has experience with this or can help in any way it will be greatly appreciated.