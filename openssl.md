# Tips and tricke for opensssl commands

## Re-encrypt your key with a different encryption algrothirm
```sh
openssl pkcs8 -topk8 -v2 aes128 -in id_rsa -out new-id_rsa
```

