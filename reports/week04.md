Pingaa palvelimia ja käyttäjiä
Joihinkin saadaan yhteys ja toisiin ei.

Mooduuleja on install-snmp.yml tiedostossa apt, copy, service, shell ja debug
install-node-exporter.yml taas sisältää apt, file, get_url, unarchive, copy, shell, url ja debug

Muuttujat ovat paikallaan, jotta niitä voi käyttää uudelleen helpommin useassa kohtaa koodia. Ne ovat myös helppo vaihtaa tarvittaessa vars kohdassa.

Handlers kohdan komennot suoritetaan vasta kaikkien taskien jälkeen, ellei toisin ole käsketty.

Node Exporter ei koske järjestelmäpalveluita tai lue erillistä asennustiedostoa.

root@ansible:/ansible/playbooks# ansible-playbook -i ../inventory.ini apache.yml

PLAY [Install and configure Nginx web server on web1] **********************************************************************************

TASK [Update apt package cache] ********************************************************************************************************

ok: [web1]

TASK [Install Nginx web server] ********************************************************************************************************
ok: [web1]

TASK [Ensure web root directory exists] ************************************************************************************************
ok: [web1]

TASK [Create index.html displaying the server hostname] ********************************************************************************
ok: [web1]

TASK [Ensure Nginx service is started and enabled at boot] *****************************************************************************
changed: [web1]

TASK [Verify web server responds with HTTP 200 and expected hostname] ******************************************************************
ok: [web1]

PLAY RECAP *****************************************************************************************************************************
web1                       : ok=6    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

Ubuntu 24.04.4 LTS
10.10.20.101
16 prosessorin ydintä
15 705 MB muistia

Käyttäjälle paljon helpompi, että koko paketti on valmiiksi suunniteltu.
