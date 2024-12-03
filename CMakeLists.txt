###############################################################################
# Copyright (c) ATTX LLC 2024. All Rights Reserved.
#
# This software and associated documentation (the "Software") are the 
# proprietary and confidential information of ATTX, LLC. The Software is 
# furnished under a license agreement between ATTX and the user organization 
# and may be used or copied only in accordance with the terms of the agreement.
# Refer to 'license/attx_license.adoc' for standard license terms.
#
# EXPORT CONTROL NOTICE: THIS SOFTWARE MAY INCLUDE CONTENT CONTROLLED UNDER THE
# INTERNATIONAL TRAFFIC IN ARMS REGULATIONS (ITAR) OR THE EXPORT ADMINISTRATION 
# REGULATIONS (EAR99). No part of the Software may be used, reproduced, or 
# transmitted in any form or by any means, for any purpose, without the express 
# written permission of ATTX, LLC.
###############################################################################
cmake_minimum_required(VERSION 3.8)
project(imgui VERSION 1.98)

# Set C++ standard to 14 and set flags for PIC and warnings
# O2 level code optimization
set(CMAKE_CXX_STANDARD            14)
set(CMAKE_CXX_STANDARD_REQUIRED   YES)
set(CMAKE_CXX_FLAGS "-g -O2 -Wall -fPIC")

# Set include directory as this directory, the imgui project, for if any CMake
# files depend on this directory
include_directories(${PROJECT_SOURCE_DIR})
include_directories(${PROJECT_SOURCE_DIR}/backends)

# Now build our imgui library. For this simple case we are going to quite literally,
# manually add files rather than adding by glob_recurse
set(IMGUI_SRC imgui.cpp  imgui_demo.cpp  imgui_draw.cpp  imgui_tables.cpp  imgui_widgets.cpp)
set(IMGUI_BACKEND backends/imgui_impl_dx11.cpp backends/imgui_impl_opengl3.cpp backends/imgui_impl_sdl2.cpp)

set(IMGUI_ALL ${IMGUI_SRC} ${IMGUI_BACKEND})
add_library(imgui STATIC ${IMGUI_ALL})