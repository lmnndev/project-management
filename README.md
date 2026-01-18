# Project-management


## Connecting to the github through SSH

Currently we're on the new start of our journey, documenting everything on our journey of
finding the joy of coding again. But first we need to document everything through git.

One of the challenge is how to connect through SSH on your github repository.

## How? Steps?

1. Create your own repository.
2. Follow the steps provided on the repository to connect.
3. Trigger the push, and you will see an error 
```The authenticity of host 'github.com (XX.XXX.XXX.XXX)' can't be established.```

4. By this moment you need to setup your machine. The github doesn't allow your computer to push an unauthenticated device on their server.

4a. If your pc is newly setup you need to run this code 
```ls ~/.ssh```
you should expect a result something as "known_hosts"

4b. You need to run another code
```ssh-keygen -t ed25519 -C "username@example.com"```

by this moment the keygen will register your email of your github on the ssh-keygen
the id ed25519 will indicate that it is for github.

Passphrase could be added for extra security. But you have an option to leave it empty.

4c. It will generate a series of generated key gen like this below.
```+--[ED25519 256]--+```

4d. After generating keygen, you need to hold your private key in the memory.
```eval "$(ssh-agent -s)"```
Run this code.

4e. Macbook have this keychain, the windows procedure is different. You need to register the access on the keychain also.
```ssh-add --apple-use-keychain ~/.ssh/id_ed25519```

4f. After that copy the SSH using command line.
```pbcopy < ~/.ssh/id_ed25519.pub```

4g. Then the copied SSH, could be pasted on your github settings. Settings > SSH & GPG > Add new SSH...

4h. Retry pushing your code.
