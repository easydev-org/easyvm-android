# easyvm-android

Walkthroughs and CI for **Android-x86** guests, driven by
[`easydev-org/easyvm`](https://github.com/easydev-org/easyvm).

## What lives here

`blissos16/steps/` - the `.walk` files for `install`, `launch` and `vm-configure`, plus the reference
images they compare against.

Android is its own name rather than its own machine: an INSTALLED Android-x86 disk boots through UEFI
and GRUB like any Linux guest. What differs is the INSTALLER, which is started with `-kernel` and
`-initrd` out of the ISO, and the video adapter, which has to provide a DRM node.

```sh
gh workflow run blissos16.yml -f disks_repository=easydev-org/easyvm-android -f from_tag=android-blissos16
```

## What lives elsewhere, on purpose

The **engine** and the **CI machinery** are both in `easydev-org/easyvm`; this workflow calls
`easydev-org/easyvm/.github/workflows/stage.yml@main` for the second.

Disks pull from and publish to this repository's own ghcr package, `easydev-org/easyvm-android`.
