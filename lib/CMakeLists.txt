
add_library(a)
target_sources(a
        PUBLIC
          FILE_SET cxx_modules TYPE CXX_MODULES FILES
        a.cppm)
