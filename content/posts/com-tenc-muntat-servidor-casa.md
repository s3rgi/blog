---
title: Com tenc muntat el servidor de casa
date: 2023-01-02T19:22:28+01:00
latitude: 39.49488515
longitude: 2.88753239
altitude: 205.2936
---

Una de les coses a les que més temps lliure he dedicat aquesta darrers mesos, apart de la domòtica, es a muntar serveis amb docker al petit servidor que tenc a casa, un SOC d'aquests xinesos comprat a Amazon (https://www.amazon.es/dp/B08HLPX1Q2?ref=ppx_pop_mob_ap_share) però que està resultant una bona maquineta, és molt potent i quasi no consumeix, genial!

A aquest servidor hi ha instalada una distribució debian sense cap entorn gràfic, i a sobre això corren els diferents serveis.

## HomeAssistant 
HomeAssistant el tenc sobre una màquina virtual qemu, ja que la versió de HA que més m'agrada és la HASSOS( https://www.home-assistant.io/installation/generic-x86-64 ), perquè és un sistema operatiu complet que s'actualitza molt fàcilment. HASSOS a la vegada corre docker dins ell, així que perfecte !

## Serveis amb docker
Aquest tema és amb el que m'entretenc més, ja que cada poc temps trobo un nou servei que provar o posar en producció. 

Ara mateix tenc tots aquests serveis muntats, funcionant i els empro cada dia:

1. Servei de contrasenyes centralitzat, amb vaultwarden
2. Servidor de notes, amb trilium
3. Un servei per guardar articles i llegir-los després, amb wallabag
4. Un gestor de links, amb shaarli
5. Lector i gestor de rss, amb freshrss
6. Gestor de dns intern amb bloquejador de publicitat, amb pi-hole
7. Gestor proxy pels serveis, amb nginxmanager
8. Gestor VPN Wireguard, amb wg-easy
9. Un servidor WebDAV, amb sftpgo
10. Portainer, per gestionar els dockers amb una interficie web.
11. Monitorització dels serveis (els meus i els de la feina) amb UptimeKum al
12. Homer, un docker que fa el servei de "Home Page" per tenir un lloc on estan tots els enllaços als meus serveis.

Aniré fent articles de cada un dels serveis, com els he muntat i com els tenc configurats, aquesta entrada es solament per llistar-los.

Una de les fonts "d'inspiració" de tot això (serveis dockers i aquest nou blog) és el lloc web d'en ugeek (https://ugeek.github.io), m'encanta com té les coses muntades i lo bé que ho explica. Des d'aquí, felicitats per la teva feina, ets un crack!

Salut a tots !
