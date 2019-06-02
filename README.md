# Sécurité des réseaux sans fil

## Laboratoire 802.11 Sécurité WPA Entreprise

__Auteurs: Doriane Tedongmo && Lopes Gouveia Miguel Angelo__



## Travail à réaliser

### 1. Capture et analyse d’une authentification WPA Entreprise

La capture que nous utilisons ici, est une capture qui nous a été donné par Dejvid Muaremi. Nous n'avons pas réussi à en capturer une.

- Requête et réponse d’authentification système ouvert

  ![](images\request_response1.JPG)

  ![request_response2](images\request_response2.JPG)

  

- Phase d’initiation. Arrivez-vous à voir l’identité du client ?

  Oui, on la voit dans la réponse d'authentification.

- Phase hello :

  - Version TLS

    ![](images\tls.JPG)

  - Suites cryptographiques et méthodes de compression proposées par le client et acceptées par l’AP

    ![](images\ciphersuite.JPG)

    ![](images\ciphersuiteServer.JPG)

  - Nonces

    Random: 7c0d7e80efe895e8e34473700c8d1d72762291ee5382794481cfa09e67a2771e

  - Session ID

    Session ID: 7d9ac6b00902a5feb70712cddab483d00e3f7ee242657347db2ce5af83a69e1e

- Phase de transmission de certificats

  ![](images\certificat.JPG)

  ![](images\change.JPG)

- Authentification interne et transmission de la clé WPA (échange chiffré, vu comme « Application data »)

  ![](images\authenti.JPG)

- 4-way hadshake

  Pas de 4-way hadshake dans notre capture

### Répondez aux questions suivantes :

> **_Question :_** Quelle ou quelles méthode(s) d’authentification est/sont proposé(s) au client ?
>
> **_Réponse :_** EAP-TLS et EAP-PEAP
>
> ![](images\methode_co.JPG)

---

> **_Question:_** Quelle méthode d’authentification est utilisée ?
>
> **_Réponse:_** EAP-PEAP
>
> ![](images\type.JPG)

---

> **_Question:_** Lors de l’échange de certificats entre le serveur d’authentification et le client :
> 
> - Le serveur envoie-t-il un certificat au client ? Pourquoi oui ou non ?
> 
> **_Réponse:_** Oui, le serveur doit envoyer son certificat pour s'authentifier auprès du client.
> 
> - b.	Le client envoie-t-il un certificat au serveur ? Pourquoi oui ou non ?
> 
> **_Réponse:_** Non, car la méthode utilisé est EAP-PEAP, il aurait un envoyé un certificat si la méthode était EAP-TLS.

---

### 2. Attaque WPA Entreprise

### Répondez aux questions suivantes :

> **_Question :_** Quelles modifications sont nécessaires dans la configuration de hostapd-wpe pour cette attaque ?
> 
> **_Réponse :_**  Le channel, le ssid et l'interface

---

> **_Question:_** Quel type de hash doit-on indiquer à john pour craquer le handshake ?
> 
> **_Réponse:_**  Netntlm

---

> **_Question:_** 6.	Quelles méthodes d’authentification sont supportées par hostapd-wpe ?
>
> **_Réponse:_** Les méthodes viennent de la [documentation de hostapd-wpe](https://tools.kali.org/wireless-attacks/hostapd-wpe)
>
> 1. EAP-FAST/MSCHAPv2 (Phase 0)
>
> 2. PEAP/MSCHAPv2
>
> 3. EAP-TTLS/MSCHAPv2
>
> 4. EAP-TTLS/MSCHAP
>
> 5. EAP-TTLS/CHAP
>
> 6. EAP-TTLS/PAP




## Livrables

Un fork du repo original . Puis, un Pull Request contenant :

-	Captures d’écran + commentaires
-	Réponses aux questions
