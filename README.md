# Ansible weareinteractive.git role

[![Build Status](https://img.shields.io/travis/weareinteractive/ansible-git.svg)](https://travis-ci.org/weareinteractive/ansible-git)
[![Galaxy](http://img.shields.io/badge/galaxy-weareinteractive.git-blue.svg)](https://galaxy.ansible.com/weareinteractive/git)
[![GitHub Tags](https://img.shields.io/github/tag/weareinteractive/ansible-git.svg)](https://github.com/weareinteractive/ansible-git)
[![GitHub Stars](https://img.shields.io/github/stars/weareinteractive/ansible-git.svg)](https://github.com/weareinteractive/ansible-git)

> `weareinteractive.git` is an [Ansible](http://www.ansible.com) role which:
>
> * installs git
> * configures git
> * manages repositories

**Note:**

> Since Ansible Galaxy switched all role names to the organization name, this role has moved from `weareinteractive.git` to `weareinteractive.git`!

## Installation

Using `ansible-galaxy`:

```shell
$ ansible-galaxy install weareinteractive.git
```

Using `requirements.yml`:

```yaml
- src: weareinteractive.git
```

Using `git`:

```shell
$ git clone https://github.com/weareinteractive/ansible-git.git weareinteractive.git
```

## Dependencies

* Ansible >= 2.4

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
---
# For more information about default variables see:
# https://docs.ansible.com/ansible/latest/modules/git_module.html
#
# git_config:
#   color:
#     branch: auto
#     diff: auto
#     interactive: auto
#     status: auto
#   push:
#     default: matching
#  git_repositories:
#    - accept_hostkey: ...
#      bare: ...
#      clone: ...
#      depth: ...
#      dest: ...
#      force: ...
#      key_file: ...
#      recursive: ...
#      reference: ...
#      refspec: ...
#      remote: ...
#      repo: ...
#      ssh_opts: ...
#      track_submodules: ...
#      pull: ...
#      version: ...
#      mode: ...
#      owner: ...
#      group: ...
#

# define package (version)
git_package: git-core
# git global configuration settings
git_config: {}
# list of repositories (http://docs.ansible.com/git_module.html)
git_repositories: []
# optional ssh private key to copy to `/etc/ssh/ssh_git.key`
# and be used as default `git_key_file`
git_key:
# optional default key file to use for git operations
git_key_file:
# optional default accept host key to use for git operations (yes | no)
git_accept_hostkey: no
# optional default update to use for git operations (yes | no)
git_pull: yes
# optional default repository mode
git_mode:
# optional default repository owner
git_owner:
# optional default repository group
git_group:

```


## Usage

This is an example playbook:

```yaml
---

- hosts: all
  become: yes
  roles:
    - weareinteractive.git
  vars:
    git_config:
      color:
        diff: auto
        branch: auto
        status: auto
        interactive: auto
      push:
        default: matching
    git_repositories:
      - repo: https://github.com/weareinteractive/ansible-git.git
        dest: /tmp/weareinteractive.git

```


## Testing

```shell
$ git clone https://github.com/weareinteractive/ansible-git.git
$ cd ansible-git
$ make test
```

## Contributing
In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

*Note: To update the `README.md` file please install and run `ansible-role`:*

```shell
$ gem install ansible-role
$ ansible-role docgen
```

## License
Copyright (c) We Are Interactive under the MIT license.
