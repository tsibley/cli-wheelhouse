# Single-executable file (PEX)

The Nextstrain CLI is also available as a single-executable file that can be
run on Linux or macOS with any copy of Python 3.5 or newer, no `pip install`
required (though you'll still need Docker).

First download the file from the [cli-pex repository][] and mark it executable:

    curl -fsSL https://github.com/nextstrain/cli-pex/raw/master/nextstrain > nextstrain
    chmod +x nextstrain

Then test it out by running a couple commands:

    ./nextstrain version
    ./nextstrain check-setup

If you move the downloaded file to somewhere in your `PATH`—for example
`/usr/local/bin` or `~/bin`—you'll be able to run it without specifying its
full location.

[cli-pex repository]: https://github.com/nextstrain/cli-pex

## How its made

The single-file is a [PEX file][] built with `pex`.

When a new `nextstrain-cli` release is made and uploaded to PyPi using
`./devel/release`, a Travis CI rebuild of the [cli-pex repository][] is
triggered.  [That repository's Travis config][travis-pex] downloads or builds
multi-platform dependencies and then builds the PEX.  The Travis builds only
happen when manually triggered as they push new commits back to the same
repository.

[PEX file]: https://pex.readthedocs.io
[travis-pex]: https://github.com/nexstrain/cli/blob/master/.travis.yml
