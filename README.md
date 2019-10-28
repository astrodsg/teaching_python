# Python


## Installing Python

1. Install [homebrew](https://brew.sh/) as a mac tool to manage packages

1. Install python versions

```
brew install python@2
brew install python
```

1. update your PATH variable in start up file. Then open a new terminal (Note this assumes you're using zshrc)

```
echo 'export PATH="/usr/local/opt/python/libexec/bin:/usr/local/bin:$PATH"' >> ~/.zshrc
```

1. confirm which python you

```
which python # should return `/usr/local/opt/python/libexec/bin/python
```

1. Install virtualenvwrapper `pip install virtualenvwrapper`
1. set variable in your startup file. Open a new terminal.

```
echo "export VIRTUALENVWRAPPER_PYTHON=`which python`" >> ~/.zshrc
```

1. Create a default `mkvirtualenv pi`
1. Install packages/modules/libraries using python's package manage `pip`.

```
pip install -r requirements.txt # installs from file
```

1. (bonus) add this to the startup file and it will look for .venv files and auto do the workon

```
check_virtualenv() {
    # Call virtualenvwrapper's "workon" if .venv exists.  This is modified from--
    # http://justinlilly.com/python/virtualenv_wrapper_helper.html
    # which is linked from--
    # http://virtualenvwrapper.readthedocs.org/en/latest/tips.html#automatically-run-workon-when-entering-a-directory
    if [ -e .venv ]; then
        env=`cat .venv`
        if [ "$env" != "${VIRTUAL_ENV##*/}" ]; then
            echo "Found .venv in directory. Calling: workon ${env}"
            workon $env
        fi
    fi
}
venv_cd () { builtin cd "$@" && check_virtualenv }

alias cd="venv_cd"
```


