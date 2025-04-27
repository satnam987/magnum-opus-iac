# Installatie Handleiding Uptime Kuma

## Belangrijke Voorbereiding

Voordat je begint met de installatie, moet je eerst het IP-adres aanpassen in het bestand `inventory/hosts.yml`:

```yaml
# In inventory/hosts.yml
ansible_host: 172.16.184.190 # Vervang dit met jouw VM IP-adres
```

## Snelle Installatie (2 stappen)

### Stap 1: Bestanden Kopiëren

```bash
# Kopieer alle benodigde bestanden naar de VM (vervang IP_ADRES met jouw VM IP)
scp -r roles inventory site.yml ansible.cfg s149226@IP_ADRES:~/magnum/
```

### Stap 2: Playbook Uitvoeren

```bash
# Log in op de VM
ssh s149226@IP_ADRES

# Ga naar de magnum directory en voer de playbook uit
cd ~/magnum
ansible-playbook -i inventory/hosts.yml site.yml
```

Na deze stappen is Uptime Kuma beschikbaar op: `http://IP_ADRES:3001`

## Voorbeeld

Voor een VM met IP-adres 172.16.184.190:

```bash
# Bestanden kopiëren
scp -r roles inventory site.yml ansible.cfg s149226@172.16.184.190:~/magnum/

# Inloggen en playbook uitvoeren
ssh s149226@172.16.184.190
cd ~/magnum && ansible-playbook -i inventory/hosts.yml site.yml
```

Uptime Kuma zal dan beschikbaar zijn op: `http://172.16.184.190:3001`
