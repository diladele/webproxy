# Web Filtering Proxy for Microsoft Windows

Web Filtering Proxy for Microsoft Windows is a new implementation of web filtering proxy running natively on Microsoft Windows. It can decrypt HTTPS traffic, filter HTTP requests and responses and inspect contents of HTML pages. 

## How to Install?

In order to install the application download and run the MSI file from http://packages.diladele.com/0.1.0.333B/amd64/release/windows/webproxy-0.1.0.333B_amd64.msi. 

The installer will make the following changes to your system.

* Install `webproxyd.exe` executable file into `C:\Program Files\Diladele\WebProxy` folder.
* Add Web Filtering Proxy service to Services Management Console.
* Put data folders with definition files, logs and other temporary contents into `C:\ProgramData\Diladele\WebProxy`.
* Add a firewall rule to built-in Windows Defender Firewall allowing TCP connections from within your local subnet to IP address of the system (port 3128).

## How to Use?

Point your browsers to the IP address of the machine where you installed the application (port 3128) and browse the web. 

## How to Configure?

Currently the project has no built-in Admin UI and can be managed only manually using JSON configuration file in `C:\ProgramData\Diladele\WebProxy\etc\config.json`. Configuration is mostly self explanatory. Just make the changes in the JSON file, save it and restart the service from the Service Management console.

## Configuration examples

For configuration examples see the following pages.

* How to Enable HTTPS Decryption
* How to Change Port to Listen On
* How to Block Sites by Categories
* How to Block Ads

## Issues, Feature Requests or Support

Please use the [New Issue](https://github.com/diladele/webproxy/issues/new) button to add the issue, feature request or support question directly to the development team. You can also send an e-mail to support@diladele.com