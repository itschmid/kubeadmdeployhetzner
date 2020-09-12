## kubeadmdeployhetzner

Ansible-Playbook zum Einrichten eines Test&Spiel - Kubernetes-Cluster in der Hetzner-Cloud.
Die Orginalversion stammt von [erkules](https://github.com/erkules/). Dies ist eine angepasste Version, die komplett auf alle Terraform und Shellskripte verzichtet.


### Requirements

* python3.6
* ansible 2.9
* python-hcloud
* pipenv

### Konfiguration

Die Konfiguration erfolgt an zwei Stellen:
* .env - hier sollten die API-Keys und die Passwörter eingetragen werden.
* group_vars/all - hier können folgende Informationen eingetragen werden:
  * mit welchen Prefix die Hostnamen anfangen sollen
  * wieviele Nodes erstellt werden sollen
  * welcher Hetzner-Server-Type verwendet werden soll
  * in welcher Location die Server laufen soll
  * und welcher SSH-Key importiert werden soll
  * Username, mit dem auf dem Server gearbeitet werden soll (Passwort kommt in die .env)
   
### Quickstart

```bash
ansible-playbook -i inventory.d all.yml
```

Nach ein paar Minuten sollte die Maschine erstellt und konfiguriert sein. Die erste Maschine wird als Master konfiguriert.
Login auf die Server erfolgt mittels dem "e2m_user" und dem entsprechendem Passwort aus der .env.

### Destroy

Zerstört werden die Maschinen mit:

```bash
ansible-playbook -i inventory.d destroy.yml
```


CNI:

In  group_vars/all kann 
cni: calico
oder 
cni: weave 
gesetzt werden.
