# Massa en traagheid berekening

## Sonder romp en vlieënier

Die Prandtl vlerk lyk as volg.  Die massa verspreiding op die Prandtl vlerk word as 'n area gewig modelleer.

Maak die volgende aannames: 
- Die vlerk se dop word uit koolstofvesel met 'n digtheid van $1800 kg/m^3$ vervaardig.  Die hoofbalk word ook uit hierdie materiaal gemaak.
- Die dikte van die vlerk dop (skin) is 1.1mm.
- Die hoofbalk word deur 'n conformal komponent in OpenVSP modelleer.  Dit het 'n dikte van 3% van die koord.

Hierdie massa aannames word in OpenVSP ingesit en dan word die massa bereken.

![[1_PrandtlVlerk.png]]

OpenVSP aannames:

![[GeenVlieenierHoofbalkMassa.png]]
![[GeenVlieenierVlerkMassa.png]]
Die massa eienskappe soos berekening is gedokumenteer in [[PrandtlD_MassProps_20240323]].

Die assestelsel word vertoon in die prent hierbo.  Die oorsprong van die assestelsel is op die voorpunt van die vlerk.

Die massa is $85.9kg$.

Die swaartepunt is as volg.  Neem die y swaartepunt as nul, want die integrasie in OpenVSP maak 'n fout want die snitte is te grof.
$$ CG = \begin{bmatrix}  
x & y & z
\end{bmatrix} = 
\begin{bmatrix}  
1.297 & 0 & 0.099
\end{bmatrix} m  $$

Die traagheidstensor:
$$ I = 
\begin{bmatrix}  
I_{xx} & I_{xy} & I_{xz}\\  
I_{yx} & I_{yy} & I_{yz} \\
I_{zx} & I_{zy} & I_{zz}
\end{bmatrix} = 
\begin{bmatrix}  
599.435 & \cdot & \cdot\\  
\cdot &  38.498 & \cdot \\
\cdot & \cdot &  636.889
\end{bmatrix} kg.m^2
$$
kan uit die bostaande lêer verkry word.  Die kruisprodukte word geneem as nul want ons neem aan die vliegtuig is goed gebalanseer.