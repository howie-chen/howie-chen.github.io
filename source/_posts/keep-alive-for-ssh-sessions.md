---
title: 配置 SSH 会话时长
date: 2025-03-02
---

1. `vi ~/.ssh/config`
2. Add below line
    ```bash
    Host *
    	ServerAliveInterval 120
    ```
    

[How can I prevent an SSH session from hanging in OS X Terminal?](https://apple.stackexchange.com/questions/36690/how-can-i-prevent-an-ssh-session-from-hanging-in-os-x-terminal)