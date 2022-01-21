---
title: "Migracio Keepass Bitwarden"
date: 2022-01-20T20:30:15+01:00
draft: true
---

# Migrant de keepass a bitwarden

Fa un temps que me duia "rondant" el cap fer un canvi al meu sistema de contrasenyes, amb el qual he estat "fidel" a keepass des de fa més de 15 anys, les primers entrades que he trobat al meu fitxer keepass són del 26/06/2006.

El decidirme a fer la migració ha vengut un poc provocat perquè he llegit una entrada del blog d'aquest tipo ( https://trycatch.dev/blog/switching-from-keepass-to-bitwarden-after-14-years/ ), que vaig trobar a través del canal de telegram de ugeek, on explica la seva transició a bitwarden després de 14 anys.

Resulta curiós que jo ja feia uns dies (setmanes pot-ser) que ja estava provant tímidament (amb poques entrades) el servei en el cloud de bitwarden (https://www.bitwarden.com) i la veritat és que m'estava agradant molt, ja que té varies "cosetes" que trobo a faltar al keepass: 

1. És un gestor centralitzat a un servidor, cosa que té els seus avantatges i inconvenients com tots els serveis centralitzats. 
2. Té client oficial per linux, windows, android, ios... multiplataforma !!
3. Pots instal·lar-te una instància en local perquè és opensource que funciona amb el mateix client oficial.

El plantejament de keepass és molt bó perquè tens el fitxer en local i no està a cap servei cloud, però realment si necessites dur els passwords al mòbil es necessari tenir aquest fitxer sincronitzat, i al final acabes emprant dropbox, owncloud, etc ... per a tenir-lo sincronitzat. Al llarg dels anys he anat sincronitzant-lo a varis serveis i últimament estava emprant el nigul de la feina (un owncloud) però així i tot no el tenia "a casa meva".

## Vaultwarden al rescat

Després de llegir l'entrada del blog de *trycatch*  i veient lo bé que van que els altres serveis que tenc allotjats al meu docker (freshrss, shaarli, joplin) m'he decidit a provar amb bitwarden. A més, he trobat una configuració de contenidor molt més lleuger que el oficial ja que aquest necessita dos contenidors, app i db amb portgres, que a més són molt pesats). Aquest contenidor lleuger és una implementació de la API de bitwarden fet amb RUST, a més d'un fork de la interfície web. També és molt més lleuger que el projecte oficial entre d'altres coses perquè empra _sqlite_ de base de dades. 

El projecte que he emprat per fer el meu contenidor privat es diu "vaultwarden", i està disponible a https://github.com/dani-garcia/vaultwarden/wiki 

Notes del seu creador:

> Vaultwarden is an unofficial Bitwarden server implementation written in Rust. It is compatible with the official Bitwarden clients, and is ideal for self-hosted deployments where running the official resource-heavy service is undesirable.
> Vaultwarden is targeted towards individuals, families, and smaller organizations. Development of features that are mainly useful to larger organizations (e.g., single sign-on, directory syncing, etc.) is not a priority, though high-quality PRs that implement such features would be welcome.

Per a desplegar-ho al meu docker he fet això:

Crear un directori on s'allotjarà la base de dades del sistema: 
`mkdir /opt/docker/vaultwarden/data`

Descarregar la darrera versió:
`docker pull vaultwarden/server:latest`

Executar el contenidor: 
`docker run -d --name vaultwarden -v /opt/docker/vaultwarden/data/:/data/ -p 8086:80 vaultwarden/server:latest`

Amb això tendrem la interfície web de *bitwarden* al port 8086 (aquesta és la meva configuració, però es pot emprar qualsevol altre port)
