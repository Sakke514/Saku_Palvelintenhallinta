
**Tehtävä a)**
- Aluski asensin Caddyn ja se tapahtui komennoilla sudo apt update ja sudo apt install caddy (muuta ei tarvtia koska teen vain localhostina)
- sitten käytiin kattomassa että kaikki tarvittava localhost on caddyfilessä sudo nano /etc/caddy/Caddyfile ja laitettiin sinne <pre>localhost {
    root * /var/www/html
    file_server
} </pre>
 <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/caddy1.png" alt="Kuvankaappaus">
- Seuraavaksi muokkasin index.html tiedostoa että saan sinne omaa tekstiä. Menin hakemimistoon /var/www/html ja kirjotin index.html (sudo nano index.html) pienen tekstin
- aluksi minulla oli ongelma että caddy default page ei vaihtunut omaani mutta kokeilin incongnito tilassa eli ilman cachea ja sivusto tuli näyviin.
-  <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/caddy.png" alt="Kuvankaappaus">
**Tehtävä b)**
- tein playbookin caddyplay.yml mihin pistin seuraavat taskit
- <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/caddyplay.png" alt="Kuvankaappaus">
