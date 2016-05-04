TCP Client
==========

The demo illustrates the use of a Spring Integration (SI) to create a Client-Server Demo over TCP. Here we play a Game of Three where 2 players communicate with each other over TCP. Below is the gist of the game.

When a player starts, it incepts a random (whole) number and sends it to the second player as an approach of starting the game.
The receiving player can now always choose between adding one of {­1,0,1} to get to a number that is divisible by 3. Divide it by three. The resulting whole number is then sent back to the original sender. The same rule are applied until one player reached the number 1 (after the division). Both players plays automatically without user input. 

You can execute this server (Player 2) by executing the jar:

    $ java -jar TCPClient.jar

Alternatively, you can also execute the **Main** method in class *com.tcp.client.Main*. In both cases you should see the following console output:

	===== Player 2 =====
	Player 1 is unavailable.. trying again!!
	Player 1 is unavailable.. trying again!!

Once TCPServer (Player 1) has started, the game will start and end automatically as seen below.

    Found player 1!!
	Requesting player 1 to initiate the game
	Player 1 sent: 83
	Player 2 played: 1
	Player 1 sent: 9
	Player 2 played: 0

In this particular example, TCPServer (Player 1) wins. Below are the steps of how Player 1 won.

	1. Player 2 requested Player 1 to start the game
	2. Player 1 generated a random whole number sends the number 83 to Player 2
	3. Player 2 plays 1 and returns 28 to Player 1 (Calculation: 83 + 1 = 84 and 84 / 3 = 28)
	4. Player 1 plays -1 and returns 9 to Player 2 (Calculation: 28 + -1 = 27 and 27 / 3 = 9)
	5. Player 2 plays 0 and returns 3 to Player 1 (Calculation: 9 + 0 = 9 and 9 / 3 = 3)
	6. Player 1 plays 0 and wins the game (Calculation: 3 + 0 = 3 and 3 / 3 = 1)
