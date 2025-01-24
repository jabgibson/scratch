# GPG usage on linux

## commands

### Generate a new key
```shell
gpg --full-gen-key
```
An alternative flag is `--full-generate-key`. This might be distro dependant.
My observation has been I see both options.

### Bypass the ui popup for password entry
> use: `--pinentry-mode loopback`

```shell
gpg --full-gen-key --pinentry-mode loopback
```

### Export public key to file
Use ASCII armor to export the key. This wraps the key in (human / machine) readable format
with stop and start guards.

> **Note**
> 
> Common practice (I think) is to use an ascii extention to exported file.
> Example: `enrypted_file.asc`

```sh
gpg --armor --export ${EMAIL_ASSOCIATED_W_KEY} > ${EXPORTED_KEY_ASC_FILE}
```

### Edit an existing key password
To update the password of an existing key, hop into edit mode for that key
```sh
gpg --edit-key ${EMAIL_ASSOCIATED_W_KEY}
```
Once in edit mode, to update the password type in command `passwd` and then `save` once completed.

### Encrypt a file

#### For external recipient
```sh
gpg --encrypt --recipient ${RECIPIENT_EMAIL} ${FILE_NAME}
```
This will create a filename named `${FILE_NAME}.gpg`

#### For personal encryption

### Decrypt a file
```sh
gpg --decrypt ${FILE_NAME}.gpg > ${DECRYPTED_FILE_NAME}
```

> **NOTE**
> 
> the `--recipient` command is not a part of decryption.
> In the decryption process looks up the signer and uses
> a public key stored in the local keyring. If this public
> key is not in the keyring, I don't think decryption is possible.




