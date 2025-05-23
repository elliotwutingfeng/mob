# 5.4.0
- Feature: Add shortcut for `mob start --create` as `mob start -c`.

Thanks to @TimsDevCorner for your contributions!

# 5.3.3
- Fix: `mob start` now functions correctly on WIP branches when the base branch is not checked out, applicable to branch names that do not contain a `-` character.

# 5.3.2
- Fix: Removed wrong warning about diverging wip branch when joining a new session

# 5.3.1
- Fix: Added documentation for `mob start --discard-uncommitted-changes` in the `mob help` command

# 5.3.0
- Feature: `mob start --discard-uncommitted-changes` allows to discard uncommitted changes and then starting a new mob session

Thank you @stefanscheidt for this feature request

# 5.2.0
- Feature: `mob done` now pulls when someone else already did `done`

# 5.1.1
- Fix: `mob break 5` is now correctly parsed

# 5.1.0
- Feature: Adds new flag `--join` for `mob start` to join an existing session
  `mob start --join` (#437)

# 5.0.1
- Fix: The configuration option `MOB_SKIP_CI_PUSH_OPTION_ENABLED` now works correctly

Thank you @stefanscheidt for reporting this issue

# 5.0.0
- Feature: You can now set goals
- Feature: Can make use of the git push-option "ci.skip"
- Removed: `mob start` does not create an emtpy commit on a new wip branch anymore
- Feature: Prints git commands before they are finished for faster feedback
- Feature: Added cli option `--room` to set the room name of timer.mob.sh once
- Feature: `mob status` shows a hint if there is no remote branch
- Feature: `mob status` shows the duration of wip branches
- Fix: `mob done --squash-wip` now squashes the start commit as well
- Fix: Fixes a bug with timers smaller than 1
- Windows Performance is improved due to use of `os.UserHomeDir()`
- Upgrade to go 1.22

Thank you @schmonz for fixing the build on non-Linux Unix systems
Thank you @jmbockhorst for improving windows performance
Thank you @michael-mader for improving our readme

# 4.5.0
- Removes feature which cancels running timers as this can lead to longer rotations if the codebase is switched. The way it was implemented is also not ideal for virus detection.
- Correct typo in the hint for creating a remote branch 

Thank you @clemlatz for finding and fixing the typo
Thank you @stefanscheidt for updating the readme on the build and install from source instructions

# 4.4.6

- Fix: Able to open last modified file with space in path
- Fix: `start` ignores git hooks
- Removes deprecated io/ioutil
- Improves uninstallation instructions

Thanks to @dkbnz for improving the uninstallation instructions
Thank you @testwill for removing the deprecated ioutil
Thank you @kriber82 for allowing filenames with spaces

# 4.4.5
- Fix: version

# 4.4.4
- Fix: missing SHA in Arch PKGBUILD
- Fix: missing glibc on older linux version

# 4.4.3
- Fix: mob.sh now specifies the remote ref when pushing to allow for custom `git config push.default` settings such as `tracking`
- Fix: Improves the suggested command when you have uncommitted changes on an attempt to open a custom wip branch using `mob start -b green`
- mob.sh now uses the go version 1.20.x

Thanks to @jstoneham for fixing the bug with using a custom `push.default` setting!
Thank you @tobiasehlert for fixing our GitHub Action workflows post-31st May 2023!

# 4.4.2
- Fix: `mob config`, `mob help`, `mob moo` and `mob version` are now working outside of git repositories again
- Fix: `mob clean` now works correctly

Thanks to @danilo-bc and @jrdodds for reporting these bugs!

# 4.4.1
- Fix: mob.sh now works correctly if git option `status.branch` is set to `true`

# 4.4.0
- Feature: `mob timer open` opens the timer website in your default web browser. If you specified `MOB_TIMER_ROOM` it will automatically open the specific timer page.
- Feature: mob.sh is now built as a mac universal app and therefore supports Apple Silicon natively. 

# 4.3.1
- Fix: `mob done` will now print the command `git merge --squash --ff mob/main` just once and not twice.

# 4.3.0
- Feature: Adds `MOB_START_COMMIT_MESSAGE` config property for changing the commit message on `mob start` empty commit introduced in 4.2.0. This should help overcome problems with pre-receive git hooks.

# 4.2.0
- Feature: mob.sh now starts a mob session with an empty commit to skip CI when creating a new remote branch for the session. The commit is squashed or dropped when `mob done` except for `--no-squash` option.

# 4.1.2
- Fix: `mob done --squash-wip` won't lose changes when you forget to `mob start`

# 4.1.1
- Fix: mob showed the wrong executable name in windows
- Feature: mob.sh now makes use of `--push-option=ci.skip` when pushing
- Feature: mob.sh now warns you when your git version is too old

Thanks to @balintf and @muskacirca for your contributions!

# 4.0.0
- **NEW** Feature: `mob reset` doesn't reset the mob branch anymore. It now warns you that it deletes the mob branch for everyone and if you want to continue do `mob reset --delete-remote-wip-branch`.
- **NEW** Feature: `mob timer`, `mob break`, `mob start`, `mob next` and `mob done` will stop already running local timers.
- Feature: `mob start --create` will create the remote branch and start the mob session on that branch.
- Feature: mob.sh now also works with tools like `git-repo` which symlink the `.git` folder
- Removed `MOB_START_INCLUDE_UNCOMMITTED_CHANGES` environment variable (has been deprecated for some time).
- `MOB_DONE_SQUASH` no longer supports a boolean value, you have to use the proper values `squash`, `no-squash` or `squash-wip` instead.

Thanks to @rustiever, @gulio-python, @freekk, and @sebsprenger for your contributions!

# 3.2.0
- Fix: `mob done --squash-wip` won't fail if a previously committed file has uncommitted modifications.
- Feature: `MOB_TIMER_INSECURE=true` allows enterprises to use the timer.mob.sh companion service despite SSL issues.

Thanks to @gregorriegler and @JanMeier1337 for your contributions!

# 3.1.5
- Add a more specific error message if `git` is not installed.
- Allow for using `mob timer` outside of git repositories.
- Fix: `mob done --squash-wip` now successfully auto-merges auto-mergeable diverging changes.
- Print the help output whenever any kind of help argument (`help`, `--help`, `-h`) is present in the command, e.g. `mob s 10 -h`.
- Adds a warning to `mob start` in case the wip branch diverges from the main branch.
- Various fixes in suggestion of next typist:
  - Show list of last committers only if there are any.
  - Skip suggestions if there has only been a single person so far.
  - Consider the case of a new typist joining the session.
  - Fix reporting on first commit.
- Show a deprecation warning when MOB_DONE_SQUASH is set to `true` or `false` in the environment variable or in the .mob configuration file.

# 3.1.4
- Fixes a bug where mob saves the wrong filepath of the last modfied file in the wip commit message.

# 3.1.3
Just a version bump.

# 3.1.2
- Fixes a bug where mob hides output of interactive git hooks when `MOB_GIT_HOOKS_ENABLED=true`. And without output, the user doesn't know what to input. And without input, mob waits indefinitely.

# 3.1.1
- Fixes a bug where `mob clean` failed to delete an orphaned wip branch because of unmerged commits.
 
Thanks to @jdrst for making this release possible!

# 3.1.0
- Add `mob clean` command that removes orphan wip branches that might be a left over of someone else doing a `mob done`. This is especially helpful when using a lot of feature branches. If you call `mob clean` on an orphan wip branch, it will switch you to the base branch, falling back to main/master if the base branch does not exist.
- The values `squash`, `no-squash` and `squash-wip` for MOB_DONE_SQUASH can be set not only via env var, but now in the .mob configuration file as well.

Thanks to @hollesse and @thmuch making this release possible!

# 3.0.0
- **NEW** Mob will automatically open the last modified file of the previous typist in your preferred IDE. Therefore, you need to set the configuration option `MOB_OPEN_COMMAND` to a command which opens your IDE. For example, the open command for IntelliJ is `idea %s`
- Add a Smiley face to Happy Collaborating message to make your day :)

Thanks to @hollesse and @aryanfaghihi making this release possible!

# 2.6.0
- **NEW** Allow keeping manual commits while squashing all wip commits by finishing a mob-session with `mob done --squash-wip`.
- Removed experimental command `mob squash-wip` in favor of new `mob done --squash-wip`.  
- Added missing configuration option `MOB_WIP_BRANCH_PREFIX` for `.mob` file.

Thanks to @gregorriegler and @hollesse making this release possible!

# 2.5.0
- Enable git hooks with `MOB_GIT_HOOKS_ENABLED=true`. By default, this option is false and no git hooks such as `pre-commit` or `pre-push` are triggered via mob itself.

# 2.4.0
- As an alternative to the environment variables, you can configure the mob tool with a `.mob` file in your home directory. For an example have a look at `mob-configuration-example` file. 
- As an alternative to the environment variables, you can configure the mob tool with a `.mob` file in your git project root directory. The configuration options `MOB_VOICE_COMMAND`, `MOB_VOICE_MESSAGE`, `MOB_NOTIFY_COMMAND`, and `MOB_NOTIFY_MESSAGE` are disabled for the project specific configuration to prevent bash injection attacks.
Thanks to @vrpntngr & @hollesse making this release possible as part of the @INNOQ Hands-On Event, February 2022.

# 2.3.0
- With `export MOB_TIMER_ROOM_USE_WIP_BRANCH_QUALIFIER=true` the room name is automatically derived from the value you passed in via the `mob start --branch <branch>` parameter.

# 2.2.0
- When mob encounters unpushed commits in the base branch, the tool now provides help for the user to fix this immediately.
- Improves console output when using `mob break 5` in combination with https://timer.mob.sh
- Gives the user the chance to name their final commit after `mob done --no-squash`

# 2.1.0
- When having set `MOB_TIMER_ROOM` the local timer keeps on working. To disable the local timer altogether, please disable it via `export MOB_TIMER_LOCAL=false`.
- Improved message when nothing to commit (Thanks to @seanpoulter for https://github.com/remotemobprogramming/mob/pull/202)

# 2.0.0
- **NEW** create a team room on https://timer.mob.sh to have a team timer. Set `MOB_TIMER_ROOM` to the name of your team room and mob will automatically send timer requests to your team room. Mob now even supports breaks with `mob break <minutes>`. 

# 1.12.0
- If you renamed the executable or use a symlink to use a different name, `mob` will detect the new name and use that in its console output.
- Improves error handling when using `mob start -i`. When the working directory is a subdirectory that would be removed due to `git stash` the mob tool will tell the user about this and aborts with an error. 

# 1.11.1
- Fixes a bug which let `mob version` fail when run outside of a git repository.

# 1.11.0
- Allow to override the text in the notification and the voice via environment variables `MOB_NOTIFY_MESSAGE` and `MOB_VOICE_MESSAGE`.
- Allow to override the stash name used for stashing uncommitted changes via the environment variable `MOB_STASH_NAME`.
- Allow to override the cli name of the tool via `MOB_CLI_NAME` so you can use `pair`, `ensemble`, `team`, or whatever you like best, instead of `mob`. Just install the `mob` tool, set an alias in your cli and set the environment variable `MOB_CLI_NAME` to the name of your alias.

# 1.10.0
- Print current time after mob start. This helps when scrolling through the terminal to distinguish the mob start calls.

# 1.9.0
- Show commit hash of WIP commits made by the `mob` tool on the console.
- `mob start --include-uncommitted-changes` now fails fast. That means, if `mob` can detect any issue preventing it to succeed, it will exit BEFORE calling `git stash`. This will make error recovery much easier as one doesn't have to think about applying any stashes by themselves. 

# 1.8.0
- `mob next` does not show the same committer multiple times in the list of previous committers.
- `mob next` does not suggest the current Git user to be the next typist as long as there were other persons involved in the mob.
- `mob next` performs a simple lookahead to also suggest persons who might have been absent only during the last mob round.
- When user.name is not set in the git config, mob no longer shows an error but a warning with a help how to fix it.

# 1.7.0
- Allows creating parallel mob sessions on the same repository more easily.
- `mob branch` shows all remote mob branches currently available.
- `mob fetch` fetches the remote state, so you have everything up to date locally. Helpful to combine with `mob status` and `mob branch` who don't fetch by themselves.

# 1.6.0
- When `mob start` fails, the timer no longer starts to run.

# 1.5.0
- Less noisy output: Only show number of unpushed commits in output if there are more than 0.
- Add experimental command `mob squash-wip` to squash any WIP commits in the wip branch into a following manual commit using `git rebase --interactive` with `mob` as the temporary `GIT_EDITOR`.
- The order of the latest commit is now reversed, the latest one is shown last.
- Add experimental configuration option `MOB_WIP_BRANCH_PREFIX` to configure the `mob/` prefix to some other value. 

# 1.4.0
- The list of commits included in a mob branch is now truncated to a maximum of 5 entries to prevent the need for scrolling up in order to see the latest included changes.
- Show more informative error message when `mob <cmd>` is run outside of a git repository.
- Add environment variable MOB_TIMER which allows setting a default timer duration for `mob start` and `mob timer` commands.
- Add automatic co-author attribution. Mob will collect all committers from a WIP branch and add them as co-authors in the final WIP commit.
- added support for preventing `mob start` if there are unpushed commits
- better output if one passes a negative number for the timer

# 1.3.0
- The default `MOB_COMMIT_MESSAGE` now includes `[ci skip]` and `[skip ci]` so that all the typical CI systems (including Azure DevOps) will skip this commit.
- Add `--squash` option to `mob done` that corresponds to `--no-squash`.
- Fixes the default text to speech command on linux and osx.
- Removed `MOB_DEBUG` environment variable (has been deprecated for some time).

# 1.2.0
- Add environment variable `MOB_REQUIRE_COMMIT_MESSAGE` which you could set to true to require a commit message other than the default one.
- Fixes a bug where you could not run `mob start --branch feature-1` because feature-1 contained a dash.
- Fixes a bug which prevented the sound output of 'mob next' and 'moo' on windows

# 1.1.0
- Add optional `--no-squash` for `mob done` to keep commits from wip branch.
- Add environment variable `MOB_DONE_SQUASH` to configure the `mob done` behaviour. `MOB_DONE_SQUASH=false` is equal to passing flag `--no-squash`.
- Special thanks to @jbrains, @koeberlue, @gregor_riegler for making this release happen, obviously, in a remote mob session.

# 1.0.0
- BREAKING: `MOB_WIP_BRANCH_QUALIFIER_SEPARATOR` now defaults to '-'.
- BREAKING: `MOB_NEXT_STAY` now defaults to 'true'.
- Proposed cli commands like `mob start --include-uncommitted-changes` are now shown on a separate line to allow double clicking to copy in the terminal.

# 0.0.27
- Add way to configure `MOB_WIP_BRANCH_QUALIFIER` via an environment variable instead of `--branch` parameter. Helpful if multiple teams work on the same repository.
- Add way to configure `MOB_WIP_BRANCH_QUALIFIER_SEPARATOR` via an environment variable. Defaults to '/'. Will change to '-' in future versions to prevent branch naming conflicts (one cannot have a branch named `mob/main` and a branch named `mob/main/green` because `mob/main` cannot be a file and a directory at the same time).

# 0.0.26
- Adds way to configure the voice command via the environment variable `MOB_VOICE_COMMAND`.
- Allow disabling voice or notification by setting the environment variables `MOB_VOICE_COMMAND` or `MOB_NOTIFY_COMMAND` to an empty string.
- Fixes a bug where a failure in executing the voice command would lead to omitting the notification.
- `mob config` now shows the currently used `MOB_VOICE_COMMAND` and `MOB_NOTIFY_COMMAND`.
- Add `mob next --message "custom commit message"` as an option to override the commit message during `mob next`.

# 0.0.25
- Adds flag `--return-to-base-branch` (with shorthand `-r`) to return to base branch on `mob next`. Because 'mob' will change the default behavior from returning to the base branch to staying on the wip branch on `mob next`, this flag provides the inverse operation of `--stay`. If both are provided, the latter one wins.
- Adds flag `-i` as a shorthand notation for `--include-uncommitted-changes`.
- Fixes a bug that prevented `mob start` to work when on an outdated the WIP branch 
- `mob next` push if there are commits but no changes.

# 0.0.24
- Fixes a bug where mob couldn't handle branch names with the '/' character 

# 0.0.23
- Commit message of wip commits is no longer quoted (see #52)

# 0.0.22
- Adds `mob start --branch <branch>` to allow multiple wip branches in the form of 'mob/<base-branch>/<branch>' for a base branch. For example, when being on branch 'main' a `mob start --branch green` would switch to a wip branch named 'mob/main/green'.
- Adds `mob moo` (Thanks Niko for the idea)
- Deprecated `MOB_DEBUG` in favor of the parameter `--debug`
- Deprecated `MOB_START_INCLUDE_UNCOMMITTED_CHANGES` in favor of the parameter `--include-uncommitted-changes` instead
- Show warning if removed configuration option `MOB_BASE_BRANCH` or `MOB_WIP_BRANCH` is used.

# 0.0.20
- `mob start` on a branch named `feature1` will switch to the branch `mob/feature1` and will merge the changes back to `feature1` after `mob done`. For the `master` branch, the `mob-session` branch will still work (but this may change in the future, switching to `mob/master` at some point).
- Removes configuration options for base branch and wip branch. These are no longer necessary.
- `mob status` added. Thanks to Jeff Langr for that contribution! 

# 0.0.19
- Removes zoom screen share integration.
- Less git commands necessary for 'mob start'
- Mob automatically provides sound output on windows without any installation

# 0.0.18
- Fixes a bug where boolean environment variables such as `MOB_NEXT_STAY` set to any value (including empty value) falsely activated their respective option.
- Simplified `mob start` when joining a mob session. It uses `git checkout -B mob-session origin/mob-session` to override any local `mob-session` in the process. It reduces the amount of commands necessary and makes the mob tool more predictable: the `origin/mob-session` always contains the truth.
- Removes `mob share` command. You can still enable the zoom integration via `mob start 10 share` although this is now DEPRECATED and will eventually be removed in the future.

# 0.0.16
- `mob start` prints out untracked files as well 
- `mob start --include-uncommitted-changes` now includes untracked files in the stash 'n' pop as well 
- keying in an unknown command like `mob conf` will internally call `mob help` to print out the usage options instead of calling `mob status`
- fixed a bug where overriding `MOB_START_INCLUDE_UNCOMMITTED_CHANGES` via an environment variable could print out a wrong value (didn't affect any logic, just wrong console output)

# 0.0.15
- Any `git push` command now uses the `--no-verify` flag

# 0.0.14
- New homepage available at https://mob.sh
- `mob config` prints configuration using the environment variable names which allow overriding the values

# 0.0.13
- Fixes bug that prevented users wih git versions below 2.21 to be able to use 'mob'.
