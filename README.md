# AuthoraCoin
Shell script to install a [AuthoraCoin](http://authoracoin.com/) Masternode on a Linux server running Ubuntu 16.04. Use it on your own risk.
***

## Installation
```bash
sudo apt update
sudo apt install -y wget curl
wget -N https://raw.githubusercontent.com/authoracoin/masternodes/master/authora_install.sh
bash authora_install.sh
```
Wait until you request "Private Key" and paste your "masternode genkey" generated in the following steps.
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the AuthoraCoin Desktop Wallet.  
2. Go to RECEIVE and create a New Address: (Example): **MN1**  
3. Send **5000** ATHR to **MN1**. You need to send all 5000 coins in one single transaction.
4. Wait for 15 confirmations.  
5. Go to **Tools -> "Debug Window - Console"**  
6. Type the following command and copy the generated key to Notepad: **masternode genkey**  And **masternode outputs**
(Use **masternode genkey** in the VPS when you request "Private Key").
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:23854**
* Privkey: **Masternode Private Key**
* TxHash: **First value from masternode outputs**
* TxIndex:  **Second value from masternode outputs**
```
Example: 
mn1 127.0.0.1:23854 2TqeXaU8k3n8mgbAieGUGgUHHtpGFz4nnrwKEz1ss1vHzm1dS3K 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 0

```
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is un
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```bash
masternode start-alias MN1
```
14. Login to your VPS and check your masternode status by running the following command:
```bash
authoracoin-cli masternode status
```
***

## Usage:
```bash
authoracoin-cli masternode status  
authoracoin-cli getinfo
```
Also, if you want to check/start/stop **ATHR**, run one of the following commands as **root**:

```bash
systemctl status AuthoraCoin #To check if AuthoraCoin service is running  
systemctl start AuthoraCoin #To start AuthoraCoin service  
systemctl stop AuthoraCoin #To stop AuthoraCoin service  
systemctl is-enabled AuthoraCoin #To check if AuthoraCoin service is enabled on boot  
```  
***

## Uninstall:
```bash
bash authora_install.sh uninstall
``` 

Credits:
https://github.com/zoldur
