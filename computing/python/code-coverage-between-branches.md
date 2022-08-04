# Code Coverage Between Branches

If you need to find code coverage between multiple branches, try the following

## Generate the Coverage Report

```bash
pytest --cov --cov-report=xml
```

## Install `diff-cover`

```bash
pip install diff_cover
```

Run `diff-cover` in your CLI, to see that it is installed properly.

**NOTE:** If it doesn't show up for you, try the steps here
[Access PIP Installed CLI Tools](./access_pip_installed_cli_tools.md).

## Determine the Commit on the Branch You want

You'll want to go to the branch you want to compare the current branch with.
So once you find the commit, and assuming that commit is `3a8c6e0`, run 
the following:

```bash
diff-cover ./coverage.xml --compare-branch=3a8c6e0
```

You should see something like this:

```bash
-------------
Diff Coverage
Diff: 3a8c6e0...HEAD, staged and unstaged changes
-------------
my_app/core/utils.py (66.7%): Missing lines 178,180,196,198
my_app/int/utils.py (85.7%): Missing lines 706
my_app/notify/email_utils.py (86.4%): Missing lines 91,114,157,160-161,164,167-168,175
my_app/notify/utils.py (100%)
my_app/api/utils.py (100%)
my_app/runbook/tasks.py (70.0%): Missing lines 710-713,721,728
my_app/runbook/utils.py (100%)
my_app/rest/tasks.py (100%)
my_app/rest/utils.py (100%)
my_app/life/serializers.py (100%)
my_app/life/tasks.py (100%)
my_app/life/utils.py (77.8%): Missing lines 792-793,800-805
my_app/life/views.py (100%)
my_app/web/utils.py (100%)
-------------
Total:   236 lines
Missing: 28 lines
Coverage: 88%
-------------
```