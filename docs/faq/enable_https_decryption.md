# How to Enable HTTPS Decryption

Web Filtering Proxy is capable of decrypting HTTPS traffic coming from the browsers. In order to decrypt the HTTPS traffic you would first need to generate a self-signed Root Certification Authority (Root CA) certificate and then install it into the trusted certificate store of your operating system.

## Generate the Root Ca Decryption Certificate

To generate the Root CA certificate use the following OpenSSL commands. 

	$ openssl req -new -newkey rsa:2048 -sha256 -days 3650 -nodes -x509 -keyout myca.pem -out myca.pem
	$ openssl x509 -outform der -in myca.pem -out myca.der

Copy the myca.pem and myca.der into `C:\ProgramData\Diladele\WebProxy\etc\` folder. Note after installation sample `myca.pem` and `myca.der` are present there already. These files shall never be used in real deployment but are ok if you need to quickly see the application in action in the test lab. Trusting these files pose serious security risk just because anyone can extract them from the MSI installer.

Note if you have trusted Root CA from our Web Safety project you can directly use it in Web Filtering Proxy application. See https://docs.diladele.com/administrator_guide_stable/https_filtering/generate_certificates/automatically.html.

## Install Root Ca as Trusted Certificate into the Microsoft Windows 

To install the newly generated Root CA certificate as trusted into certificate storage of Microsoft Windows, please follow the article for [Internet Explorer / Microsoft Edge or Google Chrome](https://docs.diladele.com/administrator_guide_stable/https_filtering/install_certificates/win_ie_chrome.html) and [Mozilla Firefox](https://docs.diladele.com/administrator_guide_stable/https_filtering/install_certificates/win_ff.html). Note that both Chrome and Edge browsers load trusted certificates from the system store and Firefox has its own certificate store.

## Enable HTTPS Decryption in the Filtering Policy

HTTPS decryption in Web Filtering Proxy is configured per policy level. This makes it very convenient to selectively enable HTTPS decryption for subsets of your network. To enable decryption, open the `config.json` file and ensure you have the `"mode" = 2` in the decryption section.

	"decryption" : {
        "trusted" : [ "banking_insurance_finance", "government", "health_medicine_fitness", "network_infrastructure" ],
        "mode" : 2,
        "targets" : []
    },

Possible values are 0 (no_decryption), 1 (targeted_decryption) and  2 (complete_decryption). 

## Ensure it Works

