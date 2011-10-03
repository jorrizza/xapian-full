Sup and Xapian for OpenBSD
==========================

This fork only works for those who want to run [sup][1] on OpenBSD or something similar with xapian-full.

Here's a short howto to get sup running on 4.9. `#` indicates a root shell and `$` indicates your user's shell.
The reason we're using gem, and not bundler is that Ruby's mkmf generates a Makefile that tries to install binaries as root.
This results in ncursesw being uninstallable as a normal user.

    # pkg_add ruby-1.9.2.136p0 e2fsprogs-1.41.4p4
    $ git clone git://github.com/jorrizza/xapian-full.git
    $ C_INCLUDE_PATH=/usr/local/include
    $ CPLUS_INCLUDE_PATH=$C_INCLUDE_PATH
    $ LIBRARY_PATH=/usr/local/lib
    $ export C_INCLUDE_PATH CPLUS_INCLUDE_PATH LIBRARY_PATH
    $ cd xapian-full && gem build
    # gem install xapian-full/xapian-full-1.2.3.gem
    # gem install sup
    $ cat >> ~/bin/locale
    #!/bin/sh
    echo "UTF-8"
    ^D
    $ chmod +x ~/bin/locale
    $ sup19

TODO: IT CRASHES! WTF!
----------------------

    <internal:lib/rubygems/custom_require>:29:in `require': Cannot load specified object - /usr/local/lib/ruby/gems/1.9.1/gems/xapian-full-1.2.3/lib/_xapian.so (LoadError)

[1]: http://sup.rubyforge.org/
