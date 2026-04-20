
**Tehtävä a)**
- Aluski asensin Caddyn ja se tapahtui komennoilla sudo apt update ja sudo apt install caddy (muuta ei tarvtia koska teen vain localhostina)
- sitten käytiin kattomassa että kaikki tarvittava localhost on caddyfilessä sudo nano /etc/caddy/Caddyfile ja laitettiin sinne <pre>localhost {
    root * /var/www/html
    file_server
} </pre>
