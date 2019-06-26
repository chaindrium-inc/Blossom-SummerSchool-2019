
# Blossom Summer School 2019
## Tutorial on token creation and usage
### von [Chaindrium](https://chaindrium.com)
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
Diese Anleitung begleitet Sie anhand eines Beispiels durch den Prozess Entitäten auf der Blockchain zu erstellen, zu versenden und Daten dieser Entitäten von der Blockchain zu holen. Dieses Projekt erklärt die Basis auf der mit einer Blockchain interagiert werden kann. Es richtet sich explizit an TeilnehmerInnen die Erfahrung mit Programmierung haben und nicht davor zurück schrecken selbst Hand an den Code zu legen.
*Sollten Sie Fragen haben geben sie gerne Handzeichen oder sprechen uns direkt an.*

#### Was Sie benötigen: 
- python3.6
- installieren Sie folgende Python Bibliotheken:
	- `pip3 install web3`
- alternativ können Sie auch python-virtualenv benutzen: `pip install virtualenv`
	- `source ./virtual_env/bin/activate`
	- jetzt befinden Sie sich in einer Virtuellen Python3 Umgebung die wir für Sie vorbereitet haben

#### Was wollen wir hier entwickeln:
Nehmen wir an Sie haben ein NConf-Ticket das Sie gerne jemandem schenken würden. Diese Person könnte das Ticket ja auch weiter verschenken. Sie würden aber gerne wissen wer das Ticket letztendlich besitzt. Diesen Prozess würden wir gerne auf einer Blockchain abbilden.

#### Dazu sind die folgenden Schritte nötig:

- laden Sie das Repository von https://github.com/chaindrium-inc/NConf-Workshop-2019 herunter. Sie können `git clone` verwenden oder einfach auf github.com `download` klicken und das zip Archiv entpacken.
- navigieren Sie zu `/src/01_basic/`

- **Erzeugen eines eigenen Wallets**
	- Öffnen Sie die Datei `generate_wallet.py`
		- Hier wird ein Wallet für Sie generiert, Sie sind dazu eingeladen den Code anhand der Dokumentation nach zu vollziehen
		- ändern Sie die Variable `random_string`, diese hilft dabei ein besonders sicheres Wallet zu generieren.
	- Führen Sie die Datei aus
		- Jetzt sollten Sie von dem Skript eine Adresse zurück geliefert bekommen haben, kopieren und speichern Sie diese Adresse, Sie werden sie später noch brauchen
		- Außerdem hat das Skript eine die Datei `wallet/private.key` erzeugt. In dieser befindet sich Ihr privater Schlüssel. Passen Sie gut auf diese Datei auf. Sollten Sie den Schlüssel verlieren, dann haben Sie keine Möglichkeit mehr auf Ihr Wallet zu zu greifen.
	- Da das Skript Ihre `wallet/private.key` Datei überschreibt sollten Sie es lediglich einmal ausführen

- **Guthaben kaufen und abfragen**
	- Sie brauchen Guthaben auf Ihrem Wallet da Transaktionen Gebühren kosten, sonst können Sie keine Transaktionen ausführen
		- Tragen Sie Ihre generierte Addresse [hier](https://medienpad.de/p/chaindrium) ein. Wir werden Ihnen dann etwas Guthaben schenken, damit Sie weiter arbeiten können. Dies kann allerdings einen Moment in Anspruch nehmen.
	- Jetzt können Sie die Datei `see_balance.py` ansehen und (nach dem Sie Ihre Addresse eingefügt haben) ausführen, dann sollten Sie das Aktuelle Guthaben ihres Wallets sehen
	- Sobald Ihr Guthaben großer als 0 ist können Sie mit dem nächsten Schritt fortfahren
		- in der Zwischenzeit könne Sie ja mal einen Blick auf die Datei `token_contract/NConfToken.sol` werfen. Das ist der Smart Contract den wir gleich auf die Blockchain laden werden.

- **Einen Smart Contract auf der Blockchain erstellen**
	- Schauen Sie sich hierzu die Datei `deploy_token.py` an
		- Sie erstellt einen Smart Contract auf dem [Ethereum Test Netzwerk](https://ropsten.etherscan.io/)
	- Hier können Sie in den ersten Zeilen sehen dass einige Variablen gesetzt werden. Vor allem die Variable `token_name` sollten Sie anpassen um Ihrem Token einen eigenen Namen zu geben.
	- Führen Sie die Datei aus
	- Wenn alles geklappt hat sollte die Datei Ihnen einen Hash-Wert Ihrer gerade erzeugten Transaktion anzeigen
	- Öffnen Sie [https://ropsten.etherscan.io/](https://ropsten.etherscan.io/) in Ihrem Browser
		- Auf dieser Website können Sie alle Blöcke und Transaktionen der "Test-Blockchain" sehen
	- Geben Sie in die Suchleiste den Hash Ihrer Transaktion ein
	- Jetzt sollten Sie Ihre Transaktion sehen können
	- vergleichen Sie die `from` Adresse mit der Ihren. Die Adressen sollten Identisch sein.
	- unter `to` sollten Sie die Adresse des von Ihnen erzeugten Smart Contracts sehen
	- kopieren Sie diese

- **Den Namen des Tokens abfragen**
	- Schauen Sie sich hierzu die Datei `get_token_name.py` an
	- ändern Sie die Variable `token_address`, tragen Sie dort die Adresse Ihres Tokens ein
	- Führen Sie die Datei aus
	- Jetzt sollte Ihnen das Skript den Namen Ihres Tokens anzeigen
		- Vielleicht finden Sie ja einen Partner dessen Token Namen Sie auch abfragen können

- **Den Besitzer des Tokens abfragen**
	- Schauen Sie sich hierzu die Datei `get_token_owner.py` an
	- ändern Sie die Variable `token_address`, tragen Sie dort die Adresse Ihres Tokens ein
	- Führen Sie die Datei aus
	- Jetzt sollte Ihnen das Skript den Besitzer Ihres Tokens anzeigen
		- Vielleicht finden Sie ja eine(n) PartnerIn dessen Token Besitzer Sie auch abfragen können

- **Ihr Token jemandem anderen geben**
	- Schauen Sie sich hierzu die Datei `send_token.py` an
	- ändern Sie die Variable `token_address`, tragen Sie dort die Adresse Ihres Tokens ein
	- ändern Sie die Variable `new_owner`, tragen Sie dort die Adresse desjenigen ein dem Sie das Token geben möchten
		- Vielleicht finden Sie ja einen Partner mit dem Sie Tokens tauschen können
	- Führen Sie die Datei aus
		- jetzt sollte das Token nicht mehr Ihnen gehören, sondern der Person der Sie das Token gegeben haben. Dies können Sie mit den Schritten unter "Den Besitzer des Tokens abfragen" nachvollziehen

- **Fertig**
	- Sollten Sie noch Zeit und Muße haben können Sie jetzt 
		- entweder mit dem Advanced Teil fortfahren 
		- oder sie schauen sich unter [https://ropsten.etherscan.io/](https://ropsten.etherscan.io/) Ihre Addresse an
			- geben Sie dazu einfach ihre Adresse in das Suchfenster ein
			- hier sollten Sie jetzt einen Überblick über Ihr Guthaben und die von Ihnen ausgelösten, bzw. Erhaltenen Transaktionen sehen


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

#### Aufgabe 0:
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

#### Aufgabe 1:
- Erstellen Sie eine Datei (`deploy_potato.py`) die den `potato` Smart Contract mit der von Ihnen generierten Adresse auf der Blockchain erstellt
- Geben Sie dem Constructor des `potato` Smart Contracts 
	- sowohl einen `string name` der den Namen der Kartoffel darstellt (https://de.wikipedia.org/wiki/Liste_von_Kartoffelsorten) 
	- die addresse des producers ist automatisch der ersteller des Smart Contracts (`producer = msg.sender` im Constructor des Smart Contracts)
- erzeugen Sie eine Transaktion die den Contract auf der Blockchain erstellt
- geben Sie den Hash der Transaktion am Ende Ihres Skriptes aus

- Erzeugen Sie einen `potato` Smart Contract auf der Blockchain

#### Aufgabe 2:
- Erstellen Sie eine Datei (`send_potato.py`) die den `potato` Smart Contract an die Fabrik sendet
- Senden Sie den in Aufgabe 1 erzeugten `potato` Smart Contract an die Fabrik

#### Aufgabe 3:
- Erstellen Sie eine Datei (`produce_vodka.py`) die auf dem `potato` Smart Contract die Methode `to_vodka` aufruft
- Benutzen Sie die Datei um aus der in Aufgabe 1 erzeugten Kartoffel Wodka zu machen

#### Aufgabe 4:
- Senden Sie (in dem Fall die Fabrik) den Wodka an den Konsumenten 
	- verwenden Sie hierzu das Skript aus Aufgabe 2

#### Aufgabe 5:
- Erstellen Sie eine Datei (`get_potato_information.py`) die die Methoden `is_vodka`, `get_producer`, `get_factory`, `get_name` aufruft und das Ergebnis in der Konsole anzeigt.
- Führen Sie die Datei aus und überprüfen Sie ob alle Informationen korrekt sind


Viel Spass und Erfolg :)
