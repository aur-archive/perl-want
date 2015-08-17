# Maintainer: Maxwell Pray a.k.a. Synthead <synthead@gmail.com>
# Contributor: Caleb Cushing <xenoterracide@gmail.com>

pkgname="perl-want"
_cpanname="Want"
pkgver="0.23"
pkgrel="1"
pkgdesc="A generalisation of wantarray"
arch=("i686" "x86_64")
url="http://search.cpan.org/dist/$_cpanname"
license=("PerlArtistic" "GPL")
depends=("perl>=5.5.0")
options=("!emptydirs")
source=("http://search.cpan.org/CPAN/authors/id/R/RO/ROBIN/$_cpanname-$pkgver.tar.gz")
sha1sums=('0e391874860988cbdac2d5448ae66179e8b6e993')

# Function to change to the working directory and set
# environment variables to override undesired options.
prepareEnvironment() {
  cd "$srcdir/$_cpanname-$pkgver"
  export \
    PERL_MM_USE_DEFAULT=1 \
    PERL_AUTOINSTALL=--skipdeps \
    PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
    PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
    MODULEBUILDRC=/dev/null
}

build() {
  prepareEnvironment
  /usr/bin/perl Makefile.PL
  make
}

check() {
  prepareEnvironment
  make test
}

package() {
  prepareEnvironment
  make install

  # Remove "perllocal.pod" and ".packlist".
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
