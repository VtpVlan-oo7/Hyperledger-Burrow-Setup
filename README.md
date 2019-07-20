# Hyperledger-Burrow-Setup

Step 1 – Install Go on Ubuntu

==>Login to your Ubuntu system using ssh and upgrade to apply latest security updates there.

$ sudo apt-get update
$ sudo apt-get -y upgrade

==>Now download the Go language binary archive file using following link. To find and download latest version available or 32 bit version go to official download page.

$ wget https://dl.google.com/go/go1.12.6.linux-amd64.tar.gz

==>Now extract the downloaded archive and install it to the desired location on the system. For this tutorial, I am installing it under /usr/local directory. You can also put this under the home directory (for shared hosting) or other location.

$ sudo tar -xvf go1.12.6.linux-amd64.tar.gz
$ sudo mv go /usr/local

Step 2 – Setup Go Environment

==>Now you need to setup Go language environment variables for your project. Commonly you need to set 3 environment variables as GOROOT, GOPATH and PATH.GOROOT is the location where Go package is installed on your system.

$ export GOROOT=/usr/local/go

==>GOPATH is the location of your work directory. For example my project directory is ~/Projects/Proj1 .

$ export GOPATH=$HOME/Projects/Proj1

==>Now set the PATH variable to access go binary system wide.

$ export PATH=$GOPATH/bin:$GOROOT/bin:$PATH

==>All the above environment will be set for your current session only. To make it permanent add above commands in ~/.profile file.

Step 3 – Verify Installation

==>At this step, you have successfully installed and configured go language on your system. First, use the following command to check the Go version.

$ go version
go version go1.12.6 linux/amd64


### Hyperledger-Burrow Installation 

Install go version 1.11 or above and have $GOPATH set

$ go get github.com/hyperledger/burrow
$ cd $GOPATH/src/github.com/hyperledger/burrow

# We need to force enable module support to build from within GOPATH (our protobuf build depends on path, otherwise any checkout location should work)

$ export GO111MODULE=on
$ make build

==>>This will build the burrow binary and put it in the bin/ directory. It can be executed from there or put wherever is convenient.
==>>You can also install burrow into $BIN_PATH/bin with make install, where $BIN_PATH defaults to $HOME/go/bin if not set in environment.



