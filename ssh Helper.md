## SSH Key generieren

ˋˋˋ
ssh-keygen -t ed25519 \
  -a 420 \
  -f ~/.ssh/demo.ed25519 \
  -C "Kommentar"
ˋˋˋ

## Key kopieren 
ssh-copy-id \
  -i ~/.ssh/demo.ed25519.pub \
  demo

## Bsp SSH Config

Host demo bastion
  HostName ssh.example.com 
  User TH 
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/demo.ed25519
  
Host internal 
  HostName target.local 
  ProxyJump bastion 
  User TH 
  PreferredAuthentications publickey 
  IdentityFile ~/.ssh/demo.ed25519
  
SSH -i <key> <host>
