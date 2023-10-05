# JetPorch Examples

This repository contains some examples and guides I wrote to learn and test out [JetPorch](https://www.jetporch.com), a fast and robust infrastructure automation tool.

## Installing JetPorch

Currently, JetPorch is in 'Tech Preview' release, so no official packages are available. You need to [follow the source install directions](https://www.jetporch.com/basics/installing-from-source) to install JetPorch on your control machine.

On my Mac, that meant:

  1. Install Rust: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
  1. Install dependencies: `brew install gcc openssl`
  1. Clone JetPorch: `git clone https://github.com/jetporch/jetporch.git`
  1. Build JetPorch: `cd jetporch && make`
  1. Add the `jetp` binary to your `$PATH` so you can execute it: `export PATH=$PATH:$(pwd)/target/release/`

> Note: If you get an error like `command not found: cargo` when you build JetPorch, make sure you have added `~/.cargo/bin` to your `$PATH`.

Test to make sure JetPorch is working:

```
$ jetp --version

┌─────┬─────────────────────────────────────────────┐
│jetp │http://www.jetporch.com/                     │
│     │(C) Michael DeHaan + contributors, 2023      │
│     │                                             │
│build│79de310f5dfd0d0ab8e30171ed411b9919e4b366@main│
│     │Thu Oct  5 07:52:19 CDT 2023                 │
├─────┼─────────────────────────────────────────────┤
│     │usage: jetp <MODE> [flags]                   │
└─────┴─────────────────────────────────────────────┘
```

## Setting up test VMs

TODO: See [this comment](https://github.com/geerlingguy/ansible-for-devops/issues/404#issuecomment-1747846798).

### UTM

Currently the easiest way to get a local Linux VM up and running with SSH access from the host on my Mac is via UTM.

Assuming you have [Homebrew installed]() and have a copy of the [Ubuntu 22.04 Server for arm64 ISO](), here are the steps to build a VM for JetPorch testing:

  1. `brew install --cask utm`
  1. Link the `utmctl` CLI utility somewhere you can use it: `sudo ln -sf /Applications/UTM.app/Contents/MacOS/utmctl /usr/local/bin/utmctl`
  1. Open UTM, create a new VM, and select the Ubuntu Server ISO.
  1. Follow the Ubuntu server setup wizard and get it set up with a user account you'd like to use.
  1. Once installation is complete, make sure you eject the ISO and reboot.

Note: Currently sudo password support is missing in JetPorch. For now, you need to run `visudo` and make sure the user account you're using for access has passwordless sudo enabled.

On an Ubuntu system, this means you need to run `visudo` and make sure the `%sudo` line looks like:

```
%sudo  ALL=(ALL) NOPASSWD:ALL
```

Run the command `ip a` to find the IP address of your UTM Linux VM, and use that in your inventory file to connect to the VM. (In my case, `192.168.64.3`.)

## License

GPLv3 or later

## Author

[Jeff Geerling](https://www.jeffgeerling.com), author of [JetPorch Automation](https://www.jetporchautomation.com).
