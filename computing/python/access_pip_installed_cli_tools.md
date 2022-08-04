# Access pip-installed CLI Tools

If you're running `pip install` and installing a CLI tool, and you're not able
to find the tool, like shown below:

```bash
$ pip install diff-cover
Defaulting to user installation because normal site-packages is not writeable
Collecting diff-cover
  Downloading diff_cover-6.5.1-py3-none-any.whl (49 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 49.5/49.5 kB 802.7 kB/s eta 0:00:00
...
Successfully installed Jinja2-3.1.2 MarkupSafe-2.1.1 Pygments-2.12.0 chardet-5.0.0 diff-cover-6.5.1 pluggy-1.0.0

$ which diff-cover
diff-cover not found

```

Then do this:

```bash
echo "export PATH=\"`python3 -m site --user-base`/bin:\$PATH\"" >> ~/.bashrc
source ~/.bashrc
```

This will add your path to the `bin` directory of your default Python 
interpretter (in this case `python3`), and you should be able to find your 
installed CLI tool.