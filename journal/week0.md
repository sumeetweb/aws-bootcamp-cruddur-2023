# Week 0 — Billing and Architecture

I was able to complete the required assignments without any issue.


## Required Homework
- MFA enabled for root account, Created new IAM user account with administrator access IAM role
- Launched Cloudshell and created credentials for CLI access
- Created an billing alarm in Cloudwatch and setup a budget of 2 USD
- Raised a support ticket to increase limit of SNS budget for sending SMS
- Designed CI/CD Pipeline in Lucidchart

Lucid Chart Diagram Link:  
https://lucid.app/lucidchart/ec658c9d-567e-4b74-8b12-400505747f58/edit?viewport_loc=-1737%2C-446%2C2994%2C1373%2C0_0&invitationId=inv_dfab2ae7-0b0f-4844-bce5-c4341fa79a0f


### Installing AWS CLI
- [AWS CLI Installation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
- I had WSL installed on my machine, so I installed the AWS CLI on WSL. I also installed the AWS CLI on my Windows machine.
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
- I was managing multiple AWS accounts, so I used a tool called Leapp (https://docs.leapp.cloud/latest/installation/install-leapp/) to manage automatic switching between AWS accounts.
![image](https://user-images.githubusercontent.com/25149022/227637252-6dc6064f-1bb0-44e9-8ed5-b3c5052f8f71.png)

### 2 USD Billing Alarm Set on Account:
![image](https://user-images.githubusercontent.com/25149022/227644844-5b31f69a-0eb6-43c2-8628-86665606eb95.png)


### MFA Enabled on Root Account
![image](https://user-images.githubusercontent.com/25149022/227637018-25b10a55-afd4-417e-8249-11c3d1474a85.png)


### SNS Quota Increase Request
![image](https://user-images.githubusercontent.com/25149022/227644033-43748a51-3d2f-4ab1-9fca-9ad224567981.png)

## Additional Homework:
- [Napkin Design](https://i.imgur.com/Nae0LPB.jpg)

