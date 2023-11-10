gpg --list-keys

pub   rsa4096 2023-05-17 [SC] [expires: 2024-05-16]
1D22853ADB064980321671AE8467929DF52E5F20
uid           [ultimate] tokcum (Tobias Mucke) <tobias.mucke@gmail.com>
sub   rsa4096 2023-05-17 [E] [expires: 2024-05-16]

gpg --export-secret-key -a tokcum > prv.key

gpg --export -a tokcum > pub.key


gpg --import pub.key

gpg --import prv.key




git config --global user.email "tobias.mucke@gmail.com"
git config --global user.name tokcum


gh auth login

-> follow instruction on screen
