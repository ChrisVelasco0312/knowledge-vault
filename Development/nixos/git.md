---
id: git
aliases: []
tags: []
---

# Setting up github in fresh installation of nixos

## 1. Setup a new ssh key

```bash
ssh-keygen -t rsa -b 4096 -C "youremail@email.com"
```

## 2. Start the ssh-agent in the background

```bash
eval "$(ssh-agent -s)"
```

## 3. Add your SSH private key to the ssh-agent

```bash
ssh-add ~/.ssh/id_rsa
```
