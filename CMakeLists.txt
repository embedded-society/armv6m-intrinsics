# Copyright (C) 2026 The Embedded Society <https://github.com/embedded-society/armv6m-intrinsics>

# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at

#     http://www.apache.org/licenses/LICENSE-2.0

# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 3.13)

project(armv6m-intrinsics
    LANGUAGES CXX
    VERSION 0.1.0
    DESCRIPTION "C++ wrappers for ARMv6-M instructions not normally emitted by the compiler (Cortex-M0, M0+, M1)"
    HOMEPAGE_URL "https://github.com/embedded-society/armv6m-intrinsics"
)

add_library(${PROJECT_NAME} INTERFACE)

target_compile_features(${PROJECT_NAME} INTERFACE cxx_std_20)

target_include_directories(${PROJECT_NAME} INTERFACE
    "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

target_sources(${PROJECT_NAME} INTERFACE
    "${CMAKE_CURRENT_SOURCE_DIR}/include/armv6m-intrinsics/barriers.hpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/include/armv6m-intrinsics/hints.hpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/include/armv6m-intrinsics/interrupts.hpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/include/armv6m-intrinsics/reverse.hpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/include/armv6m-intrinsics/svc.hpp"
)
