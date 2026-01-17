cmake_minimum_required(VERSION 3.30)

set(NAME libomp)
set(VERSION "21.1.8")
set(EXT tar.xz)
set(SHA256 856b023748b41ac7b2c83fd8e9f765ff48a4df2fe6777d2811ef7c7ed8f2f977)

project("cmeel-${NAME}" VERSION "${VERSION}")

include(ExternalProject)
ExternalProject_Add(
  ${NAME}
  URL "https://github.com/llvm/llvm-project/releases/download/llvmorg-${VERSION}/openmp-${VERSION}.src.${EXT}"
  URL_HASH "SHA256=${SHA256}"
  CMAKE_ARGS "-DOPENMP_STANDALONE_BUILD=ON"
)

# dummy file for install target
install(FILES "README.md" DESTINATION "share/cmeel-${NAME}/")
