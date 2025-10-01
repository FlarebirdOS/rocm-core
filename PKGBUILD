pkgname=rocm-core
pkgver=6.4.4
pkgrel=1
pkgdesc="AMD ROCm core package (version files)"
arch=('x86_64')
url="https://rocm.docs.amd.com/en/latest/"
license=('MIT')
depends=(
    'gcc-libs'
    'glibc'
)
makedepends=('cmake')
source=(https://github.com/ROCm/rocm-core/archive/refs/tags/rocm-${pkgver}/${pkgname}-rocm-${pkgver}.tar.gz)
sha256sums=(ec5ef028823b863c83d098ca22343febf9e15a778c71f19e10a52eece50f7fed)

build() {
    cd ${pkgname}-rocm-${pkgver}

    local cmake_args=(
        -B flarebird-build
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D CMAKE_INSTALL_LIBDIR=lib64
        -D BUILD_SHARED_LIBS=ON
        -D ROCM_VERSION=${pkgver}
        -W no-dev
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build

}

package() {
    cd ${pkgname}-rocm-${pkgver}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
