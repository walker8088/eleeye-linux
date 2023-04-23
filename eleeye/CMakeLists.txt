
aux_source_directory(. SRCS)

# 编译源码生成目标
add_executable(eleeye ${SRCS})
target_link_libraries(eleeye base)
