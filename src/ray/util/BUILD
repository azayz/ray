load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library", "cc_proto_library", "cc_test")
load("//bazel:ray.bzl", "COPTS")

cc_library(
    name = "util",
    srcs = glob(
        [
            "*.cc",
        ],
        exclude = [
            "*_test.cc",
        ],
    ),
    hdrs = glob([
        "*.h",
    ]),
    copts = COPTS,
    linkopts = select({
        "@platforms//os:windows": [],
        "//conditions:default": ["-lpthread"],
    }),
    strip_include_prefix = "//src",
    visibility = ["//visibility:public"],
    deps = [
        ":thread_checker",
        "//:aligned_alloc",
        "//:sha256",
        "//src/ray/protobuf:event_cc_proto",
        "//src/ray/protobuf:export_event_cc_proto",
        "@boost//:asio",
        "@com_github_spdlog//:spdlog",
        "@com_google_absl//absl/container:flat_hash_map",
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/debugging:failure_signal_handler",
        "@com_google_absl//absl/debugging:stacktrace",
        "@com_google_absl//absl/debugging:symbolize",
        "@com_google_absl//absl/random",
        "@com_google_absl//absl/synchronization",
        "@com_google_absl//absl/time",
        "@com_google_googletest//:gtest_main",
        "@com_google_protobuf//:protobuf",
        "@nlohmann_json",
    ],
)

cc_library(
    name = "thread_checker",
    hdrs = ["thread_checker.h"],
    srcs = ["thread_checker.cc"],
    visibility = ["//visibility:public"],
)
