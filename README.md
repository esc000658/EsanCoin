# EsanCoin: A Cryptocurrency to Learn about Cryptocurrencies

EsanCoin is a fork of SmallChange (which is a fork of LiteCoin itself). It was created for educational purposes. With this we aim to i) 
prove that really anyone(!) can start a Litecoin/Bitcoin based currency; and ii) allow users to experiment with coin parameters (in a private network).
 
We don't take any credit for the develop of the coding, outside the few changes we made. All credit goes to the creator of LiteCoin and SmallChange.

## Details
EsanCoin is  a 'faster' version of Litecoin which uses scrypt as a Proof-of-Work scheme and is intended for microtransactions.

 - 30 seconds block targets
 - 4 567 680 total coins
 - no subsidy after approximately 5 years;
    in between: 10 coins per generated block
 - difficulty retargets every 5 min
 - currently peers are looked up over IRC only
 - currently no block checkpoints are in the code (easy to include)

## References
`LearnCoin`
`SmallChange`
`Litecoin`

## Usage - Development process

### Preparing my development environment

For you can work with EsanCoin is necessary that you install the next libraries over Ubuntu 14 -Linux.

```
$ sudo apt-get install git
$ sudo apt-get install libboost-dev
$ sudo apt-get install libboost-system-dev
$ sudo apt-get install libboost-program-options-dev
$ sudo apt-get install libboost-thread-dev
$ sudo apt-get install libboost-filesystem-dev
$ sudo apt-get install libcurl4-openssl-dev
$ sudo apt-get install libdb5.1-dev
$ sudo apt-get install libdb5.1++-dev
$ sudo apt-get install qt-sdk
$ sudo apt-get install libminiupnpc-dev
$ sudo apt-get install build-essential
$ sudo apt-get install openssl
```

Since it is necessary to have two machines running in a common network, we will use virtual machines in a VMWare environment (but you can use any other alternative to emulate operating systems). To download vmware player use the following links:

- for [Linux][Linux] or [here][Here]
- for [Windows][Windows] or [here][Here]
- for [Mac][Mac]

The OS with all the required libraries (previously listed) is available at Mega - [Ubuntu 14][Ubuntu 14]. After downloading,  create a copy of the file and install two machines in VMWare (each one started from a different file).

- User: esan
- Password: esan

### Cloning EsanCoin
On each virtual machine, open the terminal and download the project.
```
$ git clone https://github.com/esc000658/EsanCoin.git
```

### Installing EsanCoin
In the project, enter `.../EsanCoin/src` in a terminal window and execute:
```
$ make -f makefile.unix	// creates wallet
$ ./EsanCoin	// asks for a user and a password
```
If everything went well, you will see a message requesting a user and password for your EsanCoin wallet

### Setting up our credentials
In the directory of your OS enter  `./EsanCoin` and within this directory, create a file called `EsanCoin.conf` that contains the following:
```
	rpcuser=<<unique_user>>
	rpcpassword=<<unique_password>>
	addnode=<<IP_of_the_other_computer>>
```

### Mining
This is the process by which the miners receive rewards, to start the mine in EsanCoin return to `.../EsanCoin/src` in the terminal and execute:
```
# First we need run our node:
$ ./EsanCoin & // starts the service (you are already a node)
$ ./EsanCoin getinfo // information about the node

# Now we can star the mining:
$ ./EsanCoin setgenerate true 4 // start mining using multi-threads
$ ./EsanCoin getmininginfo // information about the mining
$ ./EsanCoin getbalance // check the account balance
```
Note: Mining is not necessary, but to run your node is necessary in every computer.

### Making transactions
After starting the mining we wait until we have some money to start our transactions.
```
# First we need create an account:
$ ./EsanCoin getnewaddress "name_of_account"
$ ./EsanCoin listaccounts

# Now we make our first transaction
$ ./EsanCoin move "" "name_of_account" "amount"
$ ./EsanCoin sendtoaddress "address_of_wallet" "amount"

# Making transactions of some account to other account
$ ./EsanCoin sendfrom "address_name" "address_of_wallet" "amount"

$ ./EsanCoin gettransaction "transaction_hash"
```
### Queries in the BlockChain
To see the blocks and transactions, we can use:
```julia
$ ./EsanCoin listsinceblock
$ ./EsanCoin listtransactions
$ ./EsanCoin listunspent
```

## Warning
EsanCoin should not be used as a real cryptocurrency. All of the coin parameters are chosen arbitrarily or at most with 'fairness' towards everyone in mind. Again, this EsanCoin exists becuse:
 -  proves that really anyone(!) can start a Litecoin/Bitcoin based currency (just look at the changes I applied to the original Litecoin source, for genesis block generation look at main.cpp)
 - allowed us to experiment with coin parameters (in a private network)

## keywords
`EsanCoin`
`Cryptocurrency`


[Linux]:https://www.vmware.com/products/workstation-for-linux.html
[Windows]:https://www.vmware.com/products/workstation.html
[Mac]:https://www.vmware.com/products/fusion.html
[Aqui]: https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0
[Ubuntu 14]:https://mega.nz/#!5vpFWCZS!lfyKNxBqTHriyihUsrMtVtPE2tX3CmhKTBMWnDJ0-bQ
