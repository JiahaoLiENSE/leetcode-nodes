## Set Up Multiple github Accounts SSH Key In One Local Machine For Push and Pull Tips
**Windows(PowerShell run as Administor)**
### Generate SSH Key In Local
Add SSH key to second github account(within C:Users\username\.\.ssh):  
`ssh-keygen -t rsa -C "your-email-address"`  
When prompted, save the file as:  
`~/.ssh/id_rsa_OTHERNAME`  
### Attach The New SSH Key
First check `ssh-agent` is running or not:  
`Get-Service | ?{$_.Name -like '*ssh-agent*'} | select -Property Name, StartType, Status` --> supposed as: `Disabled` and `Stopped`  
If shown `Disabled`, then enable it:  
`Set-Service -Name ssh-agent -StartupType Manual`  
If not shown:  
`Start-Service ssh-agent`  
Then add your new ssh key:  
`ssh-add <path to the key>`  
### Add SSH Key to Github
Login in github:  
`Settings->SSH and GPG keys->New SSH Key`  
Copy SSH Key credentials from local machine in the right directory(at same path as storing path):  
`cat id_rsa_OTHERNAME.pub`  
### Connect To Github
1. Create a new repo on github -> eg. `test`  
2. Copy command line via `SSH` Tab from the repo  
3. Go to the location you want to put on pc, do `git clone <you copied command>`  
4. Change Git Config file: `git config -e`. Add line `sshCommand = ssh -i ~/.ssh/id_ra_OTHERNAME` to the **[Core]** list. And then, add new list **[user]** associated with new lines: `email = your_github_email`, `name = your_github_username`  
5. `git add .`  
6. `git commit -m "first init"  
7. `git remote add origin git@github.com:your_github_username/test.git`  
8. `git push origin master`  
9. Done.

#### Tips to delete SSH Key Identity
`ssh-add -D <path of storing ssh key location>`
