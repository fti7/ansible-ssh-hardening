# Change Log

## [4.0.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/4.0.0) (2017-04-22)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/3.2.0...4.0.0)

### Breaking Changes:

- remove support for ansible 1.9 [\#87](https://github.com/dev-sec/ansible-ssh-hardening/pull/87) ([rndmh3ro](https://github.com/rndmh3ro))
  - **Ansible 1.9 is not supported anymore**

- Change the ssh_client_ports list variable into a simple non-list variable named ssh_client_port.  [\#84](https://github.com/dev-sec/ansible-ssh-hardening/pull/84) ([fullyint](https://github.com/fullyint))
  - Before: 
  ```
    {% for port in ssh_client_ports -%}
    Port {{port}}
    {% endfor %}
  ```
  - After:
  ```
     Port {{ ssh_client_port }}
  ```

- Fix ssh config to handle custom options per Host [\#83](https://github.com/dev-sec/ansible-ssh-hardening/pull/83) ([fullyint](https://github.com/fullyint))
  - Before:
  ```
    # one or more hosts, to which ssh-client can connect to. Default is empty, but should be configured for security reasons!
    ssh_remote_hosts: []           # ssh
  ```
  - After:
  ```
    # Hosts with custom options.            # ssh
    # Example:
    # ssh_remote_hosts:
    #   - names: ['example.com', 'example2.com']
    #     options: ['Port 2222', 'ForwardAgent yes']
    #   - names: ['example3.com']
    #     options: ['StrictHostKeyChecking no']
    ssh_remote_hosts: []
  ```
---

**Implemented enhancements:**

- Use different Hostkeys according to installed ssh version [\#99](https://github.com/dev-sec/ansible-ssh-hardening/pull/99) ([rndmh3ro](https://github.com/rndmh3ro))
- Remove small dh primes [\#97](https://github.com/dev-sec/ansible-ssh-hardening/pull/97) ([rndmh3ro](https://github.com/rndmh3ro))
- Add Ed25519 SSH host key to match ssh-baseline [\#96](https://github.com/dev-sec/ansible-ssh-hardening/pull/96) ([techraf](https://github.com/techraf))
- Add support for FreeBSD OpenSSH server and client [\#95](https://github.com/dev-sec/ansible-ssh-hardening/pull/95) ([jbenden](https://github.com/jbenden))
- Defaults: Remove DSA from SSH host keys to match ssh-baseline profile [\#92](https://github.com/dev-sec/ansible-ssh-hardening/pull/92) ([techraf](https://github.com/techraf))
- make ChallengeResponseAuthentication configurable [\#85](https://github.com/dev-sec/ansible-ssh-hardening/pull/85) ([rndmh3ro](https://github.com/rndmh3ro))

**Fixed bugs:**

- SELinux-specific task still runs on SELinux-disabled systems [\#74](https://github.com/dev-sec/ansible-ssh-hardening/issues/74)
- List only one Port in ssh config [\#84](https://github.com/dev-sec/ansible-ssh-hardening/pull/84) ([fullyint](https://github.com/fullyint))
- Fix ssh config to handle custom options per Host [\#83](https://github.com/dev-sec/ansible-ssh-hardening/pull/83) ([fullyint](https://github.com/fullyint))

**Closed issues:**

- Should compression be opt-in? [\#90](https://github.com/dev-sec/ansible-ssh-hardening/issues/90)
- The role fails when conditionally included [\#86](https://github.com/dev-sec/ansible-ssh-hardening/issues/86)

**Merged pull requests:**

- remove duplicate section [\#105](https://github.com/dev-sec/ansible-ssh-hardening/pull/105) ([rndmh3ro](https://github.com/rndmh3ro))
- Fix ssh\_server\_ports and ssh\_client\_ports documentation bug [\#80](https://github.com/dev-sec/ansible-ssh-hardening/pull/80) ([kivilahtio](https://github.com/kivilahtio))

**Other improvements:**
- Accommodate missing plugins in kitchen\_vagrant\_block.rb [\#100](https://github.com/dev-sec/ansible-ssh-hardening/pull/100) ([fullyint](https://github.com/fullyint))
- Replace deprecated always\_run with check\_mode [\#93](https://github.com/dev-sec/ansible-ssh-hardening/pull/93) ([jbenden](https://github.com/jbenden))
- use new docker images [\#91](https://github.com/dev-sec/ansible-ssh-hardening/pull/91) ([rndmh3ro](https://github.com/rndmh3ro))
- use centos 7 in vagrant, limit ssh conns [\#88](https://github.com/dev-sec/ansible-ssh-hardening/pull/88) ([rndmh3ro](https://github.com/rndmh3ro))

## [3.2.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/3.2.0) (2016-10-24)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/3.1.0...3.2.0)

**Implemented enhancements:**

- CentOS 7 selinux dependencies [\#76](https://github.com/dev-sec/ansible-ssh-hardening/issues/76)
- install selinux dependencies, check for already installed semodule [\#79](https://github.com/dev-sec/ansible-ssh-hardening/pull/79) ([rndmh3ro](https://github.com/rndmh3ro))
- Parameterise Banner and DebianBanner as defaults [\#77](https://github.com/dev-sec/ansible-ssh-hardening/pull/77) ([tsenart](https://github.com/tsenart))

**Fixed bugs:**

- Some tasks are always run even if they are not needed [\#78](https://github.com/dev-sec/ansible-ssh-hardening/issues/78)
- Selinux issue [\#75](https://github.com/dev-sec/ansible-ssh-hardening/issues/75)
- Running the tests locally [\#61](https://github.com/dev-sec/ansible-ssh-hardening/issues/61)

**Closed issues:**

- Applied-Crypto-Hardening project and new cyphers. [\#28](https://github.com/dev-sec/ansible-ssh-hardening/issues/28)

## [3.1.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/3.1.0) (2016-08-03)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/3.1...3.1.0)

**Implemented enhancements:**

- use new ciphers, kex, macs and privilege separation for redhat family 7 or later [\#72](https://github.com/dev-sec/ansible-ssh-hardening/issues/72)

## [3.1](https://github.com/dev-sec/ansible-ssh-hardening/tree/3.1) (2016-08-03)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/3.0.0...3.1)

**Implemented enhancements:**

- Add Xenial / Ubuntu 16.04 LTS to meta/main.yml [\#63](https://github.com/dev-sec/ansible-ssh-hardening/issues/63)
- Use new ciphers, kex, macs and priv separation sandbox for redhat family 7 [\#73](https://github.com/dev-sec/ansible-ssh-hardening/pull/73) ([atomic111](https://github.com/atomic111))
- add docker support [\#71](https://github.com/dev-sec/ansible-ssh-hardening/pull/71) ([rndmh3ro](https://github.com/rndmh3ro))
- add always\_run: true to task. fix \#64 [\#69](https://github.com/dev-sec/ansible-ssh-hardening/pull/69) ([rndmh3ro](https://github.com/rndmh3ro))
- Debian8 [\#68](https://github.com/dev-sec/ansible-ssh-hardening/pull/68) ([rndmh3ro](https://github.com/rndmh3ro))
- Fixed KexAlgorithms Conditional Statement [\#66](https://github.com/dev-sec/ansible-ssh-hardening/pull/66) ([cjsheets](https://github.com/cjsheets))
- Moves vars to defaults [\#60](https://github.com/dev-sec/ansible-ssh-hardening/pull/60) ([conorsch](https://github.com/conorsch))

**Fixed bugs:**

- semodule ssh\_password error on AWS Centos 7 [\#64](https://github.com/dev-sec/ansible-ssh-hardening/issues/64)

**Closed issues:**

- `ssh\_server\_ports` a bit misleading in the vars section? [\#62](https://github.com/dev-sec/ansible-ssh-hardening/issues/62)
- sftp\_enabled: false will break Ansible's template module [\#55](https://github.com/dev-sec/ansible-ssh-hardening/issues/55)
- Move cipher/kex/mac vars to defaults [\#53](https://github.com/dev-sec/ansible-ssh-hardening/issues/53)

**Merged pull requests:**

- Add SCP/SFTP to FAQ [\#58](https://github.com/dev-sec/ansible-ssh-hardening/pull/58) ([rndmh3ro](https://github.com/rndmh3ro))

## [3.0.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/3.0.0) (2016-03-13)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/2.0.0...3.0.0)

**Implemented enhancements:**

- Added sftp\_enabled, sftp\_chroot\_dir, and ssh\_client\_roaming from the … [\#57](https://github.com/dev-sec/ansible-ssh-hardening/pull/57) ([shirokatze](https://github.com/shirokatze))
- add test support for ansible 1.9 and 2.0 [\#56](https://github.com/dev-sec/ansible-ssh-hardening/pull/56) ([rndmh3ro](https://github.com/rndmh3ro))
- update platforms in meta-file [\#52](https://github.com/dev-sec/ansible-ssh-hardening/pull/52) ([rndmh3ro](https://github.com/rndmh3ro))
- add webhook for ansible galaxy [\#51](https://github.com/dev-sec/ansible-ssh-hardening/pull/51) ([rndmh3ro](https://github.com/rndmh3ro))
- Disable experimental client roaming. [\#49](https://github.com/dev-sec/ansible-ssh-hardening/pull/49) ([rndmh3ro](https://github.com/rndmh3ro))
- use inspec as test framework [\#48](https://github.com/dev-sec/ansible-ssh-hardening/pull/48) ([chris-rock](https://github.com/chris-rock))
- Change categories to tags for upcoming ansible 2.0 [\#47](https://github.com/dev-sec/ansible-ssh-hardening/pull/47) ([rndmh3ro](https://github.com/rndmh3ro))
- add changelog generator [\#46](https://github.com/dev-sec/ansible-ssh-hardening/pull/46) ([chris-rock](https://github.com/chris-rock))

**Closed issues:**

- Install from ansible galaxy missing files \(tasks\) [\#50](https://github.com/dev-sec/ansible-ssh-hardening/issues/50)
- should generate new ssh host key files [\#45](https://github.com/dev-sec/ansible-ssh-hardening/issues/45)

**Merged pull requests:**

- New release 3.0.0 [\#59](https://github.com/dev-sec/ansible-ssh-hardening/pull/59) ([rndmh3ro](https://github.com/rndmh3ro))

## [2.0.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/2.0.0) (2015-11-28)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/1.2.1...2.0.0)

**Closed issues:**

- Fix directory structure. [\#43](https://github.com/dev-sec/ansible-ssh-hardening/issues/43)

**Merged pull requests:**

- New dir layout. Fix \#43 [\#44](https://github.com/dev-sec/ansible-ssh-hardening/pull/44) ([rndmh3ro](https://github.com/rndmh3ro))
- Add var to travis job [\#42](https://github.com/dev-sec/ansible-ssh-hardening/pull/42) ([rndmh3ro](https://github.com/rndmh3ro))
- sftp\_enable option [\#41](https://github.com/dev-sec/ansible-ssh-hardening/pull/41) ([fitz123](https://github.com/fitz123))

## [1.2.1](https://github.com/dev-sec/ansible-ssh-hardening/tree/1.2.1) (2015-10-16)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/1.2...1.2.1)

**Merged pull requests:**

- Allow whitelisted groups on ssh [\#40](https://github.com/dev-sec/ansible-ssh-hardening/pull/40) ([fheinle](https://github.com/fheinle))

## [1.2](https://github.com/dev-sec/ansible-ssh-hardening/tree/1.2) (2015-09-28)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/1.2.0...1.2)

## [1.2.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/1.2.0) (2015-09-28)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/1.1...1.2.0)

**Merged pull requests:**

- bugfix. Now option true for PrintLastLog is available again [\#39](https://github.com/dev-sec/ansible-ssh-hardening/pull/39) ([fitz123](https://github.com/fitz123))
- Add more travis-tests [\#38](https://github.com/dev-sec/ansible-ssh-hardening/pull/38) ([rndmh3ro](https://github.com/rndmh3ro))
- Support for selinux and pam. fix \#23 [\#35](https://github.com/dev-sec/ansible-ssh-hardening/pull/35) ([rndmh3ro](https://github.com/rndmh3ro))

## [1.1](https://github.com/dev-sec/ansible-ssh-hardening/tree/1.1) (2015-09-01)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/1.1.0...1.1)

## [1.1.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/1.1.0) (2015-09-01)
[Full Changelog](https://github.com/dev-sec/ansible-ssh-hardening/compare/1.0.0...1.1.0)

**Closed issues:**

- ssh\_ports - individual client/server config [\#33](https://github.com/dev-sec/ansible-ssh-hardening/issues/33)
- UsePAM should probably default to yes on Red Hat Linux 7 [\#23](https://github.com/dev-sec/ansible-ssh-hardening/issues/23)

**Merged pull requests:**

- Change variable for hmac from server to client [\#37](https://github.com/dev-sec/ansible-ssh-hardening/pull/37) ([rndmh3ro](https://github.com/rndmh3ro))
- Update kitchen-ansible, remove separate debian install [\#36](https://github.com/dev-sec/ansible-ssh-hardening/pull/36) ([rndmh3ro](https://github.com/rndmh3ro))
- Separate ssh client and server ports. Fix \#33 [\#34](https://github.com/dev-sec/ansible-ssh-hardening/pull/34) ([rndmh3ro](https://github.com/rndmh3ro))
- update common kitchen.yml platforms \(ansible\), kitchen\_debian.yml platforms \(ansible\) [\#32](https://github.com/dev-sec/ansible-ssh-hardening/pull/32) ([chris-rock](https://github.com/chris-rock))
- Make MaxAuthTries configurable [\#31](https://github.com/dev-sec/ansible-ssh-hardening/pull/31) ([rndmh3ro](https://github.com/rndmh3ro))
- Change oneliner if-statements to be more readable [\#30](https://github.com/dev-sec/ansible-ssh-hardening/pull/30) ([rndmh3ro](https://github.com/rndmh3ro))
- Make ssh client password login configurable. [\#29](https://github.com/dev-sec/ansible-ssh-hardening/pull/29) ([ypid](https://github.com/ypid))
- Fix join-filter, jinja-cases, intendation [\#27](https://github.com/dev-sec/ansible-ssh-hardening/pull/27) ([rndmh3ro](https://github.com/rndmh3ro))
- Short role review. Fixed role when ssh\_client\_weak\_kex == true. [\#26](https://github.com/dev-sec/ansible-ssh-hardening/pull/26) ([ypid](https://github.com/ypid))
- Make it configurable to only harden ssh client/server or both \(default\). [\#25](https://github.com/dev-sec/ansible-ssh-hardening/pull/25) ([ypid](https://github.com/ypid))
- Separate system-vars from editable vars [\#24](https://github.com/dev-sec/ansible-ssh-hardening/pull/24) ([rndmh3ro](https://github.com/rndmh3ro))
- Add correct CONTRIB-file [\#22](https://github.com/dev-sec/ansible-ssh-hardening/pull/22) ([rndmh3ro](https://github.com/rndmh3ro))
- Add Ansible Galaxy badge [\#21](https://github.com/dev-sec/ansible-ssh-hardening/pull/21) ([rndmh3ro](https://github.com/rndmh3ro))
- fix configuration of playbook path [\#20](https://github.com/dev-sec/ansible-ssh-hardening/pull/20) ([chris-rock](https://github.com/chris-rock))
- Debian install script [\#19](https://github.com/dev-sec/ansible-ssh-hardening/pull/19) ([rndmh3ro](https://github.com/rndmh3ro))

## [1.0.0](https://github.com/dev-sec/ansible-ssh-hardening/tree/1.0.0) (2015-04-30)
**Implemented enhancements:**

- Update variable-documentation [\#12](https://github.com/dev-sec/ansible-ssh-hardening/pull/12) ([rndmh3ro](https://github.com/rndmh3ro))

**Closed issues:**

- add travis test for ubuntu 12.04 [\#7](https://github.com/dev-sec/ansible-ssh-hardening/issues/7)
- Use handler for sshd restart [\#6](https://github.com/dev-sec/ansible-ssh-hardening/issues/6)
- Running test-kitchen fails [\#2](https://github.com/dev-sec/ansible-ssh-hardening/issues/2)

**Merged pull requests:**

- add self as author [\#18](https://github.com/dev-sec/ansible-ssh-hardening/pull/18) ([chris-rock](https://github.com/chris-rock))
- add badges [\#17](https://github.com/dev-sec/ansible-ssh-hardening/pull/17) ([chris-rock](https://github.com/chris-rock))
- fix meta.yml [\#16](https://github.com/dev-sec/ansible-ssh-hardening/pull/16) ([chris-rock](https://github.com/chris-rock))
- add more information to changelog [\#15](https://github.com/dev-sec/ansible-ssh-hardening/pull/15) ([chris-rock](https://github.com/chris-rock))
- Add meta-information for Ansible Galaxy [\#14](https://github.com/dev-sec/ansible-ssh-hardening/pull/14) ([rndmh3ro](https://github.com/rndmh3ro))
- Update CHANGELOG.md [\#13](https://github.com/dev-sec/ansible-ssh-hardening/pull/13) ([rndmh3ro](https://github.com/rndmh3ro))
- Add handler to restart ssh only if necessary. Fix \#6 [\#11](https://github.com/dev-sec/ansible-ssh-hardening/pull/11) ([rndmh3ro](https://github.com/rndmh3ro))
- add more descriptions [\#10](https://github.com/dev-sec/ansible-ssh-hardening/pull/10) ([chris-rock](https://github.com/chris-rock))
- add travis config for ansible [\#9](https://github.com/dev-sec/ansible-ssh-hardening/pull/9) ([chris-rock](https://github.com/chris-rock))
- update .kitchen.yml to find playbook role in tests [\#8](https://github.com/dev-sec/ansible-ssh-hardening/pull/8) ([chris-rock](https://github.com/chris-rock))
- Oracle support [\#5](https://github.com/dev-sec/ansible-ssh-hardening/pull/5) ([rndmh3ro](https://github.com/rndmh3ro))
-  Remove custom Vagrantfile-reference. Fix \#2 [\#4](https://github.com/dev-sec/ansible-ssh-hardening/pull/4) ([rndmh3ro](https://github.com/rndmh3ro))
- Remove custom Vagrantfile-reference. Fix \#2 [\#3](https://github.com/dev-sec/ansible-ssh-hardening/pull/3) ([rndmh3ro](https://github.com/rndmh3ro))
- Fix missing gem [\#1](https://github.com/dev-sec/ansible-ssh-hardening/pull/1) ([chris-rock](https://github.com/chris-rock))



\* *This Change Log was automatically generated by [github_changelog_generator](https://github.com/skywinder/Github-Changelog-Generator)*
