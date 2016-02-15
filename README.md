# Robocup

## Setting up the environment
1. Install newest version of Xubuntu (here: 15.10 64-bit) in a virtual machine. You can also install any other versions Ubuntu or Linux system, but Xubuntu is very small and leightweight.


You have to be logged in as root to run the following commands (or you use sudo)!


2. Update /etc/apt/sources.list to... (Optional, but recommended)
    ```bash
    ###### Ubuntu Main Repos
    deb http://de.archive.ubuntu.com/ubuntu/ wily main restricted universe multiverse
    deb-src http://de.archive.ubuntu.com/ubuntu/ wily main restricted universe multiverse

    ###### Ubuntu Update Repos
    deb http://de.archive.ubuntu.com/ubuntu/ wily-security main restricted universe multiverse
    deb http://de.archive.ubuntu.com/ubuntu/ wily-updates main restricted universe multiverse
    deb http://de.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
    deb-src http://de.archive.ubuntu.com/ubuntu/ wily-security main restricted universe multiverse
    deb-src http://de.archive.ubuntu.com/ubuntu/ wily-updates main restricted universe multiverse
    deb-src http://de.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
    ```

3. Add PPA for a newer version of git
    ```bash
    add-apt-repository ppa:git-core/ppa
    ```

4. Update current system
    ```bash
    apt update && apt upgrade -y
    ```

5. Install packages which we will need later
    ```bash
    apt install -y linux-headers-generic git git-core ssh openssh-client openssh-server flex libboost-all-dev gcc g++ make build-essential libpng-dev python-gobject-dev libfontconfig1-dev libfreetype6-dev libxrender-dev libxi-dev libxt-dev libaudio-dev libqt4-dev
    ```

6. Install VirtualBox Guest Additions

7. Restart the system

8. Login into your account and start a terminal

9. In your terminal login as root. You have to type in the password of your user account.
    ```bash
    sudo -i
    ```

10. Change current directory to /root
    ```bash
    cd /root
    ```

11. Download additional component we need for compiling the Robocup server and monitor
    ```bash
    wget http://ftp.gnu.org/gnu/bison/bison-2.7.1.tar.gz
    ```

12. Extract it and switch into the directory
    ```bash
    tar xfvz bison-2.7.1.tar.gz && cd bison-2.7.1
    ```

13. Compile bison and install it
    ```bash
    ./configure && make && make install && cd /root
    ```

After we set up the environment, we can compile the Robocup software.

### Compiling Robocup server
14. Download Robocup server
    ```bash
    wget http://heanet.dl.sourceforge.net/project/sserver/rcssserver/15.2.2/rcssserver-15.2.2.tar.gz
    ```

15. Extract it and switch into the directory
    ```bash
    tar xfvz rcssserver-15.2.2.tar.gz && cd rcssserver-15.2.2
    ```

16. Compile the server software and install it
    ```bash
    ./configure --prefix=/ --exec-prefix=/ --with-boost-libdir=/usr/lib/x86_64-linux-gnu/ && make && make install && cd /root
    ```

### Compiling Robocup monitor
17. Download Robocup monitor
    ```bash
    wget http://heanet.dl.sourceforge.net/project/sserver/rcssmonitor/15.1.1/rcssmonitor-15.1.1.tar.gz
    ```

18. Extract it and switch into the directory
    ```bash
    tar xfvz rcssmonitor-15.1.1.tar.gz && cd rcssmonitor-15.1.1
    ```

19. Compile the monitor software and install it
    ```bash
    ./configure --prefix=/ --exec-prefix=/ --with-boost-libdir=/usr/lib/x86_64-linux-gnu/ && make && make install && cd /root
    ```

### Starting
20. To start the Robocup server software start a terminal and run... (You need to run it twice because the first time it will crash or what ever)
    ```bash
    rcssserver
    ```

21. To start the Robocup monitor software start another terminal and run...
    ```bash
    rcssmonitor
    ```

READY!
