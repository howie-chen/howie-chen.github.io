---
title: 配置 OpenFortiVPN
date: 2025-03-02
---

1. Install OpenFortiVPN
    
    ```bash
    brew install openfortivpn
    ```
    
2. Install 1Password CLI
    
    ```bash
    brew install --cask 1password/tap/1password-cli
    op --version
    ```
    
3. Enable 1Password CLI
    1. Ensure 1Password 8.x has installed.
    2. Open 1Password, and go to “Preferences”.
    3. Locate “Security”, check “Touch ID”.
    4. Locate “Developer”, check "Biometric unlock for 1Password CLI”.
4. Setup 1Password CLI
    
    ```bash
    op vault ls
    ```
    
5. Create script entry
    1. New file under `/usr/local/bin`
        
        ```bash
        sudo touch /usr/local/bin/vpn
        sudo chmod +x /usr/local/bin/vpn
        sudo vi /usr/local/bin/vpn
        ```
        
    2. Enter file content:
        
        ```bash
        #! /bin/bash
        
        OP_ITEM_FOR_MAC=your-value
        OP_ITEM_FOR_VPN=your-value
        
        SUDO_PASSWORD=$(op item get $OP_ITEM_FOR_MAC --reveal --fields label=password)
        
        USER_NAME=$(op item get $OP_ITEM_FOR_VPN --fields label=username)
        PASSWORD=$(op item get $OP_ITEM_FOR_VPN --reveal --fields label=password)
        OTP_KEY=$(op item get $OP_ITEM_FOR_VPN --otp)
        
        VPN_ENDPOINT=abc.example.com:port
        VPN_TRUSTED_CERT=value-here
        
        echo "$SUDO_PASSWORD" | sudo -S openfortivpn $VPN_ENDPOINT \
                                        --trusted-cert $VPN_TRUSTED_CERT \
                                        --set-dns=0 \
                                        --pppd-use-peerdns=1 \
                                        -u $USER_NAME \
                                        -p $PASSWORD \
                                        --otp=$OTP_KEY
        ```
        
6. Verify script entry
    1. Run script
        
        ```bash
        vpn
        ```
        
    2. Authenticate with Touch ID
    3. Check terminal output
        
        ```bash
        INFO: Connected to gateway.
        INFO: Authenticated.
        INFO: Remote gateway has allocated a VPN.
        ...
        INFO: Interface ppp0 is UP.
        INFO: Setting new routes...
        ...
        INFO: Tunnel is up and running.
        ```