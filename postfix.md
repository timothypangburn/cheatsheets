# postfix email server commands

## Display queue messages - deferred and pending
```sh
mailq
```
or
```sh
postqueue -p
```

## Flush all mail queues
```sh
postqueue -f
```

## Test send mail messages - may need to install scripts
```sh
swaks --to timothy.pangburn@wildcardcorp.com --from help@sparx.academy --server 10.1.10.47 --protocol ESMTP
echo "This is the message body and contains the message" | mailx -v -r "timothy.pangburn@wildcardcorp.com" -s "Test from GCP Priv04" -S smtp="10.1.10.47:25" help@sparx.academy
```

## Test with full TLS
```sh
swaks --to timothy.pangburn@wildcardcorp.com --from help+noreply@sparx.academy --server smtp.castlemail.io --port 587 --tls --protocol ESMTP --auth-password --auth-user "help@sparx.academy"
```
## Tail the current Mail Queue
```
mailq | tail -n +2
```

### Check an existing message id
```
postcat -q 196CBD55BB
```
