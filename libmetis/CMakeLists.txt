# Add this directory for internal users.
include_directories(.)

# Find sources.
file(GLOB metis_sources *.c)

# Build libmetis.
add_library(metis ${METIS_LIBRARY_TYPE} ${metis_sources})

# GKlib and Headers
target_link_libraries(metis PUBLIC GKlib)
get_target_property(MY_LIBRARY_INCLUDE_DIRS  GKlib INCLUDE_DIRECTORIES)
target_include_directories(metis PUBLIC ${MY_LIBRARY_INCLUDE_DIRS})

if(METIS_INSTALL)
  install(TARGETS metis
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION lib
    ARCHIVE DESTINATION lib)
endif()
