# Python Poetry Buildpack

A [Heroku](https://devcenter.heroku.com/) Buildpack for [Poetry](https://github.com/python-poetry/poetry) users. 

**With pytest integrated**


## How to use

The Python Poetry Buildpack prepares the build to be processed by a Python buildpack such as `heroku/python` by generating `requirements.txt` and `runtime.txt` from `poetry.lock`.

To set up the use of several buildpacks from the Heroku CLI use `buildpacks:add`:

```
heroku buildpacks:clear
heroku buildpacks:add https://github.com/tienhm0202/python-poetry-buildpack.git
heroku buildpacks:add heroku/python
```

Generation of the `runtime.txt` can be skipped by setting `DISABLE_POETRY_CREATE_RUNTIME_FILE` to `1`:

```
heroku config:set DISABLE_POETRY_CREATE_RUNTIME_FILE=1
```

The Poetry version can be specified by setting `POETRY_VERSION` in Heroku config vars. Otherwise it will default to a hard coded version.

```
heroku config:set POETRY_VERSION=1.1.0
```