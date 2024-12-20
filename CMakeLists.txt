cmake_minimum_required(VERSION 3.10)
project(TKN2 VERSION 1.0 LANGUAGES C)
set(CMAKE_C_STANDARD 99)

add_executable(webserver src/webserver.c)

set(CPACK_GENERATOR "TGZ")
set(CPACK_PACKAGE_NAME "praxis1")
set(CPACK_PACKAGE_FILE_NAME "praxis1")
set(CPACK_SET_DESTDIR ON)
set(CPACK_INSTALL_PREFIX "")

install(TARGETS webserver 
        RUNTIME DESTINATION bin)

install(FILES 
        ${CMAKE_SOURCE_DIR}/src/webserver.c
        DESTINATION src)

install(FILES 
        ${CMAKE_SOURCE_DIR}/CMakeLists.txt
        ${CMAKE_SOURCE_DIR}/group.txt
        ${CMAKE_SOURCE_DIR}/requirements.txt
        ${CMAKE_SOURCE_DIR}/test_praxis1.py
        ${CMAKE_SOURCE_DIR}/tox.ini
        ${CMAKE_SOURCE_DIR}/conftest.py
        ${CMAKE_SOURCE_DIR}/util.py
        ${CMAKE_SOURCE_DIR}/check_submission.sh
        DESTINATION .)

set(CPACK_SOURCE_GENERATOR "TGZ")
set(CPACK_SOURCE_PACKAGE_FILE_NAME "praxis1")
set(CPACK_SOURCE_IGNORE_FILES
    "/build/"
    "/.git/"
    "/.venv/"
)

include(CPack)