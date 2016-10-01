# windows php7 environment

## existing windows dll

+ all http://windows.php.net/downloads/pecl/releases/
+ mongodb http://windows.php.net/downloads/pecl/releases/mongodb/1.1.2/php_mongodb-1.1.2-7.0-ts-vc14-x64.zip

## build missing extensions

environment x64 VC14 VisualStudio onwn compiled (steps see http://stackoverflow.com/questions/10084493/compiling-a-php-extension-as-non-thread-safe)

    // Windows Developer Console (x64)
    "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64

    nmake clean
    buildconf --force
    configure --with-all-shared --disable-all --enable-cli ...
    nmake
    
    // Option für NTS 
    --disable-zts   

### memcache

source: https://github.com/php/pecl-caching-memcache

    nmake clean
    buildconf
    configure --with-all-shared --disable-all --enable-cli --enable-memcache
    nmake 
    
### memcached

memcached doesn´t work with windows, because memcached.lib doesn´t work with windows.

### ssh2

source: https://github.com/php/pecl-networking-ssh2


    nmake clean
    buildconf
    configure --with-all-shared --disable-all --enable-cli --with-ssh2 --with-openssl
    nmake
    
    
# see

+ https://wiki.php.net/internals/windows/stepbystepbuild
+ http://windows.php.net/downloads/php-sdk/
+ https://msdn.microsoft.com/en-us/library/ff660764(v=vs.100).aspx
+ http://stackoverflow.com/questions/10084493/compiling-a-php-extension-as-non-thread-safe
