# DEN
DEN NODES BLOCKCHAIN


##Mine for blocks with your Windows wallet and the following instructions.

Click here to download the file dennodes-qt-windows.zip.

Open File Explorer and go to your downloads directory.

Extract the zip file dennodes-qt-windows.zip

Open "Run" with the keyboard shortcut winkey + r.

Enter the following text behind "Open": notepad

Press on the button "OK".

Paste the following into notepad.
addnode=den.denodes.com
addnode=den1.denodes.com

Click on the menu item "File" -> "Save As...".

The open dialog box will appear, click on "Save as type" and select the option "All Files (*.*)".

Enter the following text behind "File name": dennodes.conf

Click on the menu bar, type the following text %appdata% and press on the enter key. enter

Create the folder DENNODES and open the folder.

Press on the button "Save".

Open your wallet.

Go to Tools -> Debug console.
This is the console where you execute RPC commands.

Type the following command, to mine your first block:
setgenerate true -1



## Install Master Node 

Install a masternode on Ubuntu Server 18.04 with the following tutorial.

Open your Windows wallet.

Go to Tools -> Debug console.

Type the following RPC command, to create private key for your masternode:
createmasternodekey

Example output
75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo

Type the following RPC command, to create an address for the masternode amount fee:
getaccountaddress "MN1"

Example output
TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5

Go back to your wallet overview

Press on the toolbar button "Send".

Enter the address from the RPC command “getaccountaddress "MN1"” behind the text "Pay To:". (Example: TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5)

Enter the following amount of coins behind the text "Amount:": 5000

Press on the button "Send".

Wait until the transaction is confirmed by 20 blocks.

Go back to the console of your wallet.

Identify the transaction with the following RPC command:
getmasternodeoutputs

Example output
{
 "fdab9dff1ff9caf5d291905ad43b9f7d69775189d4d22cb085d7fedd94ea1c6a": "0"
}

Go to Tools -> Open Masternode Configuration File.

Paste the following text into notepad.
MN1 203.0.113.53:10206 75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo 06e38868bb8f9958e34d5155437d009b72dff33fc28874c87fd42e51c0f74fdb 0

MN1 - Alias for your masternode.

203.0.113.53 - External IPv4 address of your VPS.

75eqvNfaEfkd3YTwQ3hMwyxL2BgNSrqHDgWc6jbUh4Gdtnro2Wo - Private masternode key from the RPC command “createmasternodekey”.

06e38868bb8f9958e34d5155437d009b72dff33fc28874c87fd42e51c0f74fdb - Transaction hash from the RPC command “getmasternodeoutputs”.

0 - Single digit from the RPC command “masternode outputs”.

Save and close notepad.

Close your wallet.

Open putty and connect using SSH with your Ubuntu 18.04 server.

Update your Ubuntu server with the following command:
sudo apt-get update && sudo apt-get upgrade -y

Install the required dependencies with the following command:
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common cmake -y

Install the repository ppa:bitcoin/bitcoin with the following command:
sudo add-apt-repository ppa:bitcoin/bitcoin

Confirm the installation of the repository by pressing on the enter key. enter

Install Berkeley DB with the following command:
sudo apt-get update && sudo apt-get install libdb4.8-dev libdb4.8++-dev -y

Download the Linux daemon for your wallet with the following command:

Extract the tar file with the following command:
tar -xzvf dennodes-daemon-linux.tar.gz

Download the Linux tools for your wallet 

Extract the tar file with the following command:
tar -xzvf dennodes-qt-linux.tar.gz

Type the following command to install the daemon and tools for your wallet:
sudo mv dennodesd dennodes-cli dennodes-tx /usr/bin/

Create the data directory for your coin with the following command:
mkdir $HOME/.dennodes

Open nano.
nano $HOME/.dennodes/dennodes.conf -t

Paste the following into nano.
rpcuser=rpc_dennodes
rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
maxconnections=64
masternode=1
masternodeprivkey=0acbf6f183d0c9b794b9bc0dba25f8a1a1eca21aa4f2e4a86ecd3120a59efb35
externalip=203.0.113.53

203.0.113.53 - External IPv4 address of your VPS.

0acbf6f183d0c9b794b9bc0dba25f8a1a1eca21aa4f2e4a86ecd3120a59efb35 - Private masternode key from the RPC command “createmasternodekey”.

Save the file with the keyboard shortcut ctrl + x.

Type the following command to start your daemon:
dennodesd

Open your Windows wallet.

Go to Tools -> Debug console.

Type the following RPC command, to start your masternode:
startmasternode alias false MN1


##Installing Node Only 
nstall a node for on Ubuntu Server 18.04 with the following tutorial.

Update your Ubuntu server with the following command:
sudo apt-get update && sudo apt-get upgrade -y

Install the required dependencies with the following command:
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common cmake -y

Install the repository ppa:bitcoin/bitcoin with the following command:
sudo add-apt-repository ppa:bitcoin/bitcoin

Confirm the installation of the repository by pressing on the enter key. enter

Install Berkeley DB with the following command:
sudo apt-get update && sudo apt-get install libdb4.8-dev libdb4.8++-dev -y

Download the Linux daemon 

Extract the tar file with the following command:
tar -xzvf dennodes-daemon-linux.tar.gz

Download the Linux tools 

Extract the tar file with the following command:
tar -xzvf dennodes-qt-linux.tar.gz

Type the following command to install the daemon and tools for your wallet:
sudo mv dennodesd dennodes-cli dennodes-tx /usr/bin/

Create the data directory for your coin with the following command:
mkdir $HOME/.dennodes

Open nano.
nano $HOME/.dennodes/dennodes.conf -t

Paste the following into nano.
rpcuser=rpc_dennodes
rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2
rpcallowip=127.0.0.1
listen=1
server=1
txindex=1
daemon=1

Save the file with the keyboard shortcut ctrl + x.

Type the following command to start your node:
dennodesd
