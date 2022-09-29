![](https://images.unsplash.com/photo-1488590528505-98d2b5aba04b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8 )
### An easy to fallow tutorial for setting up a service for code-server.

As I mentioned here [article](https://dev.to/blitz_cloud/vscode-is-now-everywhere-5g9d), code-server lacks a service to run it in the background or at startup. I build a systemd service to solve this issue.

If you want to have the code-server running n the background just follow this steps:

- Just create this file with your favorite text editor.
```bash
/etc/systemd/system/code-service.service
```
- Paste the code below.
```
[Unit]
Description=Code-Server Service
After=network.target

[Service]
Type=simple
Restart=always
User= yourUser
ExecStart=/usr/local/bin/code-server

[Install]
WantedBy=multi-user.target
```
- Start the service
```bash
sudo service code-server start
```
- Check the status 
```bash 
sudo service code-server status
```
- Optional enable the process at startup
```bash
sudo systemctl enable code-server
```
#### Now you should be able to take you safe development environment on your iPad or on your grandma slow computer,without being afraid that the server will stop.
