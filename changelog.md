# Changelog for [`filepath` package](http://hackage.haskell.org/package/filepath)

_Note: below all `FilePath` values are unquoted, so `\\` really means two backslashes._

## 1.4.100.0 *July 2022*

Implementation of the [Abstract FilePath Proposal](https://gitlab.haskell.org/ghc/ghc/-/wikis/proposal/abstract-file-path)
in user-space as a separate type.

Introduction to the new API is explained [in this blog post](https://hasufell.github.io/posts/2022-06-29-fixing-haskell-filepaths.html).

## 1.4.2.2 *Dec 2021*

This release is purely a documentation release, fixing the broken haddock links.

### Affected users

This release affects users who apply downstream patches to `System.FilePath.Internal`,
since `System.FilePath.Posix` and `System.FilePath.Windows` are now generated via `make cpp`
during development.

To make your patch apply, either apply it to `System.FilePath.Posix` and `System.FilePath.Windows`
instead or run `make cpp` after applying your patch.

### Changes

* Document relation between `joinPath` and `(</>)` wrt [#82](https://github.com/haskell/filepath/issues/82), [#82](https://github.com/haskell/filepath/issues/86)
* Clarify that `normalise` does not remove `..` wrt [#86](https://github.com/haskell/filepath/issues/86)
* Make clear that `equalFilePath` does not expand `..` wrt [#87](https://github.com/haskell/filepath/issues/87)
* Fix haddock source links by manually cpping wrt [#81](https://github.com/haskell/filepath/issues/81)
* Make export list in `System.FilePath` explicit to get haddocks on the landing module


## 1.4.2.1 *Jul 2018*

 * Bundled with GHC 8.6.1

## 1.4.2 *Jan 2018*

 * Bundled with GHC 8.4.1

 * Add `isExtensionOf` function.

## 1.4.1.2  *Feb 2017*

 * Bundled with GHC 8.2.1

## 1.4.1.1  *Nov 2016*

 * Bundled with GHC 8.0.2

 * Documentation improvements

## 1.4.1.0  *Dec 2015*

 * Bundled with GHC 8.0.1

 * Add `replaceExtensions` and `stripExtension` functions.

 * Make `isValid` detect more invalid Windows paths, e.g. `nul .txt` and `foo\nbar`.

 * Improve the documentation.

 * Bug fix: `isValid "\0"` now returns `False`, instead of `True`

## 1.4.0.0  *Mar 2015*

  * Bundled with GHC 7.10.1

  * New function: Add `-<.>` as an alias for `replaceExtension`.

  * Semantic change: `joinDrive /foo bar` now returns `/foo/bar`, instead of `/foobar`

  * Semantic change: on Windows, `splitSearchPath File1;\"File 2\"` now returns `[File1,File2]` instead of `[File1,\"File2\"]`

  * Bug fix: on Posix systems, `normalise //home` now returns `/home`, instead of `//home`

  * Bug fix: `normalise /./` now returns `/` on Posix and `\` on Windows, instead of `//` and `\\`

  * Bug fix: `isDrive ""` now returns `False`, instead of `True`

  * Bug fix: on Windows, `dropTrailingPathSeparator /` now returns `/` unchanged, instead of the normalised `\`

  * Bug fix: on Windows, `equalFilePath C:\ C:` now returns `False`, instead of `True`

  * Bug fix: on Windows, `isValid \\\foo` now returns `False`, instead of `True`

  * Bug fix: on Windows, `isValid \\?\D:file` now returns `False`, instead of `True`

  * Bug fix: on Windows, `normalise \` now returns `\` unchanged, instead of `\\`

  * Bug fix: on Windows, `normalise C:.\` now returns `C:`, instead of `C:\\`

  * Bug fix: on Windows, `normalise //server/test` now returns `\\server\test`, instead of `//server/test` unchanged

  * Bug fix: on Windows, `makeRelative / //` now returns `//`, instead of `""`

## 1.3.0.2  *Mar 2014*

  * Bundled with GHC 7.8.1

  * Update to Cabal 1.10 format

  * Minor Haddock cleanups

## 1.3.0.1  *Sep 2012*

  * Bundled with GHC 7.6.1

  * No changes

## 1.3.0.0  *Feb 2012*

  * Bundled with GHC 7.4.1

  * Add support for SafeHaskell

  * Bug fix: `normalise /` now returns `/`, instead of `/.`
