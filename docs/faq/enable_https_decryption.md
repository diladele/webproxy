# How to Enable HTTPS Decryption

Web Filtering Proxy is capable of decrypting HTTPS traffic coming from the browsers. Use the following steps to set it up:

* Ensure you have generated Root Certification Authority decryption certificate as described in the following article. By default there is an example certificate is stored in `C:\ProgramData\Diladele\WebProxy\etc\myca.pem` after installation. You are strongly advised to generate your own. Trusting default certificate may pose serious security risk because anyone has access to it.
* Ensure you have installed this decryption certificate as trusted into your browsers. See these article for more information. Note that Chrome/Edge browsers load trusted certificates from system store and Firefox has its own certificate store.

