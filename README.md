# Setting Up a Mac for Development

## Brew

### Installing Brew

### Installing Programs with Brew

## Configure Git to use SSH for GitHub

### Create .ssh directory

```bash
# If you don't yet have a .ssh directory in your Home directory, create one
# If you want to isolate your SSH key just to be used by GitHub,
#  you can also create a github sub-folder in your .ssh directory
mkdir -p ~/.ssh/github
```

### Generate SSH keys

```bash
# Run ssh keygen command
ssh-keygen -t ed25519 -C "<your-github-email>"

# When asked for file to save the key, add the path to github directory
# (/Users/<your-user>/.ssh/github/id_ed25519

# Enter a passphrase (if you won't want to add one, hit return to leave it blank)

# Start ssh agent in the background
eval "$(ssh-agent -s)"
```

### Add ssh config file

```bash
vim ~/.ssh/config
```

```txt
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/github/id_ed25519
```

### Add ssh key to ssh-agent

```bash
ssh-add --apple-use-keychain ~/.ssh/github/id_ed25519
```

### Add public key to GitHub

```bash
# copy the public key to your clipboard
pbcopy < ~/.ssh/github/id_ed25519.pub
```

- Go to Github Settings -> SSH and GPG keys -> Add ssh key
- Paste in the public key (from pbcopy) and save it

## Configuring Mac Settings


## Resources
- [SSH key for GitHub](https://medium.com/@edoter92/ssh-key-for-github-2023-120c79908eea)
- [SSH setup for GitHub gist](https://gist.github.com/pszponder/2c6a7e8fc7cd3d0b9461fa3a31792bfa)
