### Create a Local Git Repo
- Create a new repo on your laptop called docs
- Inside docs start a textfile called lamp_server_setup.md
    `cd /Users/meganbohl/Desktop/docs`
    `touch lamp_server_setup.md`
    `git init`
---

### Create a New GitHub Repository Called lamp_server_setup
- https://github.com/MeganBohl?tab=repositories, click "new"
- Make sure the repository is created empty (no readme)

---

### Connect Your Local Repo To Your GitHub Repo
- From the directory your new repo is located in, Not inside of your new repo
- `git remote add origin https://github.com/MeganBohl/lamp_server_setup.git`
- `git push -u origin master`
    -correct response will be: "Branch master set up to track remote branch master from origin."
---

### Check Your GitHub Repo
- create a new directory elsewhere called test_lamp
- `cd /Users/meganbohl/Desktop/test_lamp`
- `git clone git clone https://github.com/MeganBohl/lamp_server_setup.git`
---

## Add Individual Files
`git commit ShellScripts1.md -m "initial commit"`
`git add ShellScripts1`
`git push`
l
