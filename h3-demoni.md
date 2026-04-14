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
