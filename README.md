
---

# 使用 GitHub 开源的 FRP 进行内网穿透，以服务于 Windows 远程桌面

## 步骤 1: 在具有公网 IP 的服务器 (A) 上设置 FRP 服务器
1. 将 `*_server.zip` 解压到具有公网 IP 地址的服务器上的一个目录。
2. 编辑 `frps.toml` 文件：
   - 配置暴露的端口和 token。
3. 双击 `run_frp_server.bat` 运行服务器。

## 步骤 2: 在被控端 PC (B) 上设置 FRP 客户端
1. 将 `*_client_visitor.zip` 解压到被控 PC 上的一个目录。
2. 编辑 `frpc.toml` 文件：
   - 指定服务器的公网 IP 地址和暴露的端口。
   - 配置本地 RDP 端口（默认为 3389）进行转发。
   - 设置密钥 (`sk`)。
3. 双击 `run_frp_client.bat` 启动客户端。
4. 要终止 RDP 端口转发，双击 `kill_frp_client.bat`。

## 步骤 3: 在要使用远控的 PC (C) 上设置 FRP 客户端
1. 将 `*_client.zip` 解压到要使用远程桌面的 PC 上的一个目录。
2. 编辑 `frpc.toml` 文件：
   - 指定服务器的公网 IP 地址和暴露的端口。
   - 使用与计算机 B 相同的密钥 (`sk`)。
   - 设置一个合理的 `bindPort`，这里假设为 7089。
3. 双击 `run_frpc_visitor.bat` 启动客户端。

## 步骤 4: 连接到远程桌面
1. 在要使用远控的 PC (C) 上打开 Windows 远程桌面连接。
2. 输入 `127.0.0.1:7089` 作为连接地址。
3. 点击“连接”以进行远程桌面连接。

**注意:** Windows 默认远程桌面帧率为 30Hz。您可以将其更改为 60Hz 以获得更流畅的体验。详细信息请参阅此指南：[更改 RDP 帧率](https://zhuanlan.zhihu.com/p/492662854)。

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
