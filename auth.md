# Authentication
Many desktop applications and almost every web service need to store a collection of user data and the passwords, that has to be stored using a hashing algorithm.

Cryptographic hash algorithms MD5, SHA1, SHA256, SHA512, SHA-3 are general purpose hash functions, designed to calculate a digest of huge amounts of data in as short a time as possible. 

Hashing is the greatest way for protecting passwords and considered to be pretty safe for ensuring the integrity of data or password.

## Problems With Cryptographic Hash Algorithm
- Brute Force attack.

Hashes can't be reversed >> An attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value.
- Hash Collision attack.

Hash functions have infinite input length and a predefined output length >> There is inevitably going to be the possibility of two different inputs that produce the same output hash.

### What exactly could be a good for securing your passwords with hashing?
- PBKDF2.
- BCrypt: It's slow and so strong >> This work factor value determines how slow the hash function will be, means different work factor will generate different hash values in different time span, which makes it extremely resistant to brute force attacks.
#### Both of these algorithms use a technique called *Key Stretching*.

## Basic Access Authentication
*Basic access authentication* is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request. 

### Features
HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it does not require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header.

### Security
The BA mechanism does not provide confidentiality protection for the transmitted credentials. They are merely encoded with Base64 in transit and not encrypted or hashed in any way. Therefore, basic authentication is typically used in conjunction with HTTPS to provide confidentiality.

### Protocol
#### Server side:
`WWW-Authenticate: Basic realm="User Visible Realm"`
The server may choose to include the charset parameter:
`WWW-Authenticate: Basic realm="User Visible Realm", charset="UTF-8"`
#### Client side:
`username:password`
Or `QWxhZGRpbjpvcGVuIHNlc2FtZQ==` >> `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`

## [Authentication Cheat Sheet ](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

## NPM
>> npm install bcrypt

### Usage
#### async: 
>> const bcrypt = require('bcrypt');
>> const saltRounds = 10;
>> const myPlaintextPassword = 's0/\/\P4$$w0rD';
>> const someOtherPlaintextPassword = 'not_bacon';

#### To hash a password:
>> // Auto-gen a salt and hash
>> bcrypt.hash(myPlaintextPassword, saltRounds, function(err, hash) {
>>   // Store hash in your password DB.
>> });

>> // Generate a salt and hash on separate function calls
>> bcrypt.genSalt(saltRounds, function(err, salt) {
>>    bcrypt.hash(myPlaintextPassword, salt, function(err, hash) {
>>        // Store hash in your password DB.
>>    });
>> });

#### To check a password:
>> // Load hash from your password DB.
>> bcrypt.compare(myPlaintextPassword, hash, function(err, result) {
>>    // result == true
>> });
>> bcrypt.compare(someOtherPlaintextPassword, hash, function(err, result) {
>>    // result == false
>> });

##### [More about node.bcrypt.js](https://www.npmjs.com/package/bcrypt)

## References:
[Securing Passwords](https://thehackernews.com/2014/04/securing-passwords-with-bcrypt-hashing.html)
[Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication)
[OWASP auth cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
[bcrypt docs](https://www.npmjs.com/package/bcrypt)

### [Home Page](./README.md)
