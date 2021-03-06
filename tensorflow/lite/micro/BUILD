load(
    "//tensorflow/lite/micro/testing:micro_test.bzl",
    "tflite_micro_cc_test",
)
load(
    "//tensorflow/lite/micro:build_def.bzl",
    "cc_library",
    "micro_copts",
)

package(
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],  # Apache 2.0
)

cc_library(
    name = "micro_compatibility",
    hdrs = [
        "compatibility.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
)

cc_library(
    name = "micro_framework",
    srcs = [
        "memory_helpers.cc",
        "micro_allocator.cc",
        "micro_interpreter.cc",
        "micro_optional_debug_tools.cc",
        "simple_memory_allocator.cc",
        "test_helpers.cc",
    ],
    hdrs = [
        "memory_helpers.h",
        "micro_allocator.h",
        "micro_interpreter.h",
        "micro_mutable_op_resolver.h",
        "micro_op_resolver.h",
        "micro_optional_debug_tools.h",
        "simple_memory_allocator.h",
        "test_helpers.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = [
        ":micro_compatibility",
        ":micro_utils",
        "//tensorflow/lite:type_to_tflitetype",
        "//tensorflow/lite/c:common",
        "//tensorflow/lite/core/api",
        "//tensorflow/lite/kernels/internal:compatibility",
        "//tensorflow/lite/kernels/internal:tensor",
        "//tensorflow/lite/micro/memory_planner",
        "//tensorflow/lite/micro/memory_planner:greedy_memory_planner",
        "//tensorflow/lite/schema:schema_fbs",
        "@flatbuffers//:runtime_cc",
    ],
)

cc_library(
    name = "debug_log",
    srcs = [
        "debug_log.cc",
    ],
    hdrs = [
        "debug_log.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
)

cc_library(
    name = "micro_error_reporter",
    srcs = [
        "micro_error_reporter.cc",
    ],
    hdrs = [
        "micro_error_reporter.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = [
        ":debug_log",
        ":micro_compatibility",
        ":micro_string",
        "//tensorflow/lite/core/api",
    ],
)

cc_library(
    name = "micro_string",
    srcs = [
        "micro_string.cc",
    ],
    hdrs = [
        "micro_string.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = ["//tensorflow/lite/c:common"],
)

cc_library(
    name = "micro_time",
    srcs = [
        "posix/micro_time.cc",
    ],
    hdrs = [
        "micro_time.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = ["//tensorflow/lite/c:common"],
)

cc_library(
    name = "micro_utils",
    srcs = [
        "micro_utils.cc",
    ],
    hdrs = [
        "micro_utils.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = [
        "//tensorflow/lite/c:common",
        "//tensorflow/lite/kernels:op_macros",
    ],
)

cc_library(
    name = "recording_simple_memory_allocator",
    srcs = [
        "recording_simple_memory_allocator.cc",
    ],
    hdrs = [
        "recording_simple_memory_allocator.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = [
        ":micro_compatibility",
        ":micro_framework",
    ],
)

tflite_micro_cc_test(
    name = "micro_error_reporter_test",
    srcs = [
        "micro_error_reporter_test.cc",
    ],
    deps = [
        ":micro_error_reporter",
    ],
)

tflite_micro_cc_test(
    name = "micro_mutable_op_resolver_test",
    srcs = [
        "micro_mutable_op_resolver_test.cc",
    ],
    deps = [
        ":micro_framework",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "micro_interpreter_test",
    srcs = [
        "micro_interpreter_test.cc",
    ],
    deps = [
        ":micro_framework",
        ":micro_utils",
        "//tensorflow/lite/core/api",
        "//tensorflow/lite/kernels:kernel_util",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "simple_memory_allocator_test",
    srcs = [
        "simple_memory_allocator_test.cc",
    ],
    deps = [
        ":micro_framework",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "recording_simple_memory_allocator_test",
    srcs = [
        "recording_simple_memory_allocator_test.cc",
    ],
    deps = [
        ":micro_framework",
        ":recording_simple_memory_allocator",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "micro_allocator_test",
    srcs = [
        "micro_allocator_test.cc",
    ],
    deps = [
        ":micro_framework",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "memory_helpers_test",
    srcs = [
        "memory_helpers_test.cc",
    ],
    deps = [
        ":micro_framework",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "testing_helpers_test",
    srcs = [
        "testing_helpers_test.cc",
    ],
    deps = [
        ":micro_framework",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "micro_utils_test",
    srcs = [
        "micro_utils_test.cc",
    ],
    deps = [
        ":micro_utils",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "micro_string_test",
    srcs = [
        "micro_string_test.cc",
    ],
    deps = [
        ":micro_string",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "micro_time_test",
    srcs = [
        "micro_time_test.cc",
    ],
    deps = [
        ":micro_time",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)
