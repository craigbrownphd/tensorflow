licenses(["notice"])  # 3-Clause BSD

exports_files(["license.txt"])

filegroup(
    name = "LICENSE",
    srcs = [
        "license.txt",
    ],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "clang_lib",
    # hdrs = glob([
    #     "include/nlohmann/**/*.hpp",
    # ]),
    copts = [
        "-I ",
    ],
    deps = [
       "@llvm",
    ],
    visibility = ["//visibility:public"],
    alwayslink=1
)
