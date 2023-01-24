# Install binary distribution

## MacOS with Homebrew

### Prerequisites

* [Homebrew](https://brew.sh/)
* Java JDK

!!!important

```
Hyperledger edeXa supports:

  * MacOS High Sierra 10.13 or later versions.
  * Java 11+.
    We recommend using at least Java 17 because that will be the minimum requirement in the next edeXa version series.
    You can install Java using `brew install openjdk`. Alternatively, you can manually install the
    [Java JDK](https://www.oracle.com/java/technologies/downloads).
```

### Install (or upgrade) using Homebrew

To install edeXa using Homebrew:

```bash
brew tap hyperledger/edexa
brew install hyperledger/edexa/edexa
```

To upgrade an existing edeXa installation using Homebrew:

```bash
brew upgrade hyperledger/edexa/edexa
```

!!! note

```
If you've upgraded your MacOS version between installing and upgrading edeXa, when running `brew upgrade
hyperledger/edexa/edexa` you may be prompted to reinstall command line tools with `xcode-select --install`.
```

!!! note

```
When upgrading edeXa, you might be prompted to fix the remote branch names in Homebrew by using the command
`brew tap --repair`.
```

To display the edeXa version and confirm installation:

```bash
edexa --version
```

To display edeXa command line help:

```bash
edexa --help
```

## Linux / Unix

### Prerequisites

* [Java JDK](https://www.oracle.com/java/technologies/downloads/)

!!! note "Linux open file limit"

```
If synchronizing to Mainnet on Linux or other chains with large data requirements, increase the
maximum number of open files allowed using `ulimit`. If the open files limit is not high
enough, a `Too many open files` RocksDB exception occurs.
```

### Install from packaged binaries

Download the edeXa [packaged binaries](https://edexa-blockchain.s3.eu-central-1.amazonaws.com/edexa.zip).

Unpack the downloaded files and change into the `edexa-<release>` directory.

Display edeXa command line help to confirm installation:

```bash
bin/edexa --help
```
