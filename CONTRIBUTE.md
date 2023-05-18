# Security

To the Kodiak project, security is key. This includes secure commits to the code base. With git spoofing a developers identity is easy as there are no controls 
to ensure that the local commiter's identity matches the GitHub account. This gap is closed by signed commits. On Kodiak's repos, only signed commits are 
allowed. Any developer contributing to Kodiak has to sign off commits.

This ensures that all commits are verified:

![Screenshot of a verified commit](https://github.com/polarlabs/kodiak-kb/blob/main/github-commit-verified.png?raw=true)

In short this involves:

* Create a GPG key and uploade the public key to the developers GitHub account.
* Enable vigilant mode on GitHub account.
* Configure git to sign commits.

The full procedure is documented at GitHub (refer to the links below). To lower the entry barrier and foster best practices, we share a short
step-by-step guide with you.

We recommend to follow these practices when creating a GPG key:

* Use a GPG key for signing commits (it's more secure, then SSH keys, as it can expire and be revoked):
  * Use your GitHub account as *real name* of your GPG key.
  * Use the verified email address of your GitHub accounts as *email address* of your GPG key.
* Set a key expiration date. 
* Protect your key with a strong passphrase and store it securely.


## GPG Key

```
~ $ gpg --full-generate-key
gpg (GnuPG) 2.2.41; Copyright (C) 2022 g10 Code GmbH
[...]

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 1

RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits

Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 1y
Key expires at Do 16 Mai 2024 22:47:02 CEST
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.
Real name: tokcum
Email address: tobias.mucke@gmail.com
Comment: Tobias Mucke
You selected this USER-ID:
    "tokcum (Tobias Mucke) <tobias.mucke@gmail.com>"
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O

We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
[...]

gpg: directory '/home/tobias/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/tobias/.gnupg/openpgp-revocs.d/DAD8BAEE4FCAB6F02001FEEE32E977BD4B4A0232.rev'
public and secret key created and signed.

pub   rsa4096 2023-05-17 [SC] [expires: 2024-05-16]
      DAD8BAEE4FCAB6F02001FEEE32E977BD4B4A0232
uid                      tokcum (Tobias Mucke) <tobias.mucke@gmail.com>
sub   rsa4096 2023-05-17 [E] [expires: 2024-05-16]
```

Check the key:

```
~ $ gpg --list-keys --keyid-format=long
/home/tobias/.gnupg/pubring.kbx
-------------------------------
pub   rsa4096/32E977BD4B4A0232 2023-05-17 [SC] [expires: 2024-05-16]
      DAD8BAEE4FCAB6F02001FEEE32E977BD4B4A0232
uid                 [ultimate] tokcum (Tobias Mucke) <tobias.mucke@gmail.com>
sub   rsa4096/261BB4CBD7281BD0 2023-05-17 [E] [expires: 2024-05-16]
~ $
```

Export the public key:

```
~ $ gpg --armor --export 32E977BD4B4A0232
-----BEGIN PGP PUBLIC KEY BLOCK-----

[...]
-----END PGP PUBLIC KEY BLOCK-----
```

Add the GPG Public Key to your GitHub Account:

![Screenshot of Github account settings (GPG Keys)](https://github.com/polarlabs/kodiak-kb/blob/main/github-settings-access-gpg-keys.png?raw=true)

Make also sure you enable vigilant mode.

![Screenshot of Github account settings (Vigilant mode)](https://github.com/polarlabs/kodiak-kb/blob/main/github-settings-access-vigilant-mode.png?raw=true)

Configure git to use your GPG key for signing and ensure that all commits are signed:

```
git config --global user.signingkey 32E977BD4B4A0232
git config --global commit.gpgsign true
```

# Links 

[Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)

[Telling Git about your signing key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
