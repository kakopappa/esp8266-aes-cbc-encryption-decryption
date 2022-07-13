# ESP8266 AES CBC Encryption/Decryption demo.

AES CBC encryption/decryption using BearSSL for ESP8266. 

![ESP8266 AES CBC encryption decryption demo](https://github.com/kakopappa/esp8266-aes-cbc-encryption-decryption/blob/main/demo.png)


Made for https://github.com/kakopappa/esp8266_public_private_key_encryption_example_with_aes_128_cbc_nodejs

*** How to decrypt in nodeJs

```
const crypto = require('crypto');

var cipher_key = Buffer.from([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]);
var cipher_iv = Buffer.from([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]);

let aesEncrypt = function(text){
    const cipher = crypto.createCipheriv('aes-128-cbc',cipher_key,cipher_iv)
    text = new Buffer.from(text)
    var crypted = cipher.update(text,'utf-8','base64')
    crypted += cipher.final('base64');
    return crypted;
}

let aesDecrypt = function(text){
    const decipher = crypto.createDecipheriv('aes-128-cbc',cipher_key,cipher_iv)
    let dec = decipher.update(text,'base64','utf-8');
    dec += decipher.final();
    return dec;
}


console.log(aesDecrypt("Cl7DlZboTjPIkjhCdORh6GTJRiSJJFE15cP0IjZq5rnNOOIg8t+w2Ckh5qo2l3UxTcm5lj3MczZQ4gb113k6oauEq70xeP3ybi4sheowxGY="));
```
