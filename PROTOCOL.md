# RES - Exercise-protocol-Design 2021

Authors : Bruno Da Rocha Carvalho

Date : 31.03.2021

---



#### What transport protocol do we use?

Nous utilisons le protocole TCP/IP car c'est celui utilisé par défaut par les sockets API de Java. C'est également un protocole de communication classique et très souvent utilisé.



#### How does the client find the server (addresses and ports)?

Lors de son lancement, le serveur indique son port d'écoute. Le client peut alors se connecter en initialisant un socket et indiquant une adresse IP et un port, il faudra donc indiquer l'adresse IP du serveur ainsi que le même port que celui sur lequel le serveur écoute. 

Le port utilisé pour la communication est le : **1440**



#### Who speaks first?

Le client initialise en premier la connexion au serveur, qui décide d'accepter ou non. 



#### What is the sequence of messages exchanged by the client and the server? (flow)

Client        ----------> Server
Connexion

Client        <---------- Server
                          Sends succesful or failure response

Client        ----------> Server
Sends operation

Client        <---------- Server
                          Send answer of the operation

Client        ----------> Server
Exit

Client        <---------- Server
                          Closes the connection



#### What happens when a message is received from the other party? (semantics)

The server needs to check the correct format of the request and also if the operation is valid or not.
If so, the server has to send either the result or an error.

#### What is the syntax of the messages? How we generate and parse them? (syntax)

Le client peut envoyer des opérations au serveur à l'aide des 3 commandes suivantes : 

Client : CALC (for connexion)

Server : ACK

Client : [OPE] VALUE1 VALUE2 (OPE could be ADD, SUB, MUL, etc...)

Server : RESULT VALUE3 or ERROR

Client : EXIT



#### Who closes the connection and when?

The client closes the connection when he has finished.