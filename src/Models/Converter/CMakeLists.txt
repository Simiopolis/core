file(GLOB all_valid_subdirs RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "*/CMakeLists.txt")

foreach(dir ${all_valid_subdirs})
    if(${dir} MATCHES "^([^/]*)//CMakeLists.txt")
        string(REGEX REPLACE "^([^/]*)//CMakeLists.txt" "\\1" dir_trimmed ${dir})
        add_subdirectory(${dir_trimmed})
    endif()
endforeach(dir)

SET(ModelTestSource ${ModelTestSource} ${ConverterTestSource} PARENT_SCOPE)
STRING(REPLACE ";" "\n\ \ \ \ \ \ \ \ " Converter_REFS "${Converter_REFS}")
STRING(REPLACE ";" "\n\ \ " RNG_INCLUDES "${RNG_INCLUDES}")
SET(Converter_REFS ${Converter_REFS} PARENT_SCOPE)
SET(RNG_INCLUDES ${RNG_INCLUDES} PARENT_SCOPE)
