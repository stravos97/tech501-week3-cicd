
![Pasted image 20250204144546](https://github.com/user-attachments/assets/60eeb9ce-5b9a-44d9-b3b7-f963d6130d7c)We are first going to generate our own internal ssh key pair
In documentation we need to show using ssh this entire process

![Pasted image 20250204144725](https://github.com/user-attachments/assets/0d3c1f0e-37f0-4ad7-baee-9b2cabc77dde)

![Pasted image 20250204145133](https://github.com/user-attachments/assets/45e430e3-593d-451b-9748-0f2c58f38e07)

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```


![Pasted image 20250204145927](https://github.com/user-attachments/assets/9b98d39b-4278-4400-9b2a-1a9252cafd52)


![Pasted image 20250204150546](https://github.com/user-attachments/assets/9997bff1-57d7-48ca-93a6-ba9041d1e459)

You then need to start the ssh key agent
```bash
eval `ssh-agent -s`
```

![Pasted image 20250204150732](https://github.com/user-attachments/assets/c776c0c7-86fc-4d21-9857-643c14f25e81)

You then need to add the private key to the ssh agent
```bash
ssh-add <private key name>
```

![Pasted image 20250204150803](https://github.com/user-attachments/assets/4e16a1d7-a852-4ecb-9c8e-a627a08a682a)

to check if it is properly authenticated you need to run
```bash
ssh -T git@github.com
```

Setting up a repo from scratch
![Pasted image 20250204151918](Pasted%20image%2020250204151918.png)

![Pasted image 20250204151918](https://github.com/user-attachments/assets/bc77396a-5cf7-4190-b62d-210733f2de61)

![Pasted image 20250204151946](https://github.com/user-attachments/assets/d47935d6-c48c-4fae-94d8-f524c2656af6)
If you need to change the remote origin url do:
```
git remote set-url origin git@github.com:your-username/tech501-test-ssl.git

```

![Pasted image 20250204152540](https://github.com/user-attachments/assets/d45f88ed-e6ac-4bce-b6a9-8c21a88f6cd3)
