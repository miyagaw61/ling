# ling - LinuxKernel GLOBAL

## Prepare

make linux kernel tag files directory

```
$ mkdir linux_kernel_tagfiles # any name
$ cd linux_kernel_tagfiles/
$ export LINUX_TAGS_DIR=$PWD
```

make kernel version directory

```
$ mkdir v4.15 # any version
```

make linux kernel tag files and copy it to LINUX_TAGS_DIR

```
$ cd linux.git
$ gtags -v
$ cp -a G* $LINUX_TAGS_DIR/v4.15/
```

## Usage

```
Usage: ling [global-options...] [version=<kernel_version>]
```

## Example

```
$ uname -r
5.0.0-stock

$ ling -x set_normalized_timespec
set_normalized_timespec  403 kernel/time/time.c void set_normalized_timespec(struct timespec *ts, time_t sec, s64 nsec)

$ ling -x set_normalized_timespec version=5.0
set_normalized_timespec  403 kernel/time/time.c void set_normalized_timespec(struct timespec *ts, time_t sec, s64 nsec)

$ ling -x set_normalized_timespec version=4.15
set_normalized_timespec   31 include/linux/time32.h # define set_normalized_timespec    set_normalized_timespec64
set_normalized_timespec  425 kernel/time/time.c void set_normalized_timespec(struct timespec *ts, time_t sec, s64 nsec)
```
