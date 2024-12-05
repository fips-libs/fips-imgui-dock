#
# project: fips-imgui-dock
#

if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 3.0)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-imgui-dock)
endif()

fips_begin_lib(imgui-dock)
    fips_dir(imgui-dock)
    fips_files(
        imconfig.h
        imgui.cpp
        imgui.h
        imgui_demo.cpp
        imgui_draw.cpp
        imgui_internal.h
        imgui_tables.cpp
        imgui_widgets.cpp
        imstb_rectpack.h
        imstb_textedit.h
        imstb_truetype.h
    )
fips_end_lib()
target_include_directories(imgui-dock PUBLIC .)

if (FIPS_CLANG)
    target_compile_options(imgui-dock PRIVATE -Wno-unused-parameter -Wno-type-limits -Wno-missing-field-initializers)
elseif(FIPS_GCC)
    target_compile_options(imgui-dock PRIVATE -Wno-unused-but-set-variable -Wno-type-limits -Wno-missing-field-initializers)
elseif(FIPS_MSVC)
    target_compile_options(imgui-dock PRIVATE /wd4312)
endif()
