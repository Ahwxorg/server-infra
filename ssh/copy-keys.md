### Copy keys from SSH client to server

```ssh-copy-id earth
ssh earth
doas nvim /etc/ssh/sshd_config

# Change port to *custom port number here*
Port 22
AddressFamily inet
PermitRootLogin prohibit-psasword
MaxAuthTries 3
MaxSessions 1
