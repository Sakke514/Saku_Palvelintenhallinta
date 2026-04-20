
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
- eli tässä play bookissa hyvin minimalistiset taskit extrana olisi voinut vielä laittaa että sulkee ja disablee kurssilla aijjemmin käytetyty apache2 ja nginx, koska voisi tulla ongelmia koska käyttävät samaa porttia. Itse olen ne disablannut joten sitä ei tässä localhost versiossa tarvittu
- sen voisi tehdö esim
- <pre> ansiblr.bultin service:
  name: apache2(esim)
  state: stopped
  enabled: no
  ignore_errors: yes (tämä siksi jos apachea ei ole menee playbookissa eteenpäin eikä kaadu) </pre>
- sitten vielä ajoin komennolla <pre> ansible-playbook caddyplay.yml --ask-become-pass </pre>
- <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/ajettuc.png" alt="Kuvankaappaus">

**Tehtävä c)**
- Aluksi luodaan samaan kansioon missä playbook on tiedosto minkä loppu on .j2
- <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/j2.png" alt="Kuvankaappaus">
- sitten lisätään task playbookkiin joka kopioi tämän tiedoston /etc/caddy/Caddyfile -polkuun ja lataa asetukset uudelleen.
-  <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/uusiplay.png" alt="Kuvankaappaus">
- lopuksi vielä kun kaikki toimii ja muokattu playbook on ajettu katsotaan tuliko haluttu teksti
-  <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/sivutoimii.png" alt="Kuvankaappaus">
- <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/ajettu80.png" alt="Kuvankaappaus">

**tehtävä d)**
- aluski ajetaan komento sudo apt-get purge caddy -y eli se poistaa caddyn
- <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/poistetaan.png" alt="Kuvankaappaus">
- sitten ajoin uudelleen playbookin
- <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/ajopoisto.png" alt="Kuvankaappaus">
- elo kuten kuvasta näämme homma pelittää eli playbookki toimii vaikka caddyn poistaa, playbook korjaa tilanteen

**tehtävä e)**
- Voimme todentaa että tila on idempotentti ajamlla playbookin uudestaa ja jos aina tulee vain ok ja mikään ei muutu näin on
