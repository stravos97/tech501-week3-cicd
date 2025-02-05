![Pasted image 20250204154321](https://github.com/user-attachments/assets/16eda5be-34d6-41c7-84e0-f92fd0360991)

```bash
ssh-keygen -t rsa -b 4096 -C "haashimalvi@pm.me"
```
Name your ssh something that relates to the service you are using and put it in `.ssh` dir
![Pasted image 20250204154459](https://github.com/user-attachments/assets/8bcc0e92-cb1a-45be-a044-d1c25d12587c)
Make sure it is moved to the right dir

![Pasted image 20250204154552](https://github.com/user-attachments/assets/a8e11431-4c80-48b5-918a-5290c1b4f376)
Run cat in you ssh dir. If you are in your home dir, then you can run:
```bash
cat ~/.ssh/gh-hetzner-vm.pub
```
Copy your public key to your clipboard

Navigate to github.com and login. Then go to your settings:
![Pasted image 20250204154954](https://github.com/user-attachments/assets/44bb889f-75a0-4f1a-9038-c5020a0f50ea)
Navigate to `SSH and GPG Keys`
![Pasted image 20250204155033](https://github.com/user-attachments/assets/a6d93ebf-7d7b-4197-ade9-3a85b47c6e9f)

Click `Create` and insert your public key with a name that best describes the device it is coming from.
Click `Add SSH Key`
![Pasted image 20250204155205](https://github.com/user-attachments/assets/e4c462c6-2eba-4e3c-a92e-308b9b38d0f3)

You then need to start your ssh key agent
What does this do?
![Pasted image 20250204155336](https://github.com/user-attachments/assets/8e161682-5102-41a2-a42d-6f3bf2d4d5c0)
```bash
eval `ssh-agent -s`
```

After starting the agent we can then add the private key to this agent
![Pasted image 20250204160046](https://github.com/user-attachments/assets/24e9a63a-f9f4-4d66-9877-56388b5a9089)
```bash
ssh-add ~/.ssh/gh-hetzner-vm
```


You can check if your ssh key is working properly by running

```bash
ssh -T git@github.com
```
If successful, we should see:
![Pasted image 20250204160135](https://github.com/user-attachments/assets/4ba97f47-f769-42a9-8a63-3bd6077820c6)

We then need to make a repo and test it with ssh authentication
![Pasted image 20250204160430](https://github.com/user-attachments/assets/dedb8645-4aba-43cd-93a7-b776e2fd7a10)
We ran `git init` in the newly created dir `tech501-test-ssh`

The git repo needs to be created on Github. For that I am using **Github CLI** which uses the `gh` command.
```bash
gh repo create tech501-test-ssh --public --source=. --remote=origin
```
This can also be done manually on the web portal:
![Pasted image 20250204160941](https://github.com/user-attachments/assets/61646525-7a91-4259-8c21-bfb2061dbcda)
Once created we need to run the following list of commands. This changes from repo to repo on first init. Github **will** always give you these instructions on a new repo creation so we can copy and paste.
![Pasted image 20250204161152](https://github.com/user-attachments/assets/388f412a-b21c-4a0f-b396-bdf3ae1b6410)
```bash
echo "# tech501-test-ssh" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:stravos97/tech501-test-ssh.git
git push -u origin main
```
![Pasted image 20250204161246](https://github.com/user-attachments/assets/dbf09823-dec2-4003-96c8-cb10c53708f0)
This didn't work in this case because on first initialization git doesn't know who you are. This can be set with the following commands:
```bash
git config --global user.email "haashimalvi@pm.me"
git config --global user.name "Haashim"
```
Once set, we should be successful
![Pasted image 20250204161457](https://github.com/user-attachments/assets/f4c4c550-fdd3-4219-82d9-0dc0a8f862d1)
If we go back to Github we can see this was set successfully
![Pasted image 20250204161539](https://github.com/user-attachments/assets/7a7aba77-93db-48e1-96ce-5061b48077d1)