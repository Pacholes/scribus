include_directories(
${CMAKE_SOURCE_DIR}
${CMAKE_SOURCE_DIR}/scribus
)

set(2GEOM_VERSION 0.1.0)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${CMAKE_CXX_FLAGS_FPIC}")

option(2GEOM_BUILD_SHARED
  "Build lib2geom and libtoy as shared libraries."
  OFF)
set(LIB_TYPE STATIC)

set(2GEOM_SRC
svg-path.h
svg-path.cpp
ord.h
path.cpp
path.h
path-intersection.cpp
path-intersection.h
svg-elliptical-arc.h
shape.cpp
shape.h
region.cpp
region.h
crossing.h
crossing.cpp
sweep.cpp
sweep.h
poly.cpp
poly.h
poly-dk-solve.cpp
poly-dk-solve.h
poly-laguerre-solve.cpp
poly-laguerre-solve.h
quadtree.cpp
quadtree.h
matrix.cpp
matrix.h
transforms.cpp
transforms.h
point.h
point.cpp
point-l.h
coord.h
d2.h
d2-sbasis.h
d2-sbasis.cpp
rect.h
piecewise.h
piecewise.cpp
sbasis.cpp
sbasis.h
sbasis-2d.h
sbasis-2d.cpp
sbasis-geometric.cpp
sbasis-geometric.h
sbasis-math.h
sbasis-math.cpp
sbasis-poly.cpp
sbasis-poly.h
sbasis-roots.cpp
sbasis-to-bezier.cpp
sbasis-to-bezier.h
bezier-to-sbasis.h
basic-intersection.h
basic-intersection.cpp
geom.cpp
geom.h
utils.h
exception.h
angle.h
bezier-utils.cpp
bezier-utils.h
choose.h
circulator.h
conjugate_gradient.cpp
conjugate_gradient.h
convex-cover.cpp
convex-cover.h
solve-bezier-one-d.cpp
solve-bezier-parametric.cpp
solver.h
sturm.h
scribushelper.h
scribushelper.cpp
)

set(SCRIBUS_2GEOM_LIB "scribus_2geom_lib")
add_library(${SCRIBUS_2GEOM_LIB} STATIC ${2GEOM_SRC})

# This is a convenience library that for linkage purposes is part of Scribus's
# main API.
set_target_properties(${SCRIBUS_2GEOM_LIB}
  PROPERTIES
  COMPILE_FLAGS -DCOMPILE_SCRIBUS_MAIN_APP
  )
