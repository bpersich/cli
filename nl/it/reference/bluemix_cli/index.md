---



copyright:

  years: 2015, 2017
lastupdated: "2017-07-12"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Introduzione alla CLI {{site.data.keyword.Bluemix_notm}}
{: #getting-started}

La CLI {{site.data.keyword.Bluemix_notm}} ti offre una modalità unificata per interagire con le tue applicazioni, contenitori, infrastrutture e altri servizi utilizzando un'interfaccia riga di comando. 

**Restrizione**: la CLI {{site.data.keyword.Bluemix_notm}} non è supportata da Cygwin, per cui non utilizzare la CLI {{site.data.keyword.Bluemix_notm}} nella finestra della riga di comando di Cygwin.

**Nota**: se la tua rete contiene un server proxy HTTP tra l'host che esegue la CLI e {{site.data.keyword.Bluemix_notm}}, devi specificare il nome host o l'indirizzo IP del server proxy nella variabile di ambiente HTTP_PROXY.

**Nota:** lo strumento CLI {{site.data.keyword.Bluemix_notm}} include un'interfaccia riga di comando Cloud Foundry nella sua installazione. Tuttavia, non è consentito utilizzare in combinazione i comandi della CLI {{site.data.keyword.Bluemix_notm}} `bx xxx` e quelli della CLI Cloud Foundry `cf xxx` se disponi della tua propria installazione della cli cf. Usa invece `bluemix cf` se intendi utilizzare la cli cf per gestire le risorse Cloud Foundry. Nel backend, questo esegue i comandi della CLI Cloud Foundry integrata in un contesto condiviso con la CLI {{site.data.keyword.Bluemix_notm}}.  Inoltre,  `bluemix cf api/login/logout/target` non è consentito e devi utilizzare invece `bluemix api/login/logout/target`.

## Installazione della CLI {{site.data.keyword.Bluemix_notm}}
{: #install_bluemix_cli}

<!-- Online installation Currently Production Only! Please don't forget to replace the domain name-->

### Installazione online

Con l'accesso a una connessione Internet, copia e incolla il seguente comando in una console del terminale ed eseguilo.

**macOS**
```
sh <(curl -fsSL https://clis.ng.bluemix.net/install/osx)
```

**Linux**
```
sh <(curl -fsSL https://clis.ng.bluemix.net/install/linux)
```

**Windows PowerShell**

Copia e incolla il seguente comando in una console del terminale [Windows PowerShell](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/getting-started-with-windows-powershell) ed eseguilo.
```
iex(New-Object Net.WebClient).DownloadString('https://clis.ng.bluemix.net/install/powershell')
```

### Installazione offline

<!-- End of online installation -->

Per Mac OS e Windows, scarica il [pacchetto CLI {{site.data.keyword.Bluemix_notm}}](/docs/cli/index.html#downloads) ed esegui il programma di installazione.

Per Linux, segui la seguente procedura:

  1. Scarica il pacchetto ed estrailo. Ad
esempio:

  ```
  ~$ tar -xvf Bluemix_CLI.tar.gz
  Bluemix_CLI/
  Bluemix_CLI/update_global_config
  Bluemix_CLI/install_bluemix_cli
  Bluemix_CLI/bx/
  Bluemix_CLI/bx/bash_autocomplete
  Bluemix_CLI/bx/zsh_autocomplete
  Bluemix_CLI/bin/
  Bluemix_CLI/bin/bluemix
  ~$
  ```

  2. Passa alla directory `Bluemix_CLI` ed esegui il comando `./install_bluemix_cli` con l'autorizzazione root. Puoi eseguire il comando come utente root o utilizzare il comando `sudo` per ottenere l'autorizzazione root. Ad
esempio:

  ```
  ~# cd Bluemix_CLI
  ~/Bluemix_CLI# sudo ./install_bluemix_cli
  Superuser privileges are required to run this script.
  The Cloud Foundry CLI version 6.15 is already installed.
  Copying files...
  The Bluemix CLI installed successfully. To get started, open a new Linux terminal and enter "bluemix help", or enter "bx help" as short name.
  ~/Bluemix_CLI#
  ```

Puoi ora iniziare a utilizzare la CLI {{site.data.keyword.Bluemix_notm}} o installare ulteriori plug-in.

## Primi passi con la CLI {{site.data.keyword.Bluemix_notm}}

Per configurare lo strumento della CLI {{site.data.keyword.Bluemix_notm}}, dovrai specificare l'API da utilizzare.  Questa dipende dalla regione con cui lavorerai; per ottenere un elenco, utilizza:

```
 ~ $ bluemix regions
Listing Bluemix regions...

Name       Geolocation      Customer   Deployment   Domain               CF API Endpoint                  Type
eu-de      Germany          IBM        Production   eu-de.bluemix.net    https://api.eu-de.bluemix.net    public
au-syd     Sydney           IBM        Production   au-syd.bluemix.net   https://api.au-syd.bluemix.net   public
us-south   US South         IBM        Production   ng.bluemix.net       https://api.ng.bluemix.net       public
eu-gb      United Kingdom   IBM        Production   eu-gb.bluemix.net    https://api.eu-gb.bluemix.net    public
```

Per la regione a cui vuoi accedere, prendi `CF API Endpoint` e utilizzalo per specificare l'endpoint API come nel seguente esempio:

```
~ $ bluemix api https://api.eu-gb.bluemix.net
Setting api endpoint to https://api.eu-gb.bluemix.net...
OK

API endpoint: https://api.eu-gb.bluemix.net (CF API version: 2.75.0)
Not logged in. Use 'bx login' to log in.
```

Segui quindi il prompt per accedere:

```
 ~ $ bluemix login
API endpoint: https://api.eu-gb.bluemix.net

Email> user@example.com

Password>
Authenticating...
OK

```

È possibile specificare l'organizzazione e lo spazio da utilizzare con gli switch `-o` e `-s`, altrimenti il comando di accesso ti chiederà di scegliere se ne hai più di uno.

La CLI {{site.data.keyword.Bluemix_notm}} è ora configurata e pronta per l'uso.

## Installazione di un plugin
{: #install_plug-in}

La CLI {{site.data.keyword.Bluemix_notm}} supporta un framework di estensione plug-in per integrare altri comandi oltre a quelli già integrati.


Puoi installare un plug-in dal repository, in locale o da un server remoto. {{site.data.keyword.Bluemix_notm}} dispone di repository che ospitano i plugin della CLI {{site.data.keyword.Bluemix_notm}} e plugin della CLI Cloud Foundry:

   * [Repository di plug-in CLI {{site.data.keyword.Bluemix_notm}} ](http://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins){: new_window} ![Icona link esterno](../../../icons/launch-glyph.svg), che contiene i plug-in per la CLI {{site.data.keyword.Bluemix_notm}}.

Per l'installazione da un repository, attieniti alla seguente procedura:

  1. Trova il plug-in nel repository. Dopo aver installato la CLI {{site.data.keyword.Bluemix_notm}}, il repository ufficiale `Bluemix` viene aggiunto per impostazione predefinita. Puoi elencare i plugin nel repository `Bluemix` utilizzando il comando `bluemix plugin repo-plugins`. Ad
esempio:

  ```
  ~$ bluemix plugin repo-plugins -r Bluemix
  Getting plug-ins from repository 'Bluemix'...

  Repository: Bluemix
  Name           Description                                    Versions
  auto-scaling   Bluemix CLI plugin for Auto-Scaling service    0.2.1, 0.2.2
  nsg            Bluemix Network Security Group plugin          0.1.1

  ~$
  ```

  2. Installa il plug-in dal repository `Bluemix` utilizzando il comando `bluemix plugin install`. Ad
esempio:

  ```
  ~$ bluemix plugin install auto-scaling -r Bluemix
  Looking up 'auto-scaling' from repository 'Bluemix'...
  9857792 bytes downloaded
  Installing plugin '/var/folder/v7/l3hnkz0x0b9b5mf1fyxh7yw00000gn/T/BluemixFileDownload062468676/auto-scaling-darwin-adm64-0.2.2'...
  OK
  Plugin 'auto-scaling 0.2.2' was successfully installed.
  ~$
  ```


Per installare un plugin dal tuo ambiente locale, completa la seguente procedura:

  1. Scarica il plug-in. Ad
esempio:

  ```
  ~$ wget http://public.dhe.ibm.com/cloud/bluemix/cli/bluemix-plugins/auto-scaling-darwin-amd64.0.2.2--2016-02-18 14:02:12-- http://public.dhe.ibm.com/cloud/bluemix/cli/bluemix-plugins/auto-scaling-darwin-amd64.0.2.2
  Resolving public.dhe.ibm.com... 9.17.248.112
  Connection to public.dhe.ibm.com|9.17.248.112|:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 9857792 (9.4M) [text/plain]
  Saving to: 'auto-scaling-darwin-amd64-0.2.2'

  auto-scaling-darwin-0.2.2 100%[===================>] 9.40M 518KB/s in 22s

  2016-02-18 14:02:34 (443 KB/s) - `auto-scaling-darwin-amd64-0.2.2' saved [9857792/9857792]
  ```

  2. Per un sistema simile a Unix, devi rendere eseguibile il file scaricato utilizzando il comando `chmod`. Ad
esempio:

  ```
  ~$ sudo chmod 755 auto-scaling-darwin-amd64-0.2.2
  Password:
  ~$
  ```

  3. Installa il plug-in utilizzando il comando `bluemix plugin install`. Ad
esempio:

  ```
  ~$ bluemix plugin install ./auto-scaling-darwin-amd64-0.2.2
  Installing pluign './auto-scaling-darwin-amd64-0.2.2'...
  OK
  Plugin 'auto-scaling 0.2.2' was successfully installed.
  ~$
  ```

Per l'installazione da un server remoto, attieniti alla seguente procedura:

  1. Installa il plug-in da un URL remoto direttamente utilizzando il comando `bluemix plugin install`. Ad
esempio:

  ```
  ~$ bluemix plugin install http://public.dhe.ibm.com/cloud/bluemix/cli/bluemix-plugins/auto-scaling-darwin-amd64-0.2.2
  Attempting to download the binary file...
  9857792 bytes downloaded
  Installing plugin '/var/folder/v7/l3hnkz0x0b9b5mf1fyxh7yw00000gn/T/BluemixFileDownload274645142/auto-scaling-darwin-adm64-0.2.2'...
  OK
  Plugin 'auto-scaling 0.2.2' was successfully installed.
  ~$
  ```


Sei ora pronto a utilizzare le righe di comando {{site.data.keyword.Bluemix_notm}}. Esegui `bluemix help` per visualizzare l'elenco dei comandi e le descrizioni. 

## Contattaci

Utilizza le seguenti opzioni per trovare informazioni sulle release, fornire un feedback e fare delle domande:
 * Per i dettagli sulle ultime release e per segnalare problemi: [SDK CLI {{site.data.keyword.Bluemix_notm}} ](https://github.com/IBM-Bluemix/bluemix-cli-sdk){: new_window} ![Icona link esterno](../../../icons/launch-glyph.svg)
 * Per fare domande e condividere informazioni con la community: [Canale Slack bluemix-cli](https://dwopen.slack.com/messages/bluemix-cli/){: new_window} ![Icona link esterno](../../../icons/launch-glyph.svg)
