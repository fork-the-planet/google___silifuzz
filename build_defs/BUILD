# Copyright 2022 The SiliFuzz Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Description:
#   Starlark rules and macros for building SiliFuzz

load("@bazel_skylib//:bzl_library.bzl", "bzl_library")
load("@bazel_skylib//lib:selects.bzl", "selects")
load("@bazel_skylib//rules:common_settings.bzl", "bool_flag")

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

# Build with integer instructions only.
# Currently this is only supported on aarch64.
bool_flag(
    name = "integer_instructions_only",
    build_setting_default = False,
)

config_setting(
    name = "integer_instructions_only_config",
    flag_values = {
        ":integer_instructions_only": "True",
    },
)

selects.config_setting_group(
    name = "integer_instructions_only_aarch64",
    match_all = [
        ":integer_instructions_only_config",
        "@silifuzz//build_defs/platform:aarch64",
    ],
)

bzl_library(
    name = "build_defs",
    srcs = glob(["*.bzl"]),
)
