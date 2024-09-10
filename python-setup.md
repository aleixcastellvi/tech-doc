# Python and Alias Setup Guide

By default, macOS comes with Python and pip pre-installed, but it's often necessary to install newer versions and follow these configuration steps.

First, ensure Python 3 is installed:

```bash
which python3
```

This should return something like:

```
/usr/local/bin/python3
```

This is the full path where Python 3 is installed.

You can also check the installed version with:

```bash
python3 --version
```

If Python 3 is installed, you can create aliases to use python and pip instead of python3 and pip3. Follow these steps:

**Step 1: Check default shell**

```bash
echo $SHELL
```

- If it returns /bin/bash, you’re using Bash.
- If it returns /bin/zsh, you’re using Zsh.

**Step 2: Configuration**

a) <u>If using Zsh</u>

Edit your Zsh config file:

```bash
nano ~/.zshrc
```

Add the following:

```
export PATH="/usr/local/bin:$PATH"  # Adjust path if needed
alias python="python3"
alias pip="pip3"
```

Apply the changes:

```bash
source ~/.zshrc
```

b) <u>If using Bash</u>

Edit your Bash profile:

```bash
nano ~/.bash_profile
```

Add the following:

```
export PATH="/usr/local/bin:$PATH"  # Adjust path if needed
alias python="python3"
alias pip="pip3"
```

Apply the changes:

```bash
source ~/.bash_profile
```

**Step 3. Verify**

Check that the aliases work:

```bash
python --version
pip --version
```

With this configuration, the python and pip commands will point to python3 and pip3 installed on your system.
