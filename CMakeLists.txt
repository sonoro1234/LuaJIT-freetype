PROJECT(LuaJIT-freetype)
cmake_minimum_required(VERSION 3.13)
if(WIN32) #to mingw work as all the others
set(CMAKE_SHARED_LIBRARY_PREFIX "")
endif(WIN32)
set(BUILD_SHARED_LIBS ON CACHE BOOL "" FORCE)
add_subdirectory(freetype EXCLUDE_FROM_ALL)
add_custom_target(LuaJIT-freetype ALL)
add_dependencies(LuaJIT-freetype freetype)
install(TARGETS freetype RUNTIME DESTINATION ${LUAJIT_BIN}
					LIBRARY DESTINATION ${LUAJIT_BIN}
)
INSTALL(FILES freetype.lua freetype_h.lua DESTINATION ${LUAJIT_BIN}/lua)