## Homework0 for the Security and Privacy

### Wang, Xusong	3375907

### Abdullahu, Shkodran 3466256

 	![image-20200426193057824](/home/xusong/.config/Typora/typora-user-images/image-20200426193057824.png)

==P2 Answers a:==

* As the picture below, the reason why Needham-Schroeder protocol cannot build a mutual authentication is that, there is no encrypted signature when Bob respond to Alice, but only encrypted $N_b$,  when Alice talks to the Eve whose private key also held by the adversary, the adversary could prevent to be Alice and talk with Bob, due to without the signature as identifier , Alice could not distinguish the message from Bob or Eve. 
* ![image-20200426193333681](/home/xusong/.config/Typora/typora-user-images/image-20200426193333681.png)* By adding the B (Signature from the Bob) , Alice could realize the trap and end the communication, therefore NSL protocol  can be proven to be secure .

![image-20200426195351802](/home/xusong/.config/Typora/typora-user-images/image-20200426195351802.png)



![image-20200426195732988](/home/xusong/.config/Typora/typora-user-images/image-20200426195732988.png)

==P2 Answer b==:

* Assuming that adversary Eve is the user of the computer network,  Eve is able to set up standard sessions with other agents. Actually agent Bob want to establish a session with Eve. In addition although the adversary Eve cannot encrypt messages, like $\{N_B\}_{k_B}^a$, but adversary Eve already has kept the messages down after Alice use $N_A$ to set up standard sessions at the first time.

* Attack on the protocol allows the Eve to impersonate agent B to set up a false session with A. Bob and Eve establish a valid session, however Eve  impersonate agent Bob to establish a fake session with Alice.

   Alice >>> $\{N_A, A\}^a_{k_B}$ 		>>> Eve >>>  $\{N_A, E\}_{k_B}^a$ 			>>> Bob
   Alice <<< $\{N_A, N_B, B\}_{k_A}^a$<<<  Eve <<<  $\{N_A, N_B, B\}_{k_E}^a$ 	<<< Bob

   Alice >>>$\{N_B\}^a_{k_B}$	     	  >>> Eve >>>  $\{N_B\}_{k_B}^a$ 			     >>> Bob

  Therefore the authentication is violated due to spoofing.

![image-20200427015116097](/home/xusong/.config/Typora/typora-user-images/image-20200427015116097.png)

==P3 Answer==:

* With shared key and without the identification, protocol above is easy to be attacked by Man-in-the-middle attack. For example:

  1. $$A \rightarrow E : \{N_A\}^s_k$$

  2. $$E \rightarrow B : \{N_A\}^s_k$$
  3. $$B \rightarrow E : \{N_B\}^s_k, N_A$$
  4. $$E \rightarrow A : \{N_B\}^s_k, N_A$$
  5. $$A \rightarrow E : N_B$$
  6. $$E \rightarrow B : N_B$$

* Adversary Eve just interpreted the messages between Alice and Bob, Alick thought she set up a session with Bob, but it is from the Eve who impersonate the Bob, the other way around as Bob, He set up a fake session with Eve as well, additionally the both Nonces are not encrypted. So authentication is violated.

![image-20200427095521474](/home/xusong/.config/Typora/typora-user-images/image-20200427095521474.png)

==P4 Answer:==

The essential of attack is to take use the fourth step, in precise to construct a suitable message, take the output from B in 2nd session, then sent it to B in 1st session.

Below is the message flow:

1.1.	$I(A) ->  B :   A ,B$

1.2. 	$B ->  I(A) :   B ,N_{B1}$

1.3.     $ I(A) ->  B :   Random-string$

1.4.	$B -> I(S) :Random - string, \{ A,B,B,N_{B_1} \}^s_{Kbs}$

2.1. 	$I(A) ->  B :   A ,N_{B1}$

2.2. 	$B ->  I(A) :   B ,N_{B2}$

2.3. 	$I(A) - > B:Random-string$

2.4.	$B -> I(S) :Random - string, \{ A,B,N_{B_1},N_{B_2}\}^s_{Kbs}$

1.5.	$I(S) -> B :Random - string, \{ A,B,N_{B_1},N_{B_2}\}^s_{Kbs}$

1.6.	$B -> I(A) :Random - string, \{ B, N_{B_1}\}N_{B_2}$

1.7.	$I(A) -> B :\{N_{B_1}\}N_{B_2}$




