licenses(["notice"])  # 3-Clause BSD

exports_files(["license.txt"])

load("@org_tensorflow//third_party/ngraph:build_defs.bzl", "debug_print")

genrule(
    name = "genrule_test",
    srcs = [
        "include/clang/Basic/Version.inc.in",  # a filegroup with multiple files in it ==> $(locations)
        #"//other:gen",   # a genrule with a single output ==> $(location)
    ] + debug_print( "$(location include/clang/Basic/Version.inc.in) genrule_test"),
    outs = ["processed.h"],
    #cmd = "cat $(locations //some:files) $(location //other:gen) > $@",
    cmd = "echo $(location include/clang/Basic/Version.inc.in)",
    output_to_bindir = 1
)

genrule(
  name = 'hello',
  outs = ['hello.txt'],
  cmd = 'echo hello > $(location hello.txt)'
)

filegroup(
    name = "LICENSE",
    srcs = [
        "license.txt",
    ],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "clang_genrule_test",
    srcs = glob([
        "lib/Basic/Module.cpp"
    ] + debug_print("Hellllllloooooooo") ),
    hdrs = [],
    copts = [
        "-I external/ngraph_clang_archive/include",
    ],
    deps = [
       "@llvm//:core",
       "@llvm//:support",
       "@llvm//:transform_utils",
    ],
    visibility = ["//visibility:public"],
    alwayslink=1
)

cc_library(
    name = "clang_basic",
    srcs = glob([
        "lib/Basic/*.cpp",
        "lib/Basic/*.def",
        "processed.h"
    ]),
    hdrs = glob([
        "include/clang/Basic/*.h",
    ]),
    copts = [
        "-I external/ngraph_clang_archive/include",
    ],
    deps = [
       "@llvm//:core",
       "@llvm//:support",
       "@llvm//:transform_utils",
    ],
    visibility = ["//visibility:public"],
    alwayslink=1
)

