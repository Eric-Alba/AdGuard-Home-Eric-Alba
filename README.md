# Pràctica 0378: Tallafocs - AdGuard Home
**Alumne:** Eric Alba (naipeer)
**Centre:** Institut El Calamot
**Curs:** 2025-2026

## 1. Introducció
Aquesta pràctica consisteix en el desplegament d'**AdGuard Home** mitjançant Docker[cite: 2, 59]. AdGuard Home actua com un servidor DNS amb filtratge a nivell de xarxa, permetent gestionar polítiques sobre les consultes DNS dels clients[cite: 8, 21].

Encara que no és un tallafoc clàssic, comparteix funcions clau com el filtratge de tràfic, el registre de consultes i l'ús de llistes de regles (ACCEPT/DROP)[cite: 9, 11, 18].

## 2. Arquitectura del Desplegament
El servei s'ha desplegat utilitzant **Docker Compose** amb la següent configuració[cite: 67]:

* **Imatge oficial:** `adguard/adguardhome`[cite: 44, 86].
* **Ports exposats:**
    * `53`: Servei DNS per a les consultes dels clients[cite: 45, 69].
    * `3000`: Panell web d'administració i estadístiques[cite: 52, 69].
* **Persistència:** S'han configurat volums per garantir que la configuració i les dades sobrevisquin als reinicis[cite: 54, 68].

## 3. Procés Realitzat
1. **Creació de l'entorn:** Preparació de la estructura de carpetes i l'arxiu `docker-compose.yml`[cite: 63, 74].
2. **Desplegament:** Execució del servei amb la comanda `docker-compose up -d`.
3. **Verificació inicial:** Comprovació de l'estat del contenidor i lectura de logs per confirmar que el servidor web està actiu a `http://localhost:3000`.

## 4. Evidències (Pendent de completar captures)
* [ ] **Dashboard:** Captura del panell principal amb estadístiques[cite: 14, 78].
* [ ] **Bloqueig:** Demostració d'un domini bloquejat al log de consultes[cite: 28, 71].
* [ ] **Configuració DNS:** Captura de la configuració de xarxa de l'equip apuntant a AdGuard[cite: 60, 72].

## 5. Recursos utilitzats
* Documentació oficial d'AdGuard Home[cite: 84, 89].
* Docker Compose Docs[cite: 90].
