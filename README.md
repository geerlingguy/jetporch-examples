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

Note: Currently sudo password support is missing in JetPorch. For now, you need to run `visudo` and make sure the user account you're using for access has passwordless sudo enabled.

On an Ubuntu system, this means ensuring the `%sudo` line looks like:

```
%sudo  ALL=(ALL) NOPASSWD:ALL
```

## License

GPLv3 or later

## Author

[Jeff Geerling](https://www.jeffgeerling.com), author of [JetPorch Automation](https://www.jetporchautomation.com).
