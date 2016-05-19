Diskimage-builder tools for creation cloud images
=================================================

Steps how to create cloud image with OpenSSH acting as a Privilege Account Mananger installed using diskimage-builder project:

1. Clone the repository "https://github.com/openstack/diskimage-builder" locally.

  ```bash
  git clone https://github.com/openstack/diskimage-builder ~/diskimage-builder
  ```

1. Add ~/diskimage-builder/bin/ directory to your path

  ```bash
  export PATH=$PATH:/home/$USER/diskimage-builder/bin/
  ```

1. Export the elements path env variable to .bashrc and source it.
  ```bash
  cat ELEMENTS_PATH=/home/$USER/diskimage-builder/elements/ >> ~/.bashrc
  source ~/.bashrc
  ```

1. Get the pam-image elements and copy then to directory disk-image-builder/elements/
  ```bash
  git clone https://github.com/splashx/pam-image ~/pam-image
  cp -R ~/pam-image/elements/* ~/diskimage-builder/elements/
  ```

1. Call the following command to create cloud image is able to run on OpenStack:
  ```bash
  disk-image-create base vm ubuntu selinux-permissive root-passwd ssh sss -o ubuntu_pam
  ```

Note
====
* The elements `base`, `vm`, `ubuntu`, `selinux-permissive` are the standard elements provided by [diskimage-builder](https://github.com/openstack/diskimage-builder).
* The elements `root-passwd`, `ssh` and `sss` are provided by this repo.
