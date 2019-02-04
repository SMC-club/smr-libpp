
cmake_minimum_required(VERSION 3.9)
project(smc-libppdemo)

#[===========================================[
  this pulls-in the smcd source code via
  git submodule. This demo exe depends on the
  xrpl_core library which is defined by the
  smcd project.
#]===========================================]
if (MSVC)
  #[=======================================[
    HACK to patch a one-line windows-only
    bug in smcd CMakeLists.txt. This can
    be removed once smcd 1.2 is available
    and we update the submodule
  #]=======================================]
  execute_process( COMMAND powershell -Command
     "(Get-Content extras/smcd/CMakeLists.txt) \
     -replace '^exclude_if_included\\s+\\(rocksdb\\)', '##' \
     | Set-Content extras/smcd/CMakeLists.txt"
     WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  )
endif ()
add_subdirectory(extras/smcd)

add_executable(smclibppdemo src/test/smc-libpp_demo.cpp)
target_link_libraries (smclibppdemo Ripple::xrpl_core)
