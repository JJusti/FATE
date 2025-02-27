# FATE Packages Build Guide

[TOC]

## 1. Software Environment

| Name   | Version |
| ------ | ------- |
| JDK    | 1.8+    |
| Maven  | 3.6.1+  |
| Python | 3.6.5   |

## 2. Get the source code

Please refer to [get source code](../common/get_source_code.md)

## 3. Build

```bash
cd FATE;
bash build/package-build/build.sh ${version_tag} all
```

The **all** means that modules needs to be deployed, all means all, supports all, fateflow fateboard eggroll examples

## 4. Output

```bash
ls -l FATE_install_${version}_${version_tag}.tar.gz
```

## 5. Check packages

```bash
tar xzf FATE_install_${version}_${version_tag}.tar.gz;
ls -lrt FATE_install_${version}_${version_tag}
```

You can see the following package:

| Name             | Details                                                   |
| ---------------- | --------------------------------------------------------- |
| bin.tar.gz       | some scripts                                              |
| conf.tar.gz      | some configuration files                                  |
| build.tar.gz     | build scripts                                             |
| deploy.tar.gz    | deploy scripts                                            |
| examples.tar.gz  | some algorithm test examples                              |
| fate.tar.gz      | include federatedml and fate arch                         |
| fateflow.tar.gz  | fateflow packages                                         |
| fateboard.tar.gz | fateboard packages                                        |
| eggroll.tar.gz   | eggroll cluster: cluster manager, node manager, rollsiter |
| fate.env         | settings for version                                      |
| requirements.txt | necessary dependency for python environment               |
| RELEASE.md       | release document                                          |
| packages_md5.txt | md5 numbers for each package                              |

## 6. Make python dependency install package(Optional)

You can make python dependency package like:

```bash
cd FATE
bash build/package-build/build.sh ${version_tag} pypi
```

And then you found it:

```bash
FATE_install_${version}_${version_tag}/pypi.tar.gz
```

You can use it like:

```bash
pip install -r FATE/python/requirements.txt --no-index -f FATE_install_${version}_${version_tag}/pypi
```

**Ensure that the operating system on which the dependency packages are made and the operating system on which the dependency packages will be installed are the same**
**Don't forget to set the value of ${version}**

## 7. Make python environment install package(Optional)

You can make it like:

```bash
cd FATE
bash build/package-build/build.sh ${version_tag} python36
```

And then you found it:

```bash
FATE_install_${version}_${version_tag}/python36.tar.gz
```

**Ensure that the operating system on which the dependency packages are made and the operating system on which the dependency packages will be installed**
**Don't forget to set the value of ${version}**

## 8. Make java environment install package(Optional)

You can make it like:

```bash
cd FATE
bash build/package-build/build.sh ${version_tag} jdk
```

And then you can use it like:

```bash
FATE_install_${version}_${version_tag}/jdk.tar.gz
```
