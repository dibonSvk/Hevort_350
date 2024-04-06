Setup new github repo on the Pi:

1. Go to https://github.com/new and create a new private repo. The repo URL will be used below.

2. Go to https://github.com/settings/tokens and generate a new personal access token. Set the expiration to "No expiration" and select the first "Repo" checkbox then click Generate Token. When prompted for your github credentials below, enter your username and the token you just generated.

3. SSH into the Pi and run the following commands:

git config --global credential.helper store
git config --global user.name "<Your Name>"
git config --global user.email "<Your email>"

cd ~/klipper_config
git init
git add .
git commit -m "First commit"
git remote add origin <remote repository URL>
git remote -v
git push --set-upstream origin master

4. If you browse to your Github repo, you should see the backup.



Setup the macro:

1. Create a new folder called "git" in ~/klipper_config (you can do this through Fluidd or Mainsail)

2. Upload backup_to_git_macro.cfg and backup_to_git.sh tp this new folder

3. SSH into the Pi and install "Shell Command" through Kiauh (Options: 4 then 9). When prompted to install the sample macro, just say No.

4. Edit printer.cfg and add this line near the top:
[include git/*.cfg]

5. Restart the macro. You should now have a working "BACKUP_CFG" macro



Cloning our config from the repo to the pi (Fresh OS Instalation)

1 - Set credentials

SSH into the Pi and run the following commands:

git config --global credential.helper store
git config --global user.name "<Your Name>"
git config --global user.email "<Your email>"

2 - Exejute "cd ~/printer_data"
3 - A - Execute "rm -r config" (Delete whats is in our config folder)
    B - Execute "mv config configold" (To move your actual config folder to another)
4 - git clone <your backup github url> config
5 - Now "cd config" then "ls -l" and you should see everything