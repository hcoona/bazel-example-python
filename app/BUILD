package(default_visibility = ["//visibility:public"])

load(
  "@io_bazel_rules_python//python:python.bzl",
  "py_binary"
)

py_binary(
    name="my_app",
    srcs=["my_app.py"],
    deps=["//lib:my_lib"]
)