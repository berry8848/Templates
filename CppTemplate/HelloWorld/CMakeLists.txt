cmake_minimum_required(VERSION 3.10)

project(HelloSO)

# 出力先のディレクトリ
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

# 共有ライブラリ（.so）をビルド
add_library(hello SHARED
    src/hello.cpp
)

target_include_directories(hello PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# 実行ファイルをビルド
add_executable(main_exec
    src/main.cpp
)

target_include_directories(main_exec PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# 実行ファイルとライブラリをリンク
target_link_libraries(main_exec hello)
