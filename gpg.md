# GPG

[GnuPG](https://www.gnupg.org/index.html) (also known as GPG) is a complete and free implementation of the OpenPGP standard as defined by RFC4880 (also known as PGP). It is a command line tool with features for easy integration with other applications. It is used to encrypt and sign data, and features a key management system.

As part of following GitHub's instructions on [signing commits with gpg](https://help.github.com/articles/signing-commits-with-gpg/), the first step is to install it.

## Install

```bash
brew install gpg
```

## Generating a key

I now have a generated key for use when signing my git commits. However should I need to generate another one in the future just call `gpg --full-generate-key`.

Note, the GitHub instructions tell you to just call `gpg --gen-key` but not only does gpg say to use the full one, I just got issues until I switched to running through the full dialog.

## Exporting existing keys

To export my keys I basically followed these instructions on how to [back up your pgp keys with gpg](https://msol.io/blog/tech/back-up-your-pgp-keys-with-gpg/)

```bash
gpg --armor --export > pgp-public-keys.asc
gpg --armor --export-secret-keys > pgp-private-keys.asc
gpg --export-ownertrust > pgp-ownertrust.asc
```

Having created these files save them to your super secret place from which you can access them from another machine when required.

## Importing

To import download the files we saved earlier and then call the following

```bash
gpg --import pgp-public-keys.asc
gpg --import pgp-private-keys.asc
gpg --import-ownertrust pgp-ownertrust.asc
```

That's it!

## Viewing keys

When setting Git and GitHub up to use your key you'll often be asked to get the key ID.

```bash
gpg --list-secret-keys --keyid-format LONG
```

Running this will return something like this

```bash
$ gpg --list-secret-keys --keyid-format LONG
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```

They key ID in this example is **3AA5C34371567BD2**.

## Signing commits

Having done all this you can then tell git about the gpg key. [Git](git.md) covers how to do this.
