# wolf-xmr-miner

Wolf's OpenCL XMR Miner for AMD GPUs

If you get an error about `clCreateBuffer`, lower your `rawintensity`. See the example config [xmr.conf](xmr.conf) for details.

Generally, you want to raise `rawintensity` as high as it will go without error - but remember, 2MiB of GPU RAM is needed for every work-item.

The GPU fan, powertune, and clock setting options are accepted, as the configuration routine was ripped from my own full-custom miner, but they do nothing.

# hyc's additions (Linux only)

Use a GPU index of `-1` to run on the CPU. The only other config item needed is "threads",
but `rawintensity` and `worksize` must still be set to a non-zero value.

As with the original CPU miner, you can gain a performance boost by configuring huge pages.
Check current setting with `sysctl vm.nr_hugepages` then set it to at least 3 times the
total number of threads you're using, as root.

    sudo sysctl -w vm.nr_hugepages=num

Also, it can run faster as root, which allows it to use mlock.

# Solo mining

Use a URL of "daemon+tcp://<host>:<port>" - requires bitmonerod v0.9.3.1 or newer

# Building

## Ubuntu 14.04

gcc 5 or newer is required.

### Installing dependencies

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y && \
sudo apt-get update && \
sudo apt-get install gcc-6 g++-6 libjansson-dev -y && \
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ g++ /usr/bin/g++-6
```

### Building and running

```
make
./miner xmr.conf
```

Donations
=========
Donations for the work done in this fork are accepted :

* BTC: `128qLZCaGdoWhBTfaS7rytpbvG4mNTyAQm`
* XMR: `46FkYo7x6LqYjLQo4Jd84UTGBybW7tsWqJaQVLPhbUSK19ajSTMY9T2Sa2LH6CfWhSingjvQARtfeM4Feekpp2yFR1wsFNT`
* AEON: `Wmtm4S2cQ8uEBBAVjvbiaVAPv2d6gA1mAUmBmjna4VF7VixLxLRUYag5cvsym3WnuzdJ9zvhQ3Xwa8gWxPDPRfcQ3AUkYra3W`

Credits
=======
wolf-multi-miner was forked from Wolf9466's wolf-xmr-miner.
* [Wolf9466](https://github.com/wolf9466)
* [hyc](https://github.com/hyc)

