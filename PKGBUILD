# Maintainer: aliu <AA RON LIU <GMAIL.COM> >
pkgname=python-rapidocr
pkgver=3.4.2
pkgrel=1
pkgdesc='Cross-runtime OCR library'
arch=('any')
license=('Apache-2.0')
depends=('python>=3.6'
	'python-pyclipper>=1.2.0'
	'python-opencv>=4.5.1.48'
	'python-numpy>=1.19.5' 'python-numpy<3.0.0'
	'python-six>=1.15.0'
	'python-shapely>=1.7.1' #'python-shapely!=2.0.4'
	'python-yaml'
	'python-pillow'
	'python-tqdm'
	'python-omegaconf'
	'python-requests'
	'python-colorlog')
optdepends=(
	'onnxruntime: Recommended runtime'
	'onnxruntime-cpu: Faster than GPU-accelerated onnxruntime (https://github.com/microsoft/onnxruntime/issues/13198)'
	'openvino: Supported runtime'
	'paddlepaddle: Supported runtime'
	'python-pytorch: Supported runtime'
)
makedepends=('python-build' 'python-installer' 'python-setuptools')
url='https://github.com/RapidAI/RapidOCR'
source=("https://github.com/RapidAI/RapidOCR/archive/v${pkgver}.tar.gz"
	'setup.py.patch')
sha256sums=('f5802814571beadbb19620adc61e39d9ccc8dfa31737168787f9fe4f21bc479f'
			'ebfa9ac2f957378702f1ec6d07e8ca7b2a3f1c66e8194fc63bc8a35dfcebb5ca')

prepare() {
	cd "${srcdir}/RapidOCR-${pkgver}/python"
	# Patch in version number without needing to install a nonce dependency
	# that fetches the version number from PyPI (what)
	patch < "$srcdir/setup.py.patch"
	sed -i "s/version=VERSION_NUM/version=\"${pkgver}\"/" setup.py
	# From gen_whl_to_pypi_rapidocr GH Action
	mkdir rapidocr_t; mv rapidocr{,_t/}; mv -T rapidocr{_t,}  # nest rapidocr within rapidocr
	cd rapidocr
    echo "from .rapidocr.main import RapidOCR, VisRes" > __init__.py
}

build() {
	cd "${srcdir}/RapidOCR-${pkgver}/python"
	python setup.py build
}

package() {
	cd "${srcdir}/RapidOCR-${pkgver}/python"
	python setup.py install --root="${pkgdir}" --optimize=1
}

# check() {
# 	$pkgdir/usr/bin/rapidocr check
# }
