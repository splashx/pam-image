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

1. Copy elements/ directory to disk-image-builder/elements/
  ```bash
      cp -R elements/* ../diskimage-builder/elements/
  ```

1. Call the following command to create cloud image is able to run on OpenStack:
  ```bash
       disk-image-create base vm ssh sss ubuntu selinux-permissive root-passwd -o ubuntu_pam
  ```
