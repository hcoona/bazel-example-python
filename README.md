# Bazel Python Project Example #

This is an example Python project build with bazel to pack the dependencies into distribution package.

Bazel is a build system maintained by Google, see [bazel](https://docs.bazel.build/versions/master/bazel-overview.html) for more details.

## Why we need it ##

We are still using system builtin Python. Sometimes we need to install some Python packages through pip to support our project. However, we cannot install them without root privilege.

There basically are 2 approaches:

1. Pack all dependencies into a Docker image & run your project in Docker
1. Pack all dependencies & publish them together with your project, load them with PYTHONPATH environment to avoid interference with other projects.

The Bazel build system could help with the second approach.

## How this project work ##

This project is a simple example. It's consist of a main entry subproject --- `app`, and a library subproject `lib`. In the real word case, you might need more libs projects or external projects. For the external projects, please check the bazel document.

The `app` project import the `lib` project. The `lib` project import several pip packages notes in `lib/requirements.txt` & `lib/BUILD`.

## How to publish the build output ##

```
tar -czf project.tar.gz -C bazel-bin/main
```

or

```
rsync -rL bazel-bin/main /path/to/
```
