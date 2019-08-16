
# Blossom Summer School 2019
## Tutorial on token creation and usage for supply chain management
### Offered by [Chaindrium](https://chaindrium.com)
<br/><br/><br/>

This repository has **three** parts. You can choose one of the three parts or do all the parts at this tutorial. However, we suggest that you do the parts in order, especially do the part for "For programmers" before doing the "For hard-coders" part. 
- For non-programmers
- For programmers
- For hard-coders

### For non-programmers
This tutorial is to demonstrate how payments can be made from one address to another address in the [Etheream Test Network](https://ropsten.etherscan.io/). This part of the tutorial is for those participants who have no programming expertise but would still like to experience first hand how transactions take place in Ethereum. It is also applicable for those who would like to ease into the tutorials by performing an easier tasks first. 

Please do the following:
- **Access an already prepared account** 
	- Go to the following website in your browser: https://www.myetherwallet.com/ 
	- Click on `Access My Wallet`
	- Click on `Software` 
	- Select `Mnemonic Phrase` and click on `continue`
	- Please give the 12 words that you can see on the beamer.
		- now, in `1`, please choose the testnet `ROP - myetherwallet.com` 
		- in `2`, please select on the top right hand corner `Ethereum Testnet (Ropsten)`
		- now, you should see a list with addresses and corresponding balance
		- choose one of the addresses with a balance greater than 0, then click on `Access My Wallet`
			- (We will coordinate to ensure that none of you end up choosing the same address)
		
- **Send A Single Transaction**
	- Take a look at your account balance. Then, click on `Send Transaction` in order to make a transaction
	- Please fill in the following fields
		- in the `To Address`, please add the address to which you would like to make the transaction to. You could choose the address of the person sitting next to you in order to make it easy to verify.
		- in `Amount`, please enter the amount you will like to send. Note that your account has a balance of approx. 0.5 ROP (The currency in the test network). Therefore, choose a value lesser than what you have in the account so that you have some money to pay as transaction fee too. Best to therefore enter a very low value so that you have more money to perform more experiments.  
	- Now, click on `Send Transaction`
	- A new window will open up. Here, you can double check the values and confirm the transaction. 

- **Done**, You have now successfully made a transaction to transfer money from one account to another. You will be able to view the transaction on the testnet in a few seconds. 

- **View the transaction on etherscan.io**
	- After confirming the transaction, please click on `Check Status on Etherscan.io`
	- Now, a new tab should open up with details of the transaction.
	- You can for example see the hash of your transaction
	- You can also take a look at the block in which your transaction was added and take a look at other transactions in there. 


<br/><br/><br/>

### For Programmers
This step by step tutorial is to demonstrate the creation of a token, transfer tokens and to retrieve some features of the token. It demonstrates the basic interactions one could perform with blockchain. This tutorial is for people familiar with programming. 
*In case you have any queries or require assistance, feel free to speak to me.*

#### Requirements: 
- python3.6
- Please install the following library:
	- `pip3 install web3`
- Alternatively, you could use python-virtualenv: `pip install virtualenv`
	- `source ./virtual_env/bin/activate`
	- You will now find yourseld in the python virtual environment

#### What are we going to develop here:
Let's assume that you have a Blossom-Tticket that you would like to gift someone. The person could further gift this ticket. However, you would like to know who has the ticket at any point of time. Let's develop this on blockchain. 

#### Let's do the following steps:

- Download the repository from https://github.com/chaindrium-inc/Blossom-SummerSchool-2019. You could either use `git clone` or click on `download` and then extract the files from the zip file. 
- go to `/src/01_basic/`

- **Create your own wallet**
	- Open the file `generate_wallet.py`
		- This will help create a wallet for you. Take a look at the code and the documentation. 
		- Change the variable `random_string`. This helps to create a secure wallet. 
	- Execute the file
		- You will now see that the script outputs an address. Copy and save this address. This is the address (it is in fact a public key) of your wallet and you will need it later. 
		- Moreover, the script has stored a file named `wallet/private.key`. In this file, you will find the private key for your address. Take care of this file. In case you lose this, you won't be able to access your wallet. Or in case some one else gets hold of this key, they can access your wallet and steal your coins. 
	- Note that everytime you rerun the script `generate_wallet.py`, a new wallet address is being generated and therefore the privat key in `wallet/private.key` is being overwritten.

- **Get some balance and create a new token**
	- You will need some ether in your account in order to perform transactions, i.e., to pay the transaction fee. 
		- Enter your address [here](https://faucet.ropsten.be/) to get an ether on the test network. 
		- Alternatively, enter your address [here](https://medienpad.de/p/chaindrium). I/We will try to send you some tokens. This can take a while. 
	- Now, take a look at the file `see_balance.py`. Replace the address variable with your address. When you run the file, you will be able to see your balance. 
	- As soon as your balance is above zero, you can go on with the next step.
		- In the mean time, you can also take a look at the token creation file `token_contract/NConfToken.sol`. This is the smart contact that we will use in the next step.

- **Set up a smart contract on Blockchain**
	- Take a look at the file `deploy_token.py`
		- you are going to deploy a smart contract on [Ethereum Test Network](https://ropsten.etherscan.io/)
	- You can observe that some variables are set in the first few rows. Most importantly, set the variable `token_name` to have the name of the token (e.g. Blossom_myname).
	- Execute the file
	- When everything works fine, you will get a hash code that represents your transaction.
	- Open [https://ropsten.etherscan.io/](https://ropsten.etherscan.io/) in your browser
		- In this webstie, you will be able to find all the blocks and transactions belonging to the test network. 		
	- In the search box, enter the hash of your transaction
	- You will be able to see your transaction now
	- Take a look at the `from` address. It should be your address since you deployed the smart contract.
	- In the `to` field, it should be the address of your smart contract
		- Copy this address (Tip: In order to ensure that the correct address is copied, best to click on the contract address and then when etherscan.io displays the contract details, copy the contract address from the top). Note, we refer to this as the token address sometimes later on. 

- **Check the name of the token**
	- Take a look at the file `get_token_name.py` 
	- Edit the variable `token_address`: enter the address of your token, i.e., the smart contract
	- Execute the file
	- You will now see that the name of your token is output
		- You could try to redo the experiment to get your partner's token's name

- **Check the owner of the token**
	- Take a look at the file `get_token_owner.py` 
	- Edit the variable `token_address`: Enter the address of your token here
	- Execute the file
	- You will be able to see the address of the owner of the token holder
		- You could redo the experiment for a different token, e.g., that of your partner(s)

- **Give the token to someone else**
	- Take a look at the file `send_token.py` 
	- Edit the variable `token_address`: Enter the address of your token here
	- Edit the variable `new_owner`: Enter the address of the person you want to give your token to
		- Best to find a partner with whom you can exchange your tokens
	- Execute the file
		- Now, the tokens should no longer belong to you, but it should belong to the person you send it to. 
			- Do the previos test `Check the owner of the token` to verify it. 
			- Also execute the file `see_balance.py` to check your balance. Some of it would have been used to execute the transaction. 

- **Done**
	- Take a look at your address in [https://ropsten.etherscan.io/](https://ropsten.etherscan.io/) 
		-Just enter your address in the search box 
		-You should be able to see your balance and the executed transactions. 

<br/><br/><br/>

### Für Hard-Coder
Die hier präsentierten Aufgaben sind so gestellt dass Sie mit dem Teil **Für ProgrammiererInnen** lösbar sein sollten. Hier werden Sie mit Absicht nicht an die Hand genommen sondern sollen selbst eine Anwendung für Blockchains entwickeln.
*Sollten Sie Fragen haben geben sie gerne Handzeichen oder sprechen uns direkt an.*

#### Was Sie benötigen: 
- python3.6
- installieren Sie folgende Python Bibliotheken:
	- `pip3 install web3`
- alternativ können Sie auch python-virtualenv benutzen: `pip install virtualenv`
	- `source ./virtual_env/bin/activate`
	- jetzt befinden Sie sich in einer Virtuellen Python3 Umgebung die wir für Sie vorbereitet haben


#### Was wollen wir hier entwickeln:
Wir stellen uns vor Sie sind Bauer (Produzent) und Sie verkaufen Bio-Kartoffeln. Diese Kartoffeln werden von Ihnen an eine Fabrik verkauft die daraus Wodka herstellt. Dieser Wodka wird dann von jemandem gekauft (Konsument).

Der Konsument würde gerne einige Informationen über den von Ihm gekaufen Wodka wissen:
- wer hat die Kartoffeln hergestellt
- wer hat aus den Kartoffeln Wodka gemacht
- sind die Kartoffeln aus Biologischer Erzeugung
- welche Sorte von Kartoffeln wurde für den Wodka genutzt

<br/><br/><br/>

**Tun Sie sich hierzu zu dritt oder zu mehreren zusammen, sodass einer von Ihnen der Produzent, einer von Ihnen die Fabrik und einer von Ihnen der Konsument ist.**

Alternativ können Sie auch so tun als ob sie alle 3 dieser Personen darstellen.

Wir werden im Weiteren Verlauf dieser Aufgaben diese drei Nutzerrollen "Produzent", "Fabrik" und "Konsument" nennen. 


- navigieren Sie zu `/src/01_advanced/`

#### Exercise 0:
Zur Modellierung dieser Supply-Chain benutzen wir einen Smart Contract (`potato`). Machen Sie sich mit `potato/potato.sol` vertraut. 
Es ist wichtig dass Sie verstehen was die Felder
- `producer`
- `factory`
- `is_vodka`
- `name`
- `owner`

machen 

und wie Sie mit den Funktionen 
- `constructor`
- `send`
- `set_factory`
- `to_vodka`
- `is_potato_vodka`
- `who_is_owner`
- `who_is_producer`
- `who_is_factory`
- `get_name`
- `is_bio_potato`

diese Felder beeinflussen/auslesen.

#### Exercise 1:
- Write code (`deploy_potato.py`) that deploys the `potato` Smart Contract on blockchain
- Ensure that all the variables required for the `potato` Smart Contract contractor is provided
	- For `string name`, you could use the name of a potato from  (https://de.wikipedia.org/wiki/Liste_von_Kartoffelsorten) 
	- The address of the producers is automatically set to the one executing the transaction. See `potato` Smart Contract where `producer = msg.sender` in the constructor does that. 
- Also print the transaction id
- Execute the file to create a `potato` smart contract

#### Exercise 2:
- Write code (`send_potato_to_factory.py`) to send the `potato` Smart Contract to the factory
- Execute the function to send the potato to the factory
- Note: Create a separate address for the factory and keep a copy of the address as well as the private key for Exercise 4

#### Exercise 3:
- Write code (`produce_vodka.py`) to call the function `to_vodka` in the `potato` Smart Contract
- Execute the function to convert the potato into vodka

#### Exercise 4:
- Write code (`send_vodka_to_consumer.py`) to send the vodka from the factory to the consumer
	- Note that the factory and consumer address is right
	- Execute it to send the vodka to the consumer

#### Exercise 5:
- Write code (`get_potato_information.py`) that calls the methods `is_vodka`, `get_producer`, `get_factory`, `get_name` and dispalys the results in the console. 
- Check if all the displayed information is correct

Have fun :)
