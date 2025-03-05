
#### What is the difference between yum and apt

YUM and APT are package managers that simplify the installation, upgrade and configurations of software packages on Linux systems. 


**Supported installation package format :** 

APT uses .deb files as the package format and is primarily used in Debian , Ubuntu and related distributions. 

YUM uses .rpm files as the package format and is commonly used in Red Hat based distributions like Centos, RHEL etc.

**RoLL Back :** 

Yum allows any changes to be rolled back whereas APT allows you to roll back by specifying the version you want to degrade to. 

**Default Repository configurations :** 

**APT:** /etc/apt/sources.list

**YUM:** /etc/yum.repos.d/



**SPEED AND PERFORMANCE :** 

* APT is generally faster because it has better **dependency resolution mechanism**. 
* YUM is slightly slower since it downloads more metadata for better package management. 


Now what is **DEPENDENCY RESOLUTION MECHANISM ?**

Imagine you want to install software packages on linux but that package depends on other software libraries to function properly. **Dependency resolution** is the process by which a package manager automatically finds , downloads and install the required dependencies before installing the main package. 


