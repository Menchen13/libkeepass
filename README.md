# Introduction
libkeepass is a C++11 library for importing and exporting
[KeePass](http://keepass.info) password databases. It supports importing and
exporting from/to both the legacy KDB format, as well as the new KDBX format.

# Building
Has been changed to CMake for the build-System and conan is used to fetch the dependencies zlib and openssl.
I have not added gtest as i dont need to build/run the tests.
Note for building OpenSSL with conan and MinGW:
Beware of a known [issue](https://github.com/conan-io/cmake-conan/issues/530#event-9832106162) for the conan package.

# Using
The main library entry points are the *KdbFile* and *KdbxFile* classes. They
take care of both importing and exporting.

Example:
```cpp
keepass::Key key("password");

keepass::KdbxFile file;
std::unique_ptr<keepass::Database> db = file.Import("in.kdbx", key);

// Do some operations using the database object.

file.Export("out.kdbx", *db.get(), key);
```
