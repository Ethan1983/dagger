# Copyright (C) 2017 The Dagger Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Description:
#   Functional tests for Dagger Producers

package(default_visibility = ["//:src"])

load(
    "//:build_defs.bzl",
    "DOCLINT_HTML_AND_SYNTAX",
    "DOCLINT_REFERENCES",
    "SOURCE_7_TARGET_7",
)
load("//:test_defs.bzl", "GenJavaTests")

GenJavaTests(
    name = "producers-functional-tests",
    srcs = glob(["**/*.java"]),
    javacopts = SOURCE_7_TARGET_7 + DOCLINT_HTML_AND_SYNTAX + DOCLINT_REFERENCES,
    deps = [
        "//:producers_with_compiler",
        "@google_bazel_common//third_party/java/auto:value",
        "@google_bazel_common//third_party/java/guava",
        "@google_bazel_common//third_party/java/jsr305_annotations",
        "@google_bazel_common//third_party/java/jsr330_inject",
        "@google_bazel_common//third_party/java/junit",
        "@google_bazel_common//third_party/java/mockito",
        "@google_bazel_common//third_party/java/truth",
    ],
)

GenJavaTests(
    name = "producers-functional-tests-with-aot",
    srcs = glob(
        ["**/*.java"],
        # TODO(b/72748365): Remove these exclusions
        exclude = [
            "subcomponent/*.java",
            "subcomponent/pruning/ProductionSubcomponentOnlyRequestedBySiblingTest.java",
            "cancellation/ProducerSubcomponentCancellationTest.java",
            "cancellation/CancellationPolicyTest.java",
        ],
    ),
    javacopts = SOURCE_7_TARGET_7 + DOCLINT_HTML_AND_SYNTAX + DOCLINT_REFERENCES,
    with_aot = True,
    deps = [
        "//:producers_with_compiler",
        "@google_bazel_common//third_party/java/auto:value",
        "@google_bazel_common//third_party/java/guava",
        "@google_bazel_common//third_party/java/jsr305_annotations",
        "@google_bazel_common//third_party/java/jsr330_inject",
        "@google_bazel_common//third_party/java/junit",
        "@google_bazel_common//third_party/java/mockito",
        "@google_bazel_common//third_party/java/truth",
    ],
)

test_suite(name = "AllTests")
