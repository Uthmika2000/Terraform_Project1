### 1. Create vpc
### 2. Create Internet Gateway
### 3. Create Custom Route Table
### 4. Create a Subnet
### 5. Associate the subnet with the Custom Route Table
### 6. Create Security Group to allow port 22,80,443
### 7. Create a network Interface with an ip in the subnet that was created in step 4
### 8. Assign an elastic IP to the network interface created in step 7
### 9. Create Ubuntu server and install/enable apache2

#### Installed AWS  CLI version: aws-cli/1.16.133 Python/3.7 .(Restart VS Code after install)
- Commnad-1: Invoke-WebRequest -Uri https://awscli.amazonaws.com/AWSCLIV2.msi -OutFile $env:TEMP\AWSCLIV2.msi; Start-Process -Wait -FilePath msiexec -ArgumentList /i,$env:TEMP\AWSCLIV2.msi
#### Installed "jq" commnad line JSON processor. (Will install in your current working directory. Move 'jq.exe' to 'C:\Windows\System32' to use it anywhere.)
- Commnad-2: Invoke-WebRequest -Uri https://github.com/stedolan/jq/releases/download/jq-1.6/jq-win64.exe -OutFile jq.exe
#### Used AWS Secrets Manager. (Make sure to use your 'my-reigon' and your 'my-secret-arn')
- Command-3: aws secretsmanager get-secret-value --region my-reigon --secret-id my-secret-arn | jq -r '.SecretString' > .env

#### If previous commnad (Command-3) is not working, then assign your credentials using 'aws configure' command (give 'json' as output format) and run previous command(Command-3) again.

#### source .env  # Load environment variables from the .env file
#### terraform apply --auto-approve

