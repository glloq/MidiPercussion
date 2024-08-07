# MidiPercussion
a way to make a midi controled percusion system with solenoids an servomotors


# Percussion Standard GM (Canal 10)

| Numéro MIDI | Instrument              |
|-------------|--------------------------|
| 35          | Acoustic Bass Drum       |
| 36          | Bass Drum 1              |
| 37          | Side Stick               |
| 38          | Acoustic Snare           |
| 39          | Hand Clap                |
| 40          | Electric Snare           |
| 41          | Low Floor Tom            |
| 42          | Closed Hi-Hat            |
| 43          | High Floor Tom           |
| 44          | Pedal Hi-Hat             |
| 45          | Low Tom                  |
| 46          | Open Hi-Hat              |
| 47          | Low-Mid Tom              |
| 48          | Hi-Mid Tom               |
| 49          | Crash Cymbal 1           |
| 50          | High Tom                 |
| 51          | Ride Cymbal 1            |
| 52          | Chinese Cymbal           |
| 53          | Ride Bell                |
| 54          | Tambourine               |
| 55          | Splash Cymbal            |
| 56          | Cowbell                  |
| 57          | Crash Cymbal 2           |
| 58          | Vibraslap                |
| 59          | Ride Cymbal 2            |
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
nous utiliserons des PCA9685 pour moduler la puissance de frappe des solenoides.

Pour toute action qui necessite le maintient d'un changement d'etat, nous utiliserons des servomoteurs (position Hat? + sifflet + maracas ?) => pas aussi rapide que les solenoides et complexifie le code .... 

### Choix mecanique 

#### Baguettes

il y a plusieurs facons de faire l'assemblage des baguettes mais il y a plusieurs contraintes a respecter :
- temps pour action => le temps/ deplacement necessaire pour actionner la note
- le temps entre 2 actions => temps minimum entre deux actions
- le bruit du solenoide => il faut utiliser un systeme pour amortir le retour de baguette
- il faut permettre une maintenance rapide => reglage de l'angle, remplacement de baguette etc

  
#### siffet 



  
