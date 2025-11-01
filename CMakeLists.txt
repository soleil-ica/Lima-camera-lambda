# --------------------------------------------------------------------------
# Dependencies
# --------------------------------------------------------------------------

find_package(yat CONFIG REQUIRED)
find_package(xsp CONFIG REQUIRED)

# --------------------------------------------------------------------------
# Collect sources
# --------------------------------------------------------------------------

file(GLOB_RECURSE sources src/*.cpp)
set(includedirs
    include/
)

# --------------------------------------------------------------------------
# Target
# --------------------------------------------------------------------------

add_library(limalambda ${sources})
target_include_directories(limalambda 
    PUBLIC 
        ${includedirs}
)
target_link_libraries(limalambda 
    PUBLIC 
        limacore
        yat::yat
        xsp::xsp
)

limatools_set_library_soversion(limalambda "VERSION")

# --------------------------------------------------------------------------
# Compile definitions
# --------------------------------------------------------------------------

file(READ "${CMAKE_CURRENT_SOURCE_DIR}/VERSION" LAMBDA_VERSION_RAW)
string(STRIP "${LAMBDA_VERSION_RAW}" LAMBDA_VERSION)

target_compile_definitions(limalambda
    PUBLIC
        LAMBDA_NAME=Lambda
        LAMBDA_VERSION=${LAMBDA_VERSION}
        LAMBDA_ENABLED
)

message(STATUS "Camera enabled: Lambda ${LAMBDA_VERSION}")

# --------------------------------------------------------------------------
# Install
# --------------------------------------------------------------------------

install(
    TARGETS limalambda 
    LIBRARY DESTINATION lib
)
