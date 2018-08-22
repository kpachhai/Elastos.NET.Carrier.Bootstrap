# Elastos Carrier Boostrap Daemon

## Summary

Elastos Carrier boostrap daemon is a basic service to help new node join and bootstrap the Elastos Carrier network.

## Build from source

### GNU/Linux

Currently, **GNU/Linux is the only recommend platform** to run the Elastos carrier boostrapd officially.

#### 1. Install Pre-requirements

Run the following commands to install all pre-requirements.

```shell
$ sudo apt-get update
$ sudo apt-get install build-essential autoconf automake autopoint libtool bison texinfo
```

#### 2. Build

Change to the directory `$(SRC_DIR)/build`, and run the following commands:

```shell
$ mkdir linux
$ cd linux
$ cmake -DCMAKE_INSTALL_PREFIX=outputs ../..
$ make install
```

To build Debian (.deb) package, run command with `"dist"` option:

```shell
$ make dist
```

The generated Debian package will be located at current working directory, can can use the command to locate it:

```shell
$ ls -la *.deb
```

#### 3. Deployment & Run

Recommended target platform: **Ubuntu server 16.04 LTS / x86_64**

Copy generated Debian package (.deb file) to target machine. Then run following command to install Elastos Carrier bootstrap daemon:

```shell
$ sudo dpkg -i /path/to/elastos_bootstrapd.deb
```

After install complete, the bootstrap deamon will start automatically. You can run:

```shell
$ sudo systemctl status ela-bootstrapd
```

to check the service status. If the deamon started successful, the status should be **active (running)**.

Reference: [Man page for systemctl](https://www.freedesktop.org/software/systemd/man/systemctl.html).

***NOTICE:*** 

After installed Elastos Carrier bootstrap deamon, you should modify `/etc/elastos/bootstrapd.conf`, update the **bootstrap_nodes** section according your deployment.

### MacOS

You can also develop Elastos Carrier boostrapd on MacOS for testing or debugging purpose.

#### 1. Install Pre-requirents

You need to install the following utility packages on your MacOS before build.

```
autoconf automake libtool shtool pkg-config gettext
```

Or, you can use `brew` command to install the packages:

```
brew install autoconf automake libtool shtool pkg-config gettext
```

#### 2. Build

Change to directory `$(SRC_DIR)/build`, and run the following commands:

```
$ mkdir macos
$ cd macos
$ cmake -DCMAKE_INSTALL_PREFIX=outputs ../..
$ make install
```

After that, you can run the following commands to run **ela-bootstrapd** to boost the bootstrap node as long as finishing certian configurations:

```shell
$ cd outputs/usr/bin
$ ./ela-bootstrapd --config=../../etc/elastos/bootstrapd.conf --foreground
```

#### 3. Deployment

Elastos Carrier bootstrap daemon currently not support deploy on MacOS.

## Thanks

Sincerely thanks to all teams and projects that we relies on directly or indirectly.

## License

MIT
