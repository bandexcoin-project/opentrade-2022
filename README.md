Credits to bandexcoin-project, we restored all needed files for running this exchange software.
visit our site here
[**https://bandexcoin.com**](http://bandexcoin.com)
# OpenTrade
OpenTrade is an open source OEMS, and algorithmic trading platform, designed for simplicity, flexibility and performance. 

# Features:
* Built on C++17
* Strictly follows [Google C++ Style Guild](https://google.github.io/styleguide/cppguide.html)
* Multi-level account functionality
* Super simple API interfaces for market data adapter, exchange connectivity and execution/alpha algo
* Multi-source market data support, e.g., different FX pricing sources
* Pre-trade risk limits on multi-level accounts
* Post-trade risk integrated with [OpenRisk](https://github.com/opentradesolutions/openrisk)
* [Multi-theme web frontend](http://demo.opentradesolutions.com)
* Fully thread-safe design, everything can be modified during runtime, e.g., reload symbol list, modify tick size table, lot-size, exchange timezone and trading/break period etc.
* Built-in execution simulator
* Simple configuration

# Steps to run on Ubuntu 18.04
* **Compile**
  * Prepare dev environment.
  ```bash
  sudo apt update \
  && sudo apt install -y \
    g++  \
    make \
    cmake \
    clang-format \
    clang \
    python \
    python-dev \
    vim \
    exuberant-ctags \
    git \
    wget \
    libssl-dev \
    libboost-program-options-dev \
    libboost-system-dev \
    libboost-date-time-dev \
    libboost-filesystem-dev \
    libboost-iostreams-dev \
    libsoci-dev \
    libpq-dev \
    libquickfix-dev \
    libtbb-dev \
    liblog4cxx-dev
  ```
  * Build
  ```bash
  sudo adduser opentrade
  usermod -aG sudo opentrade
  su opentrade
  cd  
  git clone https://github.com/bandexcoin-project/opentrade-2022
  mv opentrade-2022 opentrade
  cd opentrade
  make debug
  ```
  
 * **Setup database**
   ```bash
   sudo apt remove --purge postgres*
   sudo apt autoremove
   sudo apt install -y postgresql-10 postgresql-contrib postgresql-client
   wget https://github.com/bandexcoin-project/data-1/raw/master/opentrade-pg_dumpall.sql
   sudo -u postgres psql -f opentrade-pg_dumpall.sql postgres
   ```
 
 * **Run opentrade**
   * Download tick data files
   ```bash
   cd opentrade
   wget https://github.com/bandexcoin-project/data-1/raw/master/bbgids.txt
   wget https://bandexcoin.com/downloads/ticks.txt
   ```
   * Run
   ```Bash
   cp opentrade.conf-example opentrade.conf
   ./opentrade
   ```
   
 * **Open Web UI**
   ```
   # username/password: test/test
   http://localhost:9111
   ```
   
# The other OS system
  we prepared [Dockfile-dev](https://raw.githubusercontent.com/opentradesolutions/opentrade/master/Dockfile-dev) for you. (don't found this file back yet on the internet)
