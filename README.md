> [!NOTE]
> rien n'est fait ni testé, c'est un debut de travail!


# MidiPercussion
a way to make a midi controled percusion system with solenoids an servomotors


# Percussion Standard GM (Canal 10)

| Numéro MIDI | Instrument              | exemple pca output number |
|-------------|--------------------------|-------------------------|
| 35          | Acoustic Bass Drum       |:heavy_check_mark: 0 |
| 36          | Bass Drum 1              |:heavy_check_mark: 0 |
| 37          | Side Stick               | :heavy_check_mark: 1 |
| 38          | Acoustic Snare           | :heavy_check_mark: 2 |
| 39          | Hand Clap                | :heavy_check_mark: 3 |
| 40          | Electric Snare           | :heavy_check_mark: 2 |
| 41          | Low Floor Tom            | :heavy_check_mark: 3 |
| 42          | Closed Hi-Hat            | :heavy_check_mark: 4 |
| 43          | High Floor Tom           | :heavy_check_mark: 5 |
| 44          | Pedal Hi-Hat             | :heavy_check_mark: 6 |
| 45          | Low Tom                  | :heavy_check_mark: 3 |
| 46          | Open Hi-Hat              | :heavy_check_mark: 7 |
| 47          | Low-Mid Tom              | :heavy_check_mark: 8 |
| 48          | Hi-Mid Tom               | :heavy_check_mark: 9 |
| 49          | Crash Cymbal 1           | :heavy_check_mark: 10 |
| 50          | High Tom                 | :heavy_check_mark: 11 |
| 51          | Ride Cymbal 1            | :heavy_check_mark: 12 |
| 52          | Chinese Cymbal           | :heavy_check_mark: 11 |
| 53          | Ride Bell                | :heavy_check_mark: 12 |
| 54          | Tambourine               |:heavy_check_mark: 13 |
| 55          | Splash Cymbal            | :heavy_check_mark: 14 |
| 56          | Cowbell                  |:heavy_check_mark: 15 |
| 57          | Crash Cymbal 2           |:heavy_check_mark: 10 |
| 58          | Vibraslap                |:heavy_check_mark: 16 |
| 59          | Ride Cymbal 2            |:heavy_check_mark: 12 |
| 60          | Hi Bongo                 |
| 61          | Low Bongo                |
| 62          | Mute Hi Conga            |
| 63          | Open Hi Conga            |
| 64          | Low Conga                |
| 65          | High Timbale             |
| 66          | Low Timbale              |
| 67          | High Agogo               |
| 68          | Low Agogo                |
| 69          | Cabasa                   |
| 70          | Maracas                  |
| 71          | Short Whistle            |
| 72          | Long Whistle             |
| 73          | Short Guiro              |
| 74          | Long Guiro               |
| 75          | Claves                   |
| 76          | Hi Wood Block            |
| 77          | Low Wood Block           |
| 78          | Mute Cuica               |
| 79          | Open Cuica               |
| 80          | Mute Triangle            |
| 81          | Open Triangle            |

## Actionneurs 

On va utiliser des solenoides pour toutes actions simple qui n'ont pas besoin d'etre maintenue activé (pour eviter les surchauffes) 

Pour toute action qui necessite le maintient d'un changement d'etat, nous utiliserons des servomoteurs (position Hat? + sifflet + maracas ?) => pas aussi rapide que les solenoides et complexifie le code ....  <=== a voir !!

### Schemas branchement

Nous devrons etre capable de faire varier la puissance de frappe de chacune des percussions, il faut donc varier l'alimentation a l'aide de pca9685.
l'idée est de simplement d' atribuer une sortie pour une ou plusieurs note midi,les sorties 0 a 15 seront gerré par le pca1, les sorties 16 a 32 seront géré par le pca2 etc...
![Schema electrique](https://raw.githubusercontent.com/glloq/MidiPercussion/main/img/branchement%20pwm.png?raw=true)


### Choix mecanique 

#### Baguettes

il y a plusieurs facons de faire l'assemblage des baguettes mais il y a plusieurs contraintes a respecter :
- temps pour action => le temps/ deplacement necessaire pour actionner la note
- le temps entre 2 actions => temps minimum entre deux actions
- le bruit du solenoide => il faut utiliser un systeme pour amortir le retour de baguette
- il faut permettre une maintenance rapide => reglage de l'angle, remplacement de baguette etc

  
#### siffet 


## Partie code

Un solenoide sera controlé via le pca9685 pour moduler la puissance de frappe en fonction de la velocité de la note midi recue.
Chaque note midi jouable est declaré avec toutes les information necessaire (numeroMidi,numero pin sortie, temps actif, min PWM, etc...)
en fonction du montage mecanique et des solenoides, il faudra surement doubler certain solenoides afin d'ateindre un rythme elevé => a verifier !





  
