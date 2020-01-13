//Auth@r Sylvain TANGUY


<h2> Cahier de suivi du projet PolyBee </h2>

<h3>Séance du Vendredi 25 Octobre </h3>

Pilotage de la séance Brainstorming

<h3>Inter-séance</h3>
  
recherche de composants
 
<h3>Séance du 08/11/2019 </h3>

  Apprentissage Github
  
  Finalisation du cahier des charges: partie Alimentation & Protocole
  
  Installation des modules IDE arduino pour ESP32

<h3>séance du 29/11/2019</h3>
  Recherche et test des librairies utiles à notre projet
    - Wifi
    - BLE
    - LoRa
    - LCD OLED

<h3>séance du 13/12/2019 </h3>

  Trade-off comparatif des différents protocoles orientés IoT utilisables pour notre projet: le websocket sera utilisé
 
<h3>Inter-séance</h3>
  Test du package applicatif TTGO V2 => fonctionnel
  Revue de mise en oeuvre websocket:
    - Nécessité d'installer des modules Apache mod_proxy_wstunnel et de composer (outil de téléchargement PHP de dépendances)
    - Le module apache configuré devra rediriger les requêtes ws:// ou wss:// vers le serveur websocket interne
 
 
 
 <h3>Séance du Vendredi 10 Janvier 2020 (Bonne année!) </h3>
  => La mise en oeuvre de ce type de service est trop complexe pour être proposée sur ce projet (vouée à être utilisée sur des providers gratuits, donc sans installations supplémentaires)
  
 => L'étude portera donc plus simplement sur un service PHP simple.
 
Les mesures seront à enregistrer dans les tables
mesure_ext
 -> paramètres de la table:
      masse (int(5) NOT NULL)
      tare (int(5) NOT NULL)
      temp_capteur	float(5,2)	
      nourriss_t	enum('sirop 50/50', 'sirop lourd', 'candy', 'modif')
      nourriss_q	int(5)
      vbat	float(5,2)
      date_enr	timestamp	 NOT NULL
      send_counter	int(1)
      FK_IdColonie	int(11)
      FK_IdCapteur	int(11)
      
mesure_int
  -> paramètres de la table:
      temp_1	float(5,2)	
      temp_2	float(5,2)	
      temp_3	float(5,2)
      hygro_1	float(5,2)	
      hygro_2	float(5,2)
      hygro_3	float(5,2)	
      vbat	float(5,2)	NOT NULL
      date_enr	timestamp	NOT NULL
      send_counter	int(1)
      FK_IdColonie	int(11)
      FK_IdCapteur	int(11)	
      
meteo
  -> paramètres de la table:
    	pres_atm	float(6,2)	
      temp	float(5,2)	
      hygro	float(5,2)
      vent_vit	float(5,2)	
      vent_vit_max	float(5,2)	
      vent_dir	int(3)
      pluie	float(5,2)	
      soleil	int(5)
      vbat	float(5,2)	NOT NULL
      date_enr	timestamp	NOT NULL
      send_counter	int(1)
      FK_IdRucher	int(11)
      FK_IdCapteur	int(11)
      
      
      Test des scripts PHP:
      http://rucher.polytech.unice.fr/~rucher/mesure_ext.php?masse=1&tare=2&temp_capteur=3&vbat=2.3
      
 <h3>interséance  </h3>
 pour l'utilisation de process concurents (ex: recevoir un message LORA pendant qu'on envoie des données au serveur), il y a possibilité d'utiliser les librairies FreeRTOS (https://icircuit.net/esp32-introduction-freertos/1297)

13-01-2020: compteur de coulombs low power: http://www.ti.com/product/BQ26231#


