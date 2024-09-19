
> [!NOTE]
> rien n'est fait ni testé, c'est un debut de travail!

# MidiPercussion
l'objectif est de permettre de jouer de la batteries et autre percussion en utilisant [la norme General Midi Drum](https://en.wikipedia.org/wiki/General_MIDI#Percussion)
nous aurons donc besoin d'actionner differentes percussions

## Actionneurs 

On va utiliser des solenoides pour toutes actions simple qui n'ont pas besoin d'etre maintenue activé (pour eviter les surchauffes) 

Pour toute action qui necessite le maintient d'un changement d'etat, nous utiliserons des servomoteurs (position Hat? + sifflet + maracas ?) => pas aussi rapide que les solenoides et complexifie le code ....  <=== a voir !!

### Schemas branchement

Nous devrons etre capable de faire varier la puissance de frappe de chacune des percussions, il faut donc varier l'alimentation a l'aide de pca9685.
l'idée est de simplement d' atribuer une sortie pour une ou plusieurs note midi,les sorties 0 a 15 seront gerré par le pca1, les sorties 16 a 32 seront géré par le pca2 etc...
<img src="https://raw.githubusercontent.com/glloq/MidiPercussion/main/img/branchement%20pwm.png" alt="Your image title" width=80% height=80%/>


### Choix mecanique 

#### Baguettes

il y a plusieurs facons de faire l'assemblage des baguettes mais il y a plusieurs contraintes a respecter :
- temps pour action => le temps/ deplacement necessaire pour actionner la note
- le temps entre 2 actions => temps minimum entre deux actions
- le bruit du solenoide => il faut utiliser un systeme pour amortir le retour de baguette
- il faut permettre une maintenance rapide => reglage de l'angle d'attaque, remplacement pieces ou de baguette, etc...

<img src="https://raw.githubusercontent.com/glloq/MidiPercussion/main/img/baguette.png" alt="Your image title" width=30% height=30%/>


## Partie code

Un solenoide sera controlé via le pca9685 pour moduler la puissance de frappe en fonction de la velocité de la note midi recue.
  
Pour permettre une adaptation simple, nous utiliserons une structure pour regroupper toutes les information pour chacune des sorties/note midi.
```
struc midiNote{
  byte midiNumber;      // Numéro de note MIDI (0 à 127 pour les percussions)
  byte outputPin;       // Numéro de pin du PCA9685 pour la sortie
  byte pcaAddress;      // Adresse I2C du PCA9685 (0x40 par défaut, mais peut changer)
  int pwmMin;           // Valeur minimale du signal PWM (par exemple, 1000)
  unsigned long activeTime; // Temps actif max (en millisecondes) de la sortie lorsqu'elle est activée
}

```

avec cette organisation nous pouvons simplement declarer les differentes notes percussion et leurs parametres.  
On pourra associer plusieurs numero midi avec une seule sortie/numero outputPin.





  
