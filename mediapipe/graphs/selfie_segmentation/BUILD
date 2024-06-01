# Copyright 2021 The MediaPipe Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load(
    "//mediapipe/framework/tool:mediapipe_graph.bzl",
    "mediapipe_binary_graph",
)

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "selfie_segmentation_gpu_deps_image",
    deps = [
        "//mediapipe/calculators/image:recolor_calculator",
        "//mediapipe/calculators/image:image_transformation_calculator",
        "//mediapipe/calculators/image:mask_overlay_calculator",
        "//mediapipe/calculators/image:ColorSliderCalculator",
        "//mediapipe/calculators/core:flow_limiter_calculator",
        "//mediapipe/calculators/core:packet_cloner_calculator",
        "//mediapipe/calculators/core:packet_presence_calculator",
        "//mediapipe/calculators/core:gate_calculator",
        "//mediapipe/gpu:image_frame_to_gpu_buffer_calculator",
        "//mediapipe/gpu:gpu_buffer_to_image_frame_calculator",
        "//mediapipe/modules/selfie_segmentation:selfie_segmentation_gpu_image",
        "//mediapipe/modules/face_landmark:face_landmark_front_gpu_image",
    ],
)

mediapipe_binary_graph(
    name = "selfie_segmentation_gpu_binary_graph_image",
    graph = "selfie_segmentation_gpu_image.pbtxt",
    output_name = "selfie_segmentation_gpu_image.binarypb",
    deps = [":selfie_segmentation_gpu_deps_image"],
)

cc_library(
    name = "selfie_segmentation_gpu_image_to_color_deps",
    deps = [
        "//mediapipe/calculators/core:flow_limiter_calculator",
        "//mediapipe/calculators/image:recolor_calculator",
        "//mediapipe/modules/selfie_segmentation:selfie_segmentation_gpu",
    ],
)

mediapipe_binary_graph(
    name = "selfie_segmentation_gpu_image_to_color_binary_graph",
    graph = "selfie_segmentation_gpu_image_to_color.pbtxt",
    output_name = "selfie_segmentation_gpu_image_to_color.binarypb",
    deps = [":selfie_segmentation_gpu_image_to_color_deps"],
)
