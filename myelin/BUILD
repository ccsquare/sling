package(default_visibility = ["//visibility:public"])

cc_library(
  name = "flow",
  srcs = ["flow.cc"],
  hdrs = ["flow.h"],
  deps = [
    "//base",
    "//file",
    "//string:printf",
  ],
)

cc_library(
  name = "compute",
  srcs = [
    "compute.cc",
    "macro-assembler.cc",
  ],
  hdrs = [
    "compute.h",
    "macro-assembler.h",
  ],
  deps = [
    ":flow",
    "//base",
    "//file",
    "//third_party/jit:assembler",
    "//string:printf",
  ],
)

cc_library(
  name = "profile",
  srcs = ["profile.cc"],
  hdrs = ["profile.h"],
  deps = [
    ":compute",
    "//base",
    "//base:clock",
    "//third_party/jit:cpu",
    "//string:printf",
  ],
)

cc_library(
  name = "graph",
  srcs = ["graph.cc"],
  hdrs = ["graph.h"],
  deps = [
    ":flow",
    "//base",
    "//file",
    "//string:printf",
  ],
)

cc_library(
  name = "multi-process",
  srcs = ["multi-process.cc"],
  hdrs = ["multi-process.h"],
  deps = [
    ":compute",
    "//base",
  ],
)

cc_library(
  name = "express",
  srcs = ["express.cc"],
  hdrs = ["express.h"],
  deps = [
    "//base",
  ],
)

cc_library(
  name = "builder",
  srcs = ["builder.cc"],
  hdrs = ["builder.h"],
  deps = [
    ":flow",
    "//base",
  ],
)

cc_library(
  name = "elf-linker",
  srcs = ["elf-linker.cc"],
  hdrs = ["elf-linker.h"],
  deps = [
    ":compute",
    "//base",
    "//util:elf-writer",
  ],
)

cc_library(
  name = "dictionary",
  srcs = ["dictionary.cc"],
  hdrs = ["dictionary.h"],
  deps = [
    ":flow",
    "//base",
  ],
)

cc_binary(
  name = "analyze",
  srcs = ["analyze.cc"],
  deps = [
    ":compute",
    ":elf-linker",
    ":flow",
    ":graph",
    ":profile",
    "//base",
    "//file:posix",
    "//myelin/cuda:cuda-runtime",
    "//myelin/kernel:cuda",
    "//myelin/kernel:dragnn",
    "//myelin/kernel:tensorflow",
  ],
)

