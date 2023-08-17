#
# Copyright 2023 The titan-search Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
###########################################################################
# below are examples, after initialization, modify it to your own.
###########################################################################
###carbin_example
configure_file( "${PROJECT_SOURCE_DIR}/clfft/fft/clFFT.version.h.in" "${PROJECT_SOURCE_DIR}/clfft/fft/clFFT.version.h" )
set(FFT_SRC
        fft/transform.cc
        fft/dllmain.cc
        fft/accessors.cc
        fft/plan.cc
        fft/repo.cc
        fft/generator.stockham.cc
        fft/generator.transpose.gcn.cc
        fft/generator.transpose.cc
        fft/action.transpose.cc
        fft/generator.copy.cc
        fft/lifetime.cc
        fft/fft_binary_lookup.cc
        fft/md5sum.c
        fft/enqueue.cc
        fft/stdafx.cc
        timer/statisticalTimer.CPU.cc
        timer/statisticalTimer.GPU.cc
        timer/statisticalTimer.extern.cc
        timer/stdafx.cc
        timer/dllmain.cc
)

if(BUILD_STATIC_LIBRARY)
carbin_cc_library(
        NAMESPACE clfft
        NAME fft
        SOURCES
        ${FFT_SRC}
        COPTS
        ${CARBIN_CXX_OPTIONS}
        DEPS
        ${CARBIN_DEPS_LINK}
        PUBLIC
)
endif ()

if(BUILD_SHARED_LIBRARY)
    carbin_cc_library(
            NAMESPACE clfft
            NAME fft
            SOURCES
            ${FFT_SRC}
            COPTS
            ${CARBIN_CXX_OPTIONS}
            DEPS
            ${CARBIN_DEPS_LINK}
            PUBLIC
            SHARED
    )
endif ()