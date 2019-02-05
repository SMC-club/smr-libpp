
cmake_minimum_required(VERSION 3.9)
project(smr-libppdemo)

#[===========================================[
  this pulls-in the smrd source code via
  git submodule. This demo exe depends on the
  xrpl_core library which is defined by the
  smrd project.
#]===========================================]
if (MSVC)
  #[=======================================[
    HACK to patch a one-line windows-only
    bug in smrd CMakeLists.txt. This can
    be removed once smrd 1.2 is available
    and we update the submodule
  #]=======================================]
  execute_process( COMMAND powershell -Command
     "(Get-Content extras/smrd/CMakeLists.txt) \
     -replace '^exclude_if_included\\s+\\(rocksdb\\)', '##' \
     | Set-Content extras/smrd/CMakeLists.txt"
     WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  )
endif ()
add_subdirectory(extras/smrd)

add_executable(smrlibppdemo src/test/smr-libpp_demo.cpp)
target_link_libraries (smrlibppdemo Ripple::xrpl_core)
