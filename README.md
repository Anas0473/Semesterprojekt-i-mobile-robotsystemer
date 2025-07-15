# Semesterprojekt i mobile robotsystemer

Mobil robot bygget på TurtleBot Burger-platformen, der sporer en persons hånd og sender sin position via MTMF-lydsignaler til en modtagercomputer. Projektet inkluderer billedbehandling med MediaPipe, avanceret lydsignalbehandling og en skræddersyet kommunikationsprotokol.

---

## Projektoversigt

### Håndsporing og robotbevægelse  
Robotten benytter MediaPipe og OpenCV til at spore en persons hånd via webcam. Når hånden er over 50 cm væk, bevæger robotten sig mod den og opdaterer sin position i et (X,Y)-koordinatsystem. Bevægelse udføres med ROS Twist-kommandoer og konverteres til polære koordinater.

### MTMF-kommunikation  
Systemet bruger specialdesignede MTMF (Multi-Tone Multi-Frequency) signaler til at sende robotpositioner til en modtager. Signalerne består af fire samtidige toner, som repræsenterer en hex-værdi. En kontrol-array validerer signaler ved at kræve 3 gentagelser i en glidende vindue på 5.

### Kommunikationsprotokol  
Kommunikationen foregår i trin:
- Robotten sender position, modtageren ekko’er signalet tilbage  
- Robotten sammenligner og sender bekræftelse (FF, FE eller FD)  
- Modtageren bekræfter bekræftelsen  
Protokollen minimerer støj og fejltolkning med spejlede frekvensmatricer mellem sender og modtager.

### Audio processing  
FFT anvendes på lydsignalet for at finde dominerende frekvenser. Bins udenfor MTMF-matrix fjernes. Projektet anvender sample rate på 5120 Hz og frame size på 512 for optimal FFT-præcision.

---

## Inkluderede filer

- Semester_3___Projekt.pdf – Fuld rapport med metode, kommunikationsprotokol og eksperimenter  
- Python code/ – Mappe med Python-kildekode til robotstyring og signalbehandling:
  - TrackingRobot.py – Robotbevægelse og håndsporing
  - Receivercode.py – MTMF-dekodning og signalbekræftelse

---

## Udførte eksperimenter

- Vurdering af kommunikationsrækkevidde (maks. 3–4 meter)  
- Test af tonevarighed (optimal længde 0.5 sekunder)  
- Sammenligning af forskellige FFT-parametre  
- Analyse af signalfejl og støj i typiske rumscenarier

---

## Kompetencer

- Udvikling af realtids computer vision-systemer med MediaPipe  
- Avanceret FFT- og signalanalyse med NumPy  
- Udvikling af lydbaseret kommunikationsprotokol  
- Programmering af robotbevægelse via ROS og Python  
- Fejlhåndtering, signalverifikation og robusthedsanalyse  
- Teknisk dokumentation og systemintegration

---

## Bidragsydere

- Anas Butt Hussain  
- Alan Rashid  
- Jakub Hubert Rudowski  
- Patrick Ørsted Povey Andersen  
- Robin Hansen  
- Thomas Korsgaard Vilholm

---

## Intention

Dette projekt blev afleveret som en del af faget "Mobile Robotic Systems" på Syddansk Universitet og deles her for at fremvise kompetencer inden for robotik, signalbehandling og kommunikationssystemer.
