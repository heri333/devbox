# Introduction

Simple project of a complete pipeline to setup a Java developer VM with
* Unattended install of a minimal Xubuntu system
* Theme customization
* Installation of tools with custom settings
* Installation of a Java development environment including OpenJDK, OpenJ9, GraalVM with native image, IntelliJ IDEA

# Running

Create a file ` vars.json` with the mandatory variables:

    {
      "git_email": "<your_email>"
    }

Run packer

    packer build -on-error=ask -force -var-file vars.json -var-file packer/xubuntu-19.04.json packer/xubuntu.json

# Notes
* If you want to run the Ansible roles to setup a real machine, you may want to skip settings which are targeted to
VM setups (like disabling lock screen and power management) with `--skip-tags "vm"`
* If you are behind a proxy, set `d-i mirror/http/proxy` accordingly in `preseed/default.cfg`

