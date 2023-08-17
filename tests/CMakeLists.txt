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

#[[carbin_cc_test(
        NAME custom_comparator_test
        SOURCES custom_comparator_test.cc
        DEPS turbo::turbo ${CARBIN_DEPS_LINK} ${GTEST_LIB} ${GTEST_MAIN_LIB}
        COPTS ${USER_CXX_FLAGS}
)]]
#[[
carbin_cc_test(
        NAME foo_test
        SOURCES foo_test.cc
        DEPS changeme::foo ${CARBIN_DEPS_LINK} gtest gtest_main
        COPTS ${USER_CXX_FLAGS}
)

carbin_cc_test(
        NAME foo_doctest
        SOURCES foo_doctest.cc
        DEPS changeme::foo ${CARBIN_DEPS_LINK} doctest
        COPTS ${USER_CXX_FLAGS}
)
]]
set(TEST_SRC
        test_constants.cc
        buffer_memory.cc
        buffer.cc
        unit_test.cc
        accuracy_test_common.cc
        accuracy_test_pow2.cc
        accuracy_test_pow3.cc
        accuracy_test_pow5.cc
        accuracy_test_pow7.cc
        accuracy_test_mixed_radices.cc
        accuracy_test_random.cc
        accuracy_test_directed.cc
        accuracy_test_mixed_callback.cc
        accuracy_test_pow2_precallback.cc
        accuracy_test_pow3_precallback.cc
        accuracy_test_pow5_precallback.cc
        accuracy_test_pow7_precallback.cc
        accuracy_test_postcallback.cc
        gtest_main.cc
        ${PROJECT_SOURCE_DIR}/clfft/client/openCL.misc.cc
        c-compliance.c
)

carbin_cc_test(
        NAME fft_test
        SOURCES ${TEST_SRC}
        DEPS clfft::fft ${CARBIN_DEPS_LINK} ${OPENCL_LIBRARIES} ${Boost_LIBRARIES} ${FFTW_LIBRARIES} turbo gtest
        COPTS ${USER_CXX_FLAGS}
)
