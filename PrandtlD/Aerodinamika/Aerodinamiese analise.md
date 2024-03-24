
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

# Stabiliteitsanalise vir dempingskoeëffisiënte

Dit is belangrik om die volgende instellings te doen met 'n stabiliteitsanalise:
- Maak die digtheid sodat dit in SI eenhede is oftewel ongeveer $1kg/m^3$.  Maak ook die spoed by Vinf na die regte waarde.
- Stel die "Stability Type" as "Steady".
- Dit is dan ook baie belangrik om die hoofbalk van die vlerk weg te steek.  Die analise word dan geloop op Geometry set "Shown".  Anders val die analise om.
![[StabilityAnalysis.png]]
Die resultate is dan in die *.stab* lêer.
![[StabilityAnalysisResults.png]]
As 'n voorbeeld word $C_{Mq}$ uitgewys in die *.stab* lêer.

# Resultate van verskillende konfigurasies
## Sonder romp en vlieënier

Die effek van 'n romp word nie in ag geneem nie.  Dit beteken dat daar minder parasitiese sleurkrag sal wees en dat daar geen aerodinamiese moment gaan wees as gevolg van die romp nie.

### Parasiet sleurkrag $C_{D0}$

Die $C_{D0}$ waarde is as 0.01024 bereken met OpenVSP.
Resultate in [[ParasiteVlerkAlleen]].

![[ParasietSleurGeenRomp.png]]

### Vorteksroostermetode analise

'n Vorteksrooster analise in OpenVSP is gedoen om die dempingskoeëffisiënte te bereken:  [[PrandtlD_DegenGeomStab]].

### Paneelmetode analise

Gebruik OpenVSP vir analise.

Eienskappe is uit:  [[Prandtl D eienskappe]].

Die 2D XFOIL voorlopige analise is gebruik om die staak te voorspel.  Daar is nog 'n anomalie (sien rooi sirkel) wat verduidelik moet word met die XFOIL resultate maar gebruik CLmax as 1.2 soos uit die data.

![[PrandtlInboard_XFOIL_Prelim.png]]
Die CLMax is hier ingesit:
![[CLMax.png]]

Die resultate is in:  [[PrandtlD_VSPGeom.polar]]

Hier is die resultate van die $C_{M \alpha}$ in vergelyking met die Cessna 172 se kurwe.  Wag hierdie is dalk 'n fout.  Die positiewe kurwe is dalk uit 'n DATCOM analise.  Volg dit op en maak hierdie grafiek reg.  Die plat gedeelte op die rooi grafiek is 'n aanname.
![[CMalpha_OpenVSP_PrandtlvlerkAlleen.png]]
Hierdie is dalk nie heeltemal reg nie.  Dit moet nog daardie erg neus op verskynsel modelleer, wat in hierdie video genoem word:  https://www.youtube.com/watch?v=hzh9JC5QwOg by tyd 7:30.  Die paneelmetode kan dit nie modelleer nie.  Dalk was DATCOM die regte metode hiervoor.  Maak dalk 'n DATCOM model hiervoor.

Sleur is ook  heeltemal te veel.  Die paneelmetode oorskat dit.  Veral op hoër invalshoeke
Die beheereffektiwiteit van die beheervlakke moet bereken word.
Die gradient van die momentkurwe lyk te steil.


Die giermoment of $\beta$ defleksie resultate kan gevind word in:  [[PrandtlD_VSPGeomGier.polar]]
Hier is die positiewe sin van $\alpha$ en $\beta$ uit [[Verwysings]] 2.
![[StabilityWindAxes.png]]

A quick consideration of the signs convention will yield the stability criterion for $C_{n \beta}$ - which is the **yaw stiffness** - sometimes called the **weathercock derivative**:

- A positive sideslip means the velocity approaches the aircraft from the stbd side, meaning that a positive sideslip is achieved by an aircraft motion _nose port_.
- Hence this is achieved from a _negative_ perturbation in $\psi$.
- To return the aircraft back to equilibrium would require a positive moment to cause the aircraft to move nose starboard.
- Hence for stability, if $\beta$ increases, $N$ also needs to increase. Hence $C_{n \beta} > 0$ for stability.

$CN beta	0.001253912313393		Vir Cessna 172 is CN beta:		0.02106	Dus is die gier styfheid van die Prandtl vlerk baie laag, maar stabiel.
### Handberekening analise

Tans geen handberekeninge nie.