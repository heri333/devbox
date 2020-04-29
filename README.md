# Introduction

Simple project of a complete pipeline to setup a Java developer VM with
* Unattended install of a minimal Xubuntu system
* Installation of a Java development environment including OpenJDK, OpenJ9, GraalVM with native image, IntelliJ IDEA
* Theme customization
* Installation of tools with custom settings

# Using the built image

The image is automatically built by Github and uploaded to the Vagrant Cloud as `frostcode/devbox`.
You can use the sample Vagrantfile in the `vagrant` subfolder of this repository to spin it up:

    git clone git@github.com:heri333/devbox.git
    cd devbox/vagrant
    vagrant up

# Using the Ansible roles locally

The Ansible roles used for provisioning the VM can also be used to setup a local PC (in fact I'm using them to
keep my developer PC up to date, and just add further roles for private stuff). In this case you may want to skip
settings which are targeted to VM setups (like disabling lock screen and power management) with `--skip-tags "vm"`

# Running the packer build locally

Create a file `vars.json` with the mandatory variables:

    {
      "git_email": "<your_email>"
    }

Run packer

    packer build -on-error=ask -force -var-file vars.json -var-file packer/xubuntu-20.04.json packer/xubuntu.json

## Notes
* If you are behind a proxy, set `d-i mirror/http/proxy` accordingly in `preseed/default.cfg`

