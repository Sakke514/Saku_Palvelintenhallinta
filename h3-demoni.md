**1. Karvinen 2026: Apache installed with Ansible - quick notes**
- Antaa esimerkin millaiselta skripti voisi näyttää että jokainen user pystyisi muokkaamaan niitä.
- Huomiona aina kun konfiguraatiota muokataan apache pitää käynnistää uudelleen.


**2. Ansible Community Documentation: Handlers: running operations on change**
- Handlerssit ovat taskeja, jotka suoritetaan aina vain, kun niistä ilmoitetaan
- Handlerssit voivat käyttää silmukoita ilmoittamiseen. Looppeja käytetään yhdistettynä muuttujiin useiden ilmoitusten laukaisimeksiki. Mikä tahansa silmukan muutos laukaiseen kaikki handlerssit
- Handlerssit käynnistetään siis silloin kuin tehdään muutoksia

  
**3.'ansible-doc service'**
- Service moduuli ohjaa palveluita ja osaa tunnistaa mitä järjestelmää palvelin käyttää esim **systemd**
- enabled kertoo käynnistyykö palvelu automaattisesti eli yes/no
- name = palvelun nimi
- State kertoo palvelun tilan
   - started, stopped, restarted
     
- **Esimerkkinä** <pre>" name: Apache on päällä ja käynnistyy bootissa
  ansible.builtin.service:
    name: httpd
    state: started
    enabled: yes "<pre>

**Tehtävä a) Apassi. Asenna Apache 2 käsin. Weppisivun tulee näkyä palvelimen etusivulla. Sivun tulee olla tavallisen          käyttäjän muokattavissa, ilman root- tai sudo-oikeuksia.**
- Ensimmäiseksi päivitetään ja asennettaan apache2
<pre>sudo apt update
sudo apt install apache</pre>
- sitten siirretään oikeudet rootilta käyttäjälle  komennolla <pre>sudo chown -R sakup:sakup /var/www/html<pre>

- Lopuksi luodaan uusi etusivu
    - aluksi poistetaan vakio index
      <pre> rm /var/www/html/index.html </pre>
    - Ja viimeiseksi luodaan oma sivu komennolla
 <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/Screenshot 2026-04-14 200743.png" alt="Kuvankaappaus">  
    - sitten vielä tarkistetaan selaimesta että toimi ja tadaa ja tästä opin myös että ääkkösiä ei kannata käyttää
 <img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/Screenshot 2026-04-14 200837.png" alt="Kuvankaappaus">


**Tehtävä b)**
- Ensimmäiseksi sammutetaan apache "sudo systemctl stop apche2 ja sitten vielä estetään että se ei käynnisty myöskään bootissa sudo systemctl disable apache2 ***(tämä tehdään siksi koska apache varaa portin 80 eikä nginx toimi jos apache on päällä)***
- sitten asennellaan taas eli <pre> sudo apt install nginx -y </pre>
- ja kuten apachessakin tehdään hakemistosta oma, että voidaan muokkailla ilman sudoa <pre> sudo chown -R sakup:sakup /var/www/html </pre>
- ja viimeiseksi luodaan sivu ilman sudoa ja testataan localhostissa, että homma pelittäää
<img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/Screenshot 2026-04-14 204446.png" alt="Kuvankaappaus">
<img src="https://raw.githubusercontent.com/Sakke514/Saku_Palvelintenhallinta/main/Screenshot 2026-04-14 204412.png" alt="Kuvankaappaus">  


**Tehtävä b)**
- Aluksi luodaan playbookki ja itse annoin sen nimeksi install_nginx.yml
- **Tässä kerron alla olevan playbookin erikohdat ja mitä tekevät**
- hosts: localhost kertoo että suoritetaan tällä koneella
- connection: local eli ansible ei avaa shh:ta vaan ajaa paikallisesti
- become yes kertoo että tehtävät pitää ajaa pääkäyttäjän oikeusilla eli vähän sama kui "sudo"
- state stopped varmitaa sen että apache ei ole päällä

