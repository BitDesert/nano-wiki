# Building on OSX
* Install QT5

## Required source
* Boost 1.55 extracted to [boost.src]
* Googletest 1.7 extracted to [gtest.src]
* LevelDB extracted to [leveldb.src]
* cryptopp extracted to [cryptopp.src]
* cpp-netlib extracted to [cppnetlib.src]
* mu_coin source in [mu_coin_source]

## Build cmake
* Inside [cmake.build]
* Run "[cmake.src]/configure --prefix=[cmake]"
* Run "make"
* Run "make install"

## Build Boost
* Inside [boost.src]
* Run "./bootstrap.sh
* Run "./b2 --prefix=[boost] link=static install"

## Build leveldb
* Inside [leveldb.src]
* Run "make"

## Build Googletest
* Inside directory [gtest.build]
* Run "[gtest.src]/configure"
* Run "make"

## Build cryptopp
* Inside directory [cryptopp.src]
* Run "make"
* Run "make install PREFIX=[cryptopp]"

## Build mu_coin
* Inside directory [mu_coin.build]
* Run "../cmake-3.0.1/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562 -D LevelDB_LIBRARY:FILEPATH=/Users/colin/Desktop/leveldb-1.15.0.src/libleveldb.a -D LevelDB_INCLUDE_PATH:PATH=../leveldb-1.15.0.src/include -D BOOST_ROOT:PATH=../boost_1_56 -D Qt5_DIR=../../Qt/5.3/clang_64/lib/cmake/Qt5 ../mu_coin"