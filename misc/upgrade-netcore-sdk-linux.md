# How to upgrade Net Core SDK in Ubuntu Linux
[Index](README.md)

This has to be done one time:

    > wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
    > sudo dpkg -i packages-microsoft-prod.deb

After the one-time, this will install the specific version

    > sudo apt-get update
    > sudo apt-get install apt-transport-https
    > sudo apt-get update
    > sudo apt-get install dotnet-sdk-3.1

[Microsoft Full Instructions](https://docs.microsoft.com/en-us/dotnet/core/install/linux-package-manager-ubuntu-1904)
