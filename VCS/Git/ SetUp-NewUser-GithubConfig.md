# USER CONFIGURATIONS(ssh included) WITH Git

## set your Username:

     git config --global user.name "Your Name"

## set your Email:

      git config --global user.email "your.email@example.com"

## verify configuration:

       git config --global --list

## create a new ssh key:

        ssh-keygen -t rsa -b 4096 -C "your.email@example.com"

## Run the ssh-keygen command and specify a filename iy you want:

        ssh-keygen -t rsa -b 4096 -C "your.email@example.com" -f ~/.ssh/your_key_name

##  Add the New SSH Key to the SSH Agent:
       eval "$(ssh-agent -s)"
       ssh-add ~/.ssh/your_key_name   

##   Add the Public Key to Your GitHub Account:

##    Copy the public key to your clipboard:

        pbcopy < ~/.ssh/id_rsa_new.pub  # macOS
        cat ~/.ssh/id_rsa_new.pub | clip  # Windows
        xclip -sel clip < ~/.ssh/id_rsa_new.pub  # Linux (if xclip is installed)                         

## set the key within the ~/.sshconfig file as following:
        Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/<your-private-key>
## Verify that the key is loaded:

        ssh-add -l

## Test SSH Connection

## Run: ssh -T git@github.com
        output: Hi <username account>! You've successfully authenticated, but GitHub does not provide shell access.

## Set the Correct Git Remote URL

        git remote set-url origin git@github.com:JFKTBonny/Devops_Resources.git

## un: git remote -v to verify

## Push to GitHub

        git push origin main


   

















