# Day 19 - Linux Filesystem Structure

**Date:** 26 January,2026

---

## Why i need to know this

Every time i land on a linux machine during an assessment, knowing
where things live tells me where to look. config files, binaries,
user data, boot files — its all in specific places and its always
the same. learn the structure once and it applies everywhere.

---

## The directories that matter

**`/bin`**
Contains all the basic binaries and executables that every user
needs. things like ls, cp, mv, cat. the commands you run daily
all live here.

**`/sbin`**
System binaries. same idea as /bin but these are for root or the
superuser. mount, deluser, system administration stuff.
normal users technically cant run most of these without sudo.

**`/lib`**
Shared libraries for the binaries in /bin and /sbin. think of
these as dependencies — the executables need them to actually run.

**`/usr`**
Has its own bin and sbin inside it. the difference is these arent
essential for the operating system itself — theyre essential for
the user. most of the software you install ends up here.
also contains a local directory for locally compiled software.

**`/etc`**
This is the one i care about most from a pentesting perspective.
all the text-based configuration files live here. ssh config,
apache config, user password hashes (/etc/shadow), cron jobs —
if you want to understand how a system is configured, you start here.

**`/home`**
Each user on the system gets their own directory here. user data,
personal files, shell history, ssh keys — all stored under
/home/username. when i get access to a machine, /home is one of
the first places i check.

**`$PATH`**
Not a directory but worth noting here. PATH tells the OS where to
look for executables when you type a command. if PATH is misconfigured
or writable, thats a privesc vector — you can drop a malicious binary
earlier in the PATH and get it executed instead of the real one.

**`/boot`**
Contains files needed to boot the system. kernel, bootloader config.
not usually interesting for pentesting unless youre doing something
very specific.

**`/dev`**
Device files. disks, partitions, terminals — everything is treated
as a file in linux. /dev/sda is your first hard drive. /dev/null is
the void you pipe things into when you dont want output.

**`/opt`**
Optional addon software. third party applications that arent part
of the default package manager often install here. worth checking
on a target — software installed manually is often less maintained
and more likely to be outdated.

---

## From a pentesting angle

The directories i check first after getting a foothold:
```bash
cat /etc/passwd          # list all users
cat /etc/shadow          # password hashes (needs root)
ls /home                 # see what users exist
cat /etc/crontab         # scheduled tasks running as root
ls -la /opt              # third party software
echo $PATH               # check for path hijack opportunities
find / -perm -4000 2>/dev/null   # find SUID binaries
```

Knowing where everything lives means i spend less time guessing
and more time actually finding things worth exploiting.

---

## What i want to practice

- Navigating a linux filesystem quickly without getting lost
- Finding sensitive files using find and locate
- Understanding file permissions and what they mean
