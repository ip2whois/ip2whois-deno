# Quickstart

## Dependencies

This module requires API key to function. You may sign up for a free API key at <https://www.ip2location.io/pricing>.

## Installation

This module does not require any installation, you can import from Deno land like this:

```js
import { Configuration, IPGeolocation, DomainWhois } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";
```

## Sample Codes

### Lookup IP Address Geolocation Data

You can make a geolocation data lookup for an IP address as below:

```js
import { Configuration, IPGeolocation } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";

// Configures IP2Location.io API key
let mykey = "YOUR_API_KEY";
let config = new Configuration(mykey);

let ipl = new IPGeolocation(config);

let myip = "8.8.8.8";
let lang = "en"; // language parameter is only available for Plus and Security plans

// Lookup ip address geolocation data
ipl.lookup(myip, lang)
  .then((data) => {
    // print the data in json format
    console.log(data)
  })
  .catch((error) => {
    // print the error
    console.log(error)
  });
```

### Lookup Domain Information

You can lookup domain information as below:

```js
import { Configuration, DomainWhois } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";

// Configures IP2Location.io API key
let mykey = "YOUR_API_KEY";
let config = new Configuration(mykey);
let whois = new DomainWhois(config);

let mydomain = "locaproxy.com";

// Lookup domain information
whois.lookup(mydomain)
  .then((data) => {
    // print the data in json format
    console.log(data)
  })
  .catch((error) => {
    // print the error
    console.log(error)
  });
```

### Convert Normal Text to Punycode

You can convert an international domain name to Punycode as below:

```js
import { Configuration, DomainWhois } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";

let config = new Configuration();
let whois = new DomainWhois(config);

// Convert normal text to punycode
console.log(whois.getPunycode("täst.de"));
```

### Convert Punycode to Normal Text

You can convert a Punycode to international domain name as below:

```js
import { Configuration, DomainWhois } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";

let config = new Configuration();
let whois = new DomainWhois(config);

// Convert punycode to normal text
console.log(whois.getNormalText("xn--tst-qla.de"));
```

### Get Domain Name

You can extract the domain name from an url as below:

```js
import { Configuration, DomainWhois } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";

let config = new Configuration();
let whois = new DomainWhois(config);

// Get domain name from URL
console.log(whois.getDomainName("https://www.example.com/exe"));
```

### Get Domain Extension

You can extract the domain extension from a domain name or url as below:

```js
import { Configuration, DomainWhois } from "https://deno.land/x/ip2whois@1.0.0/mod.ts";

let config = new Configuration();
let whois = new DomainWhois(config);

// Get domain extension (gTLD or ccTLD) from URL or domain name
console.log(whois.getDomainExtension("example.com"));
```