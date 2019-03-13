`_sastack`: Stand-alone Pre-built Haskell Stack
===============================================

The [Haskell Tool Stack][stack] is brilliant, but under some
circumstances the initial build time for dependencies for simple
projects is a problem. For example, if you want to use [Hakyll] to
build a static web site on [Netlify]'s build server you'll find that
the initial download and build of the dependencies takes more than the
half-hour time limit provided by their build container.

In some circumstances you'd just use stack's ["Docker integration"],
but that doesn't work when you're already in a Docker container.

This repo is intended to provide: the `stack` binary and pre-installed
GHC plus pre-built packages for a particular stack resolver (e.g.
`lts-12.26`) and application. With this you can make this repo a [Git
submodule] and, with a little bit of configuration (basically, setting
[`$STACK_ROOT`] and possibly adding this repo's `.local/bin/` to
`$PATH`) greatly reduce the amount of build work the build container
needs to do.


Stack Versions
--------------

Handling different versions of Linux may be an issue, though Stack
tries to make this as easy as possible. Currently the code in this
repo assumes that the build container will be some reasonably recent
version of 64-bit (`x86_64`) architecture Linux that's not too far
different from Debian/Ubuntu.

For details of the different versions of generic Linux `stack` see the
["Manual download"] section of the Stack User Guide. Here we use the
"Linux 64-bit, standard" version which should work on most generic
build containers supplied by services such as [Netlify]. There are
several development-related OS dependencies listed there; these need
either be installed already or Stack must have sudo access to install
them.



<!-------------------------------------------------------------------->
["Docker integration"]: https://docs.haskellstack.org/en/stable/docker_integration/
["Manual download"]: https://docs.haskellstack.org/en/stable/install_and_upgrade/#manual-download_2
[Git submodule]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[Hakyll]: https://jaspervdj.be/hakyll/
[Netlify]: https://www.netlify.com/
[`$STACK_ROOT`]: https://docs.haskellstack.org/en/stable/GUIDE/#setting-stack-root-location
[stack]: https://haskellstack.org
