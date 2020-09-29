# manjaro-chrootbuild

```
Usage: chrootbuild [options]
     -b <branch> Branch to use (unstable/testing/stable-staging/stable;
                                arm-unstable/arm-testing/arm-stable)
                                default: arm-unstable)
     -c          Start with clean chroot fs
     -i <pkg>    Install local package (specify full path!)
     -l <list>   List to build
     -n          Install built pkg to chroot fs (default when building lists)
     -p <pkg>    Package to build
     -r          Remove previously built packages in $PKGDEST
     -s          Sign package(s)
```

Host package cache is used by default.

PKGDEST and GPGKEY are read from host's `/etc/makepkg.conf` and/or (with precedence) the user's `~/.makepkg.conf`

If PKGDEST isn't defined, package will be moved to current work directory.

`<package>` names may be used with trailing slashes.

`Lists` must be present in the work directory as `<list>.list` together with a directory named `<list>`, containing all PKGBUILD-repos specified in `<list>.list`. Commenting list entries with `#` is supported.

### todo:
- check options
- more error handling
- collect multiple packages and lists in arrays
