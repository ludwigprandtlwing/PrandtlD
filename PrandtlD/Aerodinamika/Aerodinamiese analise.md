
# Verwysingspunt

Die aerodinamiese verwysingspunt word gekies as die swaartepunt van die vliegtuig en word in AERORP (aero reference point) gedefinieer.  Dit is as volg vir die vliegtuig en kom uit [[Massa en traagheid]].

```xml
    <location name="AERORP" unit="M">
        <x>1.297</x>
        <y>0.0</y>
        <z>0.099</z>
    </location>
```

Die swaartepunt word in die volgende plek in die JSBsim XML definisielêer vasgelê:

```xml
  <location name="CG" unit="M">
    <x>1.297</x>
    <y>0.0</y>
    <z>0.099</z>
  </location>
```


Die vehicle reference point of VRP word geneem as die oorsprong van die 3D model, wat 0,0,0 is.  Dit behoort die model reg te vertoon.

# Resultate van verskillende konfigurasies
## Sonder romp en vlieënier

Die effek van 'n romp word nie in ag geneem nie.  Dit beteken dat daar minder parasitiese sleurkrag sal wees en dat daar geen aerodinamiese moment gaan wees as gevolg van die romp nie.

### Parasiet sleurkrag $C_{D0}$

Die $C_{D0}$ waarde is as 0.01024 bereken met OpenVSP.
Resultate in [[ParasiteVlerkAlleen]].

![[ParasietSleurGeenRomp.png]]


### Paneelmetode analise

Gebruik OpenVSP vir analise.

Eienskappe is uit:  [[Prandtl D eienskappe]].


### Handberekening analise

