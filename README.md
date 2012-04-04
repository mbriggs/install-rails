# Installing Rails

Installing rails can be quite daunting for a beginner, and there is a good deal of bad documentation on the internet just waiting to trip you up. This is a simple, step by step guide to help you through the process.

Before starting, please get rid of any existing attempts to install rails (via apt, macports, etc). The methods provided will work, and are the preferred way that experienced rails developers use to get rails up and running on a machine.

# Installing Rails on OSX

OSX is the operating system of choice for both ruby and rails developers. Support is excellent, and it should be easy to find help with any os specific problems you may encounter due to the fact that most of the community is using this operating system.

### 1. Install GCC Toolchain

GCC is an extremely popular C compiler that we will use to build ruby (and that ruby will use to build libraries that have C dependancies in the future).

If you are planning on doing any iOS/OSX development, your best choice is to just get it with XCode (the IDE for everything Apple). It can be downloaded for free off of the appstore, although it is quite a large download, so this can take some time.

Once it is installed, launch the application, and open its preferences (in the XCode menu, or press cmd-,). Click on the "Downloads" tab, and press the button that says "Install" next to "Command Line Tools"

If you do not plan on developing anything on Apples platforms, you can opt for the _much_ smaller GCC installer for OSX, which can be found here https://github.com/kennethreitz/osx-gcc-installer.

Once you have installed gcc, you can make sure it is accessible by opening a new terminal, and entering `gcc -v`. You should see something resembling the following snippet

```bash
 % gcc -v
Using built-in specs. Target: i686-apple-darwin11 Configured with: /private/var/tmp/llvmgcc42/llvmgcc42-2336.9~22/src/configure --disable-checking --enable-werror --prefix=/Applications/Xcode.app/Contents/Developer/usr/llvm-gcc-4.2 --mandir=/share/man --enable-languages=c,objc,c++,obj-c++ --program-prefix=llvm- --program-transform-name=/^[cg][^.-]*$/s/$/-4.2/ --with-slibdir=/usr/lib --build=i686-apple-darwin11 --enable-llvm=/private/var/tmp/llvmgcc42/llvmgcc42-2336.9~22/dst-llvmCore/Developer/usr/local --program-prefix=i686-apple-darwin11- --host=x86_64-apple-darwin11 --target=i686-apple-darwin11 --with-gxx-include-dir=/usr/include/c++/4.2.1 Thread model: posix gcc version 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2336.9.00)
```

### Installing Homebrew

Homebrew is a tool for easily downloading and building libraries that you will need as a developer on OSX. You can install it with the following command

```bash
/usr/bin/ruby -e "$(/usr/bin/curl -fksSL
https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)" 
```

To see that homebrew installed, try running the `brew` command. You should see something that looks like the following snippet

```bash
 % brew
 Example usage:
   brew install FORMULA...
   brew uninstall FORMULA...
   brew search [foo]
   brew list [FORMULA...]
   brew update
   brew upgrade [FORMULA...]
   brew [info | home] [FORMULA...]

 Troubleshooting:
   brew doctor
   brew install -vd FORMULA
   brew [--env | --config]

 Brewing:
   brew create [URL [--no-fetch]]
   brew edit [FORMULA...]
   open https://github.com/mxcl/homebrew/wiki/Formula-Cookbook

Further Help:
  man brew
  brew home
```

### Installing Ruby

Most Rubyists use a tool called RVM (Ruby Version Manager) to install their ruby. The goal of the project is to allow one to switch between rubies easily, but it also has a set of very well maintained build scripts for the various versions of ruby on various operating systems.

To install rvm, run the following command in a new terminal 

```bash
bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)
```

This will download and set up rvm for you. You should see some notes from wayne on how to use rvm show up on your screen. One of the notes will tell you to paste a line into your `.bashrc` file, which is required.

You can see that rvm is installed correctly by running `rvm -v`, which should show something like this

```bash
rvm 1.10.3 by Wayne E. Seguin <wayneeseguin@gmail.com>, Michal Papis <mpapis@gmail.com> [https://rvm.beginrescueend.com/]
```

Now that you have rvm, ruby is simple to install

```bash
rvm install 1.9.3
## -- rvm will download and compile ruby -- ##
rvm 1.9.3 --default # switch to the new ruby, and make it your default
ruby -v # you should see something like "ruby 1.9.3p125 (2012-02-16 revision 34643) [x86_64-darwin11.3.0]"
```

### Installing Rails

Now that we have ruby, we will install rails the same way we install any ruby library -- with the `gem` command

```bash
gem install rails
```

To see that rails is working, create a new project

```bash
rails new test-my-rails # create a new directory with a full rails setup
cd test-my-rails
bundle install # install all the project dependancies specified by your Gemfile
rails server # start the rails server
```

Assuming all of that happened without error, open a browser and enter `http://localhost:3000`. You should see a page welcoming you to rails.

Congratulations! You have a full rails development set up :)
