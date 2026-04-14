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
- State kertoo palvelun tilan
   - started, stopped, restarted
- **Esimerkkinä** <pre>" name: Apache on päällä ja käynnistyy bootissa
  ansible.builtin.service:
    name: httpd
    state: started
    enabled: yes "<pre>
