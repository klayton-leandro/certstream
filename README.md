# Certstreamcatcher
Catching phishing by observing [certificate transparency logs](https://www.certificate-transparency.org/known-logs). This tool is based on regex with effective standards for detecting phishing sites in real time using [certstream](https://github.com/CaliDog/certstream-js) and can also detect [punycode (IDNA)](https://en.wikipedia.org/wiki/Punycode) attacks such as https://www.ṁyetḣerwallet.com.


### Phishing 

[![Phishing](https://pbs.twimg.com/media/DY-k7YFWsAA_f8l.jpg)](https://twitter.com/6IX7ine/status/943229448614182912)


### Installation

```
$ cd /opt/
$ git clone https://github.com/klayton-leandro/certstreamcatcher.git
$ cd certstreamcatcher
$ npm install
```

### npm package

To install certstreamcatcher using `npm` run:

  	npm install --save certstreamcatcher
       
### Try on npm runkit

This is a playground to test certstreamcatcher

[https://npm.runkit.com/certstreamcatcher](https://npm.runkit.com/certstreamcatcher)
    
### Usage
The certstreamcatcher is extremely simple, all you have to do is to import the library **certstreamcatcher** and certstream register the callback and call **certstreamClientPhishing** and pass the callback parameter to certstreamClientPhishing.

```
const certstreamcatcher = require('certstreamcatcher'); 
const certstream = require("certstream");

const regex = /(wellsfargo|paypal|login|sign-in|secure|update|money|sslsecure|amazon)/gi; # Keywords

const tlds = ['.io','.gq','.ml','.cf','.tk','.xyz','.pw','.cc']; # tlds 

var client = new certstream(function(certstream) {  
	certstreamcatcher.certstreamClientPhishing(certstream, regex, tlds, {tlds: true});
});

client.connect();
```
To execute the program save the above code and execute with the command:
```
$ node certstreamcatcher.js
```