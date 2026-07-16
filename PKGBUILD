# Maintainer: JappeOS

# Source URL: https://launchpad.net/ubuntu/+source/ubuntu-wallpapers

pkgname=jappeos_wallpapers
pkgver=1.0.3
_tag=main-v1.0.3-1
pkgrel=1
pkgdesc="Default wallpapers for JappeOS, based on Ubuntu community wallpapers"
arch=('any')
url="https://github.com/JappeOS/$pkgname"
license=('CC-BY-SA-3.0')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/$_tag.tar.gz")
sha256sums=('SKIP')

package() {
  local _bundle="$srcdir/$pkgname-$_tag"
  cd "$_bundle"

  local backgrounds_dir="$pkgdir/usr/share/backgrounds/jappeos"
  local licenses_dir="$pkgdir/usr/share/licenses/$pkgname"
  local docs_dir="$pkgdir/usr/share/doc/$pkgname"

  install -dm755 "$backgrounds_dir" "$licenses_dir" "$docs_dir"

  # Install all wallpaper image files from this source tree.
  find "$_bundle" -maxdepth 1 -type f \( -iname '*.jpg' -o -iname '*.png' \) \
    -exec install -m644 -t "$backgrounds_dir" '{}' +

  # Preserve license and attribution information from the original package.
  install -m644 "$_bundle/COPYING" "$licenses_dir/COPYING"
  install -m644 "$_bundle/AUTHORS" "$licenses_dir/AUTHORS"

  cat > "$docs_dir/README.JappeOS" <<'EOF'
These wallpapers come from the Ubuntu wallpapers source package.

They are licensed under the Creative Commons Attribution-ShareAlike 3.0
Unported License. See /usr/share/licenses/jappeos-wallpapers/COPYING.

Original image authors are listed in:
/usr/share/licenses/jappeos-wallpapers/AUTHORS

If you modify any image, mark your changes and distribute the modified image
under CC BY-SA 3.0 or another license allowed by CC BY-SA 3.0.

Do not imply endorsement by Ubuntu, Canonical, or the original photographers.
EOF
}
