
cmake_minimum_required(VERSION 3.6)
project(eleeye)

# 设置
set(CMAKE_CXX_STANDARD 11)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)

#准备的版本设置
SET(MAJOR_VERSION 3)
SET(MINOR_VERSION 1)
SET(PATCH_VERSION 3)

#说明要生成的是deb包
SET(CPACK_GENERATOR "DEB")

##############设置debian/control文件中的内容###############
#设置版本信息
set(CPACK_PACKAGE_VERSION_MAJOR "${MAJOR_VERSION}")
set(CPACK_PACKAGE_VERSION_MINOR "${MINOR_VERSION}")
set(CPACK_PACKAGE_VERSION_PATCH "${PATCH_VERSION}")

#设置安装包的包名，打好的包将会是packagename-version-linux.deb，如果不设置，默认是工程名
#set(CPACK_PACKAGE_NAME "cn.net.pikachu.bulbasaur")

set(CPACK_DEBIAN_FILE_NAME DEB-DEFAULT)
set(CPACK_DEBIAN_PACKAGE_NAME "eleeye")
set(CPACK_DEBIAN_PACKAGE_SECTION "game")
set(CPACK_DEBIAN_PACKAGE_PRIORITY "Optional")

#set(X86 ON)
#set(X86_64 OFF)

if(X86)
  set (CPACK_DEBIAN_PACKAGE_ARCHITECTURE "i386")
  set (CPACK_RPM_PACKAGE_ARCHITECTURE    "i686")
elseif(X86_64)
  set (CPACK_DEBIAN_PACKAGE_ARCHITECTURE "amd64")
  set (CPACK_RPM_PACKAGE_ARCHITECTURE    "x86_64")
endif(X86)

set(CPACK_DEBIAN_PACKAGE_DEPENDS "libc6 (>= 2.3.1-6)")
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/LICENSE")
set(CPACK_PACKAGE_DESCRIPTION "eleeye Chinese Chess UCCI engine linux rebuild")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Chinese Chess UCCI engine")
set(CPACK_PACKAGE_CONTACT "walker8088@gmail.com")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Walker Li")


include(CPack)

add_subdirectory(base)
add_subdirectory(eleeye)

install(TARGETS eleeye RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR} )

