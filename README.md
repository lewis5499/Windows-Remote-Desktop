---


使用 Github 开源的 frp 进行内网穿透, 以服务于 Windows 远程桌面。

step 1: 在具有公网 ip 的服务器:A 上解压 "*_server.zip", 在 "frps.toml" 中配置暴露的 port 和 token, 然后双击 "run_frp_server.bat".
step 2: 在被控端 PC:B 上解压 "*_client_visitor.zip", 在 "frpc.toml" 中配置服务器公网 ip 与服务器暴露的 port, 设置本地 3389 远控端口的转发, 设置 sk, 然后双击"run_frp_client.bat", 要终止远控端口转发则双击"kill_frp_client.bat".
step 3: 在要使用远控的 pc:C 上解压 "*_client.zip", 在 "frpc.toml" 中配置服务器公网 ip 与服务器暴露的 port, 设置与计算机 B 相同的 sk. 可随意设置合理的 bindPort, 这里假定为 7089, 然后双击"run_frpc_visitor.bat"
step 4: 在要使用远控的 pc:C 上打开 Windows 远程桌面, 输入 "127.0.0.1:7089" 即可进行远程桌面连接. Windows默认远程桌面帧率为30Hz, 可以改为60Hz. 详见: https://zhuanlan.zhihu.com/p/492662854


---

**Using GitHub Open-Source FRP for Remote Desktop Through NAT**

**Step 1: Set Up FRP Server on Public IP Server (A)**
1. Extract `*_server.zip` to a directory on the server with a public IP address.
2. Edit the `frps.toml` file:
   - Configure the exposed port and token.
3. Run the server by double-clicking `run_frp_server.bat`.

**Step 2: Set Up FRP Client on Controlled PC (B)**
1. Extract `*_client_visitor.zip` to a directory on the controlled PC.
2. Edit the `frpc.toml` file:
   - Specify the public IP address and exposed port of the server.
   - Configure the local RDP port (default is 3389) for forwarding.
   - Set the secret key (`sk`).
3. Start the client by double-clicking `run_frp_client.bat`.
4. To stop the RDP port forwarding, double-click `kill_frp_client.bat`.

**Step 3: Set Up FRP Client on Remote Access PC (C)**
1. Extract `*_client.zip` to a directory on the remote access PC.
2. Edit the `frpc.toml` file:
   - Specify the public IP address and exposed port of the server.
   - Use the same secret key (`sk`) as configured for PC B.
   - Set a reasonable `bindPort`, e.g., 7089.
3. Start the client by double-clicking `run_frpc_visitor.bat`.

**Step 4: Connect to Remote Desktop**
1. On the remote access PC (C), open Windows Remote Desktop Connection.
2. Enter `127.0.0.1:7089` as the connection address.
3. Proceed with the RDP connection.

**Note:** Windows default RDP frame rate is 30Hz. You can change it to 60Hz for smoother performance. For more details, refer to this guide: [Changing RDP Frame Rate](https://zhuanlan.zhihu.com/p/492662854).

---

This translation maintains the original instructions while ensuring clarity and accuracy in English.