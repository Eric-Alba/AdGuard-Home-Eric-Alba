# Pràctica 0378: Tallafocs - AdGuard Home

**Alumne:** Eric Alba (naipeer)  
**Centre:** Institut El Calamot  
**Curs:** 2025-2026

---

## 1. Introducció
Aquesta pràctica consisteix en el desplegament d'**AdGuard Home** mitjançant Docker. Aquest sistema actua com un servidor DNS amb filtratge a nivell de xarxa, permetent gestionar polítiques sobre les consultes DNS dels clients. 

Encara que no és un tallafoc clàssic de capa 3/4, comparteix funcions clau de seguretat com el filtratge de tràfic maliciós, el registre detallat de consultes i l'ús de llistes de regles (filtres) per decidir quines connexions s'accepten o es deneguen.

## 2. Arquitectura del Desplegament
El servei s'ha desplegat utilitzant **Docker Compose**, garantint un entorn aïllat i fàcilment replicable:

* **Imatge oficial:** dguard/adguardhome.
* **Ports exposats:**
    * **53 (TCP/UDP):** Servei DNS per a les consultes dels clients.
    * **3000 (TCP):** Panell web d'administració i configuració inicial.
* **Persistència:** S'han configurat volums per mapar les carpetes de dades i configuració, assegurant que les estadístiques i regles no es perdin en reiniciar el contenidor.

## 3. Procés Realitzat
1.  **Creació de l'entorn:** Preparació de l'estructura de carpetes i definició de l'arxiu docker-compose.yml.
2.  **Desplegament:** Execució del servei amb la comanda docker-compose up -d.
3.  **Verificació inicial:** Comprovació de l'estat del contenidor (docker ps) i lectura de logs per confirmar l'activació del servidor.
4.  **Configuració de xarxa:** Configuració de la interfície de Windows per utilitzar 127.0.0.1 com a DNS.

---

## 4. Evidències del Desplegament

### 4.1 Verificació de Logs i Contenidor
Es confirma que el contenidor s'ha creat correctament i que el servei web està disponible.
![Logs inicials de Docker](paso1_logs.png)

### 4.2 Assistent de Configuració Web
Procés inicial on es defineixen les interfícies d'escolta per al tràfic DNS i l'administració.
![Configuració inicial AdGuard](paso2_wizard.png)

### 4.3 Configuració DNS del Sistema
Evidència de la configuració manual de la pila TCP/IPv4 en el sistema host per redirigir el tràfic cap al tallafocs DNS.
![Configuració DNS Windows](paso3_dns_windows.png)

### 4.4 Dashboard i Estadístiques de Bloqueig
Demostració del funcionament real amb consultes processades i tràfic bloquejat automàticament per les llistes de regles.
![Dashboard Final AdGuard](paso4_dashboard.png)

---

## 5. Recursos utilitzats
* [Documentació oficial d'AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)
* [Docker Compose Docs](https://docs.docker.com/compose/)
* Imatge oficial de Docker Hub.
