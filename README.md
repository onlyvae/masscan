# Static Building

Download the compile tool chain based on musl from https://toolchains.bootlin.com/

    # armv7
    wget https://toolchains.bootlin.com/downloads/releases/toolchains/armv7-eabihf/tarballs/armv7-eabihf--musl--stable-2022.08-1.tar.bz2

    # x86-64
    wget https://toolchains.bootlin.com/downloads/releases/toolchains/x86-64/tarballs/x86-64--musl--stable-2022.08-1.tar.bz2


Download and build libpcap

    wget https://www.tcpdump.org/release/libpcap-1.10.4.tar.gz
    tar xvf libpcap-1.10.4.tar.gz
    
    cd libpcap-1.10.4/
    export CC="/path/x86-64--musl--stable-2022.08-1/bin/x86_64-linux-gcc"
    ./configure --host=$($CC -dumpmachine)
    make

Download masscan in the same directory with libpcap and static build masscan.

    git clone https://github.com/onlyvae/masscan.git

    cd masscan
    export CC="/path/x86-64--musl--stable-2022.08-1/bin/x86_64-linux-gcc"
    make
    strip bin/masscan

# Referrence
https://github.com/robertdavidgraham/masscan/commit/e2e997331d07659f9f2fb05cd57f69f623618433?diff=split