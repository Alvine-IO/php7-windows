# windows php7 environment

## existing windows dll

+ mongodb http://windows.php.net/downloads/pecl/releases/mongodb/1.1.2/php_mongodb-1.1.2-7.0-ts-vc14-x64.zip

## build missing pecl extensions

environment x64 VC14 VisualStudio onwn compiled (steps see http://stackoverflow.com/questions/10084493/compiling-a-php-extension-as-non-thread-safe)

    // Windows development Console
    "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\amd64\vcvars64.bat"

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
    configure ^
    --with-all-shared ^
	--disable-all ^
	--enable-cli  ^
        --enable-memcache
    nmake 
    
### memcached

source: https://github.com/php-memcached-dev/php-memcached

### ssh2

source: https://github.com/php/pecl-networking-ssh2


    nmake clean
    buildconf
    configure ^
    --with-all-shared ^
	--disable-all ^
	--enable-cli  ^
        --with-ssh2 ^
	--with-openssl
    nmake
    
    
    
# see

+ https://wiki.php.net/internals/windows/stepbystepbuild
+ http://windows.php.net/downloads/php-sdk/
+ https://msdn.microsoft.com/en-us/library/ff660764(v=vs.100).aspx
+ http://stackoverflow.com/questions/10084493/compiling-a-php-extension-as-non-thread-safe
