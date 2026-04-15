# GitHub SSH Setup (Step-by-Step)

This guide explains how to:

- Create a GitHub repo  
- Generate SSH keys  
- Add the public key to Deploy Keys  
- Start the SSH agent + add your key  
- Connect your local repo to GitHub using SSH  

---

## 1. Create GitHub Repository


## 2️. Generate an SSH Key Pair

Open Git Bash and run:

```bash
cd ~/.ssh
ssh-keygen -t rsa -b 4096 -C "martynahaliniak@gmail.com"
```

### What this command means
- `ssh-keygen` → generates an SSH key  
- `-t rsa` → RSA algorithm  
- `-b 4096` → 4096-bit key (strong)  
- `-C "email"` → adds an identifying comment  

When prompted:
- Enter a file name → e.g. `tech601-martyna-github-key`  
- Press **Enter** for passphrase (optional)

This creates:
- **Private key:** `tech601-martyna-github-key`
- **Public key:** `tech601-martyna-github-key.pub`

---

## 3. Copy the Public Key

```bash
cat tech601-martyna-github-key.pub
```

Copy the whole output. 

## 4. Add the Public Key to GitHub (Deploy Keys)

1. Go to your GitHub repository  
2. **Settings → Deploy Keys**  
3. Click **Add deploy key**  
4. Title: anything (e.g., *Martyna CI/CD Key*)  
5. Paste the **public** key you copied from `tech601-martyna-github-key.pub`  
6. Tick **Allow write access** (so you can push)  
7. Save

---

## 5. Start the SSH Agent (must be run every new terminal session)

```bash
eval `ssh-agent -s`
```

The SSH agent holds your private keys in memory for the session. It resets every time you close the terminal, so you need to run this in each new terminal session.


## 6. Add Your Private Key to the Agent

```bash 
ssh-add ~/.ssh/tech601-martyna-github-key
```

You should see:
```
Identity added: tech601-martyna-github-key (martynahaliniak@gmail.com)
```

## 7. Test SSH Connection
```bash
ssh -T git@github.com
```
Expected output:
```
Hi martyna-haliniak! You've successfully authenticated, but GitHub does not provide shell access.
```


## 8. Connect Your Local Repo to GitHub via SSH

Navigate to your project folder:
```bash
cd ~/Documents/SpartaGlobal/Devops/Training/github/tech601_CI_CD/
```

Remove any old remote (if already connected via HTTPS):
```bash
git remote remove origin
```

Add the new SSH remote:
```bash
git remote add origin git@github.com:martyna-haliniak/tech601_CI_CD.git
```

Check it:
```bash
git remote -v
```

You should see something like:
```
origin  git@github.com:martyna-haliniak/tech601_CI_CD.git (fetch)
origin  git@github.com:martyna-haliniak/tech601_CI_CD.git (push)
```

## 9. Add, Commit, and Push

```bash
git add .
git commit -m "set up .ssh key"
git push -u origin main
```


## Daily Usage Summary 
Every time you open Git Bash, run:

```bash
eval `ssh-agent -s`
ssh-add ~/.ssh/tech601-martyna-github-key
```

After this, Git will use your SSH key automatically for pushes and pulls.


tests