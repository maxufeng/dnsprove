# Open Attestation (dnsprove)

A helper library to retrieve OpenAttestation DNS-TXT records from domains using Google's public DNS service.

A valid OpenAttestation DNS-TXT record looks like:

```js
[
  {
    name: "example.openattestation.com.",
    type: 16,
    TTL: 110,
    data: '"openatts net=ethereum netId=3 addr=0x2f60375e8144e16Adf1979936301D8341D58C36C"',
  },
];
```

Validation is run on all retrieved records to ensure they conform to the expected format, and records that fail validation will simply be omitted from the returned results.

## Installation

```bash
npm i @tradetrust-tt/dnsprove
```

***

## Debug

To see validation failures run the library with the debug flag turned on, either

In Browser:

`localStorage.debug="dnsprove*"`

In NodeJS:

```sh
DEBUG="dnsprove*" npm run test
```

## Types

This library uses [runtypes](https://github.com/pelotom/runtypes) for compile time static type checking as well as run time input validation. The generated documentation below is inaccurate for any Runtypes generated types due to documentation generator limitations.

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

*   [OpenAttestationDNSTextRecord](#openattestationdnstextrecord)
*   [OpenAttestationDnsDidRecord](#openattestationdnsdidrecord)
*   [IDNSRecord](#idnsrecord)
*   [IDNSQueryResponse](#idnsqueryresponse)
*   [CustomDnsResolver](#customdnsresolver)
*   [defaultDnsResolvers](#defaultdnsresolvers)
*   [queryDns](#querydns)
    *   [Parameters](#parameters)
*   [parseOpenAttestationRecord](#parseopenattestationrecord)
    *   [Parameters](#parameters-1)
*   [parseDocumentStoreResults](#parsedocumentstoreresults)
    *   [Parameters](#parameters-2)
*   [parseDnsDidResults](#parsednsdidresults)
    *   [Parameters](#parameters-3)
*   [getDocumentStoreRecords](#getdocumentstorerecords)
    *   [Parameters](#parameters-4)
    *   [Examples](#examples)
*   [getDnsDidRecords](#getdnsdidrecords)
    *   [Parameters](#parameters-5)

### OpenAttestationDNSTextRecord

### OpenAttestationDnsDidRecord

### IDNSRecord

### IDNSQueryResponse

### CustomDnsResolver

Type: function (domain: [string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)): [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[IDNSQueryResponse](#idnsqueryresponse)>

### defaultDnsResolvers

Type: [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[CustomDnsResolver](#customdnsresolver)>

### queryDns

#### Parameters

*   `domain` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)**&#x20;
*   `customDnsResolvers` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[CustomDnsResolver](#customdnsresolver)>**&#x20;

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[IDNSQueryResponse](#idnsqueryresponse)>**&#x20;

### parseOpenAttestationRecord

Parses one openattestation DNS-TXT record and turns it into an OpenAttestationsDNSTextRecord object

#### Parameters

*   `record` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** e.g: '"openatts net=ethereum netId=3 addr=0x0c9d5E6C766030cc6f0f49951D275Ad0701F81EC"'

Returns **GenericObject**&#x20;

### parseDocumentStoreResults

Takes a DNS-TXT Record set and returns openattestation document store records if any

#### Parameters

*   `recordSet` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[IDNSRecord](#idnsrecord)>** Refer to tests for examples (optional, default `[]`)
*   `dnssec` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)**&#x20;

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[OpenAttestationDNSTextRecord](#openattestationdnstextrecord)>**&#x20;

### parseDnsDidResults

#### Parameters

*   `recordSet` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[IDNSRecord](#idnsrecord)>**  (optional, default `[]`)
*   `dnssec` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)**&#x20;

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[OpenAttestationDnsDidRecord](#openattestationdnsdidrecord)>**&#x20;

### getDocumentStoreRecords

Queries a given domain and parses the results to retrieve openattestation document store records if any

#### Parameters

*   `domain` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** e.g: "example.openattestation.com"
*   `customDnsResolvers` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[CustomDnsResolver](#customdnsresolver)>?**&#x20;

#### Examples

```javascript
> getDocumentStoreRecords("example.openattestation.com")
> [ { type: 'openatts',
net: 'ethereum',
netId: '3',
addr: '0x2f60375e8144e16Adf1979936301D8341D58C36C',
dnssec: true } ]
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[OpenAttestationDNSTextRecord](#openattestationdnstextrecord)>>**&#x20;

### getDnsDidRecords

#### Parameters

*   `domain` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)**&#x20;
*   `customDnsResolvers` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[CustomDnsResolver](#customdnsresolver)>?**&#x20;

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[OpenAttestationDnsDidRecord](#openattestationdnsdidrecord)>>**&#x20;

## License

MIT
