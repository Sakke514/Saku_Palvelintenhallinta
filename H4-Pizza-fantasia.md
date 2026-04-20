
**Tehtävä a)**
- Aluski asensin Caddyn ja se tapahtui komennoilla sudo apt update ja sudo apt install caddy (muuta ei tarvtia koska teen vain localhostina)
- sitten käytiin kattomassa että kaikki tarvittava localhost on caddyfilessä sudo nano /etc/caddy/Caddyfile ja laitettiin sinne <pre>localhost {
    root * /var/www/html
    file_server
} </pre>
- Seuraavaksi muokkasin index.html tiedostoa että saan sinne omaa tekstiä. Menin hakemimistoon /var/www/html ja kirjotin index.html (sudo nano index.html) pienen tekstin
- aluksi minulla oli ongelma että caddy default page ei vaihtunut omaani mutta kokeilin incongnito tilassa eli ilman cachea ja sivusto tuli näyviin.
