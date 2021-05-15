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
    fips_vs_disable_warnings(4312)   # 'type cast': conversion from 'int' to 'void *' of greater size
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
    set_target_properties(imgui PROPERTIES COMPILE_FLAGS "-Wno-unused-parameter -Wno-type-limits -Wno-missing-field-initializers")
elseif(FIPS_GCC)
    set_target_properties(imgui PROPERTIES COMPILE_FLAGS "-Wno-unused-but-set-variable -Wno-type-limits -Wno-missing-field-initializers")
endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()

