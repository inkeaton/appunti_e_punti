Guida per l'installazione e la configurazione di Arch, usando archinstall e Awesome WM

## 1. Installazione

### 1.1 Arch
Avviata L'ISO, aggiorniamo le repository (nella tastiera americana, "-" si scrive con " ' ")
~~~
pacman -Syy
~~~
Installiamo archinstall
~~~
pacman -S archinstall
~~~
Avviamo archinstall
~~~
archinstall
~~~

### 1.2 Archinstall
Impostazioni importanti sono:
* Formato dei dischi: __ext4__
* Bootloader: __grub__
* Account Utente: __Aggiungere__ un utente, ed impostarlo come __superutente__
* Profilo: in questa guida, usiamo il profilo __xorg__. Si può anche scegliere __minimal__, ed installare xorg ed i driver separatamente
* Audio: __pipewire__
* Kernel: nel caso di un portatile, usiamo __linux__, per un desktop impostato per il gaming, __linux-zen__
* Pacchetti Aggiuntivi: installiamo, dato che ci serviranno in seguito:
	* __awesome__
	* __rofi__
	* __polybar__
	* __alacritty__
	* __feh__
	* __nano__
	* __git__
* Repository Opzionali: abilitare __multilib__ nel caso si usino programmi come steam o wine
Procedere poi con l'installazione, ed una volta terminata, riavviare.

#### 1.2.1 Xorg 
Entriamo e facciamo l'accesso. Nel caso avessimo scelto il profilo __minimal__, possiamo installare xorg con:
~~~
sudo pacman -S xorg xorg-xinit
~~~
Bisogna anche installare i __driver__ adatti alla propria scheda grafica.

### 1.3 AUR
Installiamo ed abilitiamo l'AUR, così da poter usare __yay__.
Prima cloniamo la repository con __git__
~~~
git clone https://aur.archlinux.org/yay-git.git
~~~
Dopo di che entriamo nella nuova cartella e creiamo ed installiamo il pacchetto con __makepkg__
~~~
cd yay-git
makepkg -si
~~~

### 1.4 Startx & xinitrc
Nel caso non sia già presente, copiamo `xinitrc` in `home`
~~~
cp etc/X11/xinit/xinirc ~/.xinitrc
~~~
Apriamo `.xinitrc` e rimuoviamo le ultime __5__ righe.
In questa sezione possiamo aggiungere tutti i comandi che vogliamo eseguire a startup. In questo caso, aggiungiamo solo il seguente:
~~~
exec awesome
~~~
Per aggiungere più comandi, possiamo collegarli usando __&__

Ora, per eseguire il WM possiamo semplicemente usare `startx`. Per eseguirlo in automatico all'avvio, possiamo modificare nel seguente modo il nostro `.bash_profile`, aggiungendo le seguenti linee:
~~~
[[ $(fgconsole 2>/dev/null) == 1 ]] && exec startx --vt
~~~

#### 1.4.1 Risoluzione
Nel caso fossimo in una macchina virtuale, possiamo impostare una risoluzione tramite il comando `xrandr`
Eseguendolo, avremo una lista delle risoluzioni disponibili
Per settarne una:
~~~
xrandr -s "length"x"height"
~~~

## 2. Configurazione

### 2.1 Github
Il pacchetto necessario è il seguente:
~~~
sudo pacman -S github-cli
~~~
Per accedere, è necessario usare il comando
~~~
gh auth login 
~~~

### 2.2 Polybar
launch.sh deve essere eseguibile

I file .desktop, le applicazioni, si trovano in `/usr/share/applications` (quelli per tutti gli utenti)

i font sono in `/usr/local/share/fonts` 

### 2.3 SDDM
Per instllare questo Display Manager usiamo:
~~~
sudo pacman -S sddm
~~~
E lo abilitiamo con:
~~~
sudo systemctl enable sddm -f
~~~

Installeremo poi il tema [Sugar Candy for SDDM](https://www.gnome-look.org/p/1312658) Per farlo, possiamo seguire la guida presente sulla pagina.

Estraiamo il tar.gz nella cartella giusta
~~~
sudo tar ‑xf sugar‑candy.tar.gz ‑C /usr/share/sddm/themes
~~~

Aggiungiamo al nostro `etc/sddm.conf` la linea seguente
~~~
[Theme]
Current=sugar-candy
~~~

Per la personalizzazione del tema, bisogna modificare il suo `theme.conf`

### 2.4 Ranger

