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
<img width="1450" height="361" alt="Captura de pantalla 2026-05-08 154341" src="https://github.com/user-attachments/assets/cfc7c438-2f46-4b54-ad67-2e0d6f552fa7" />


### 4.2 Assistent de Configuració Web
Procés inicial on es defineixen les interfícies d'escolta per al tràfic DNS i l'administració.
<img width="1478" height="758" alt="Captura de pantalla 2026-05-08 154758" src="https://github.com/user-attachments/assets/222a9ee4-ffad-4c52-9510-6f4728eea6b4" />
<img width="1432" height="962" alt="Captura de pantalla 2026-05-08 154831" src="https://github.com/user-attachments/assets/7edb1119-f80a-46d2-8727-9b203e5a030f" />
<img width="416" height="677" alt="Captura de pantalla 2026-05-08 154946" src="https://github.com/user-attachments/assets/6c259085-b4e1-496f-bfe1-41c4cc9e2e8f" />


### 4.3 Configuració DNS del Sistema
Evidència de la configuració manual de la pila TCP/IPv4 en el sistema host per redirigir el tràfic cap al tallafocs DNS.
<img width="1266" height="780" alt="image" src="https://github.com/user-attachments/assets/2ebbf21e-d73d-4dad-8876-adb29115ccb4" />


### 4.4 Dashboard i Estadístiques de Bloqueig
Demostració del funcionament real amb consultes processades i tràfic bloquejat automàticament per les llistes de regles.
<img width="1917" height="967" alt="image" src="https://github.com/user-attachments/assets/d6c0f647-1b26-46f5-8f31-026e8da1ae75" />



---

## 5. Recursos utilitzats
* [Documentació oficial d'AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)
* [Docker Compose Docs](https://docs.docker.com/compose/)
* Imatge oficial de Docker Hub.
