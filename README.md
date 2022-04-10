# ROS_autonomenFahren
  In den letzten Semestern habe ich Kurse zu maschinellem Lernen und Steuerungsmethoden belegt, und in meiner Freizeit habe ich mir C++ und ROS und einige grundlegende Algorithmen für autonomes Fahren selbst beigebracht. Aber ich kann das Prinzip immer noch nicht ganz verstehen. Deswegen habe ich zwei Projekte mit die Smart-Car-Plattform, die von mir gebaut wurden, gemacht, um die praktische Anwendung dieser Algorithmen besser zu verstehen. Und in Zukunft kann die Plattform genutzt werden, um einige Lösungen, die von praktischen Anwendungen benötigt werden, schnell zu verifizieren und umzusetzen.

## Projekt 1. Spurhalten

Hardware:  

  Kinematik-Modell(Fahrgestell): Heckantrieb, Ackermann-Lenkung；  
  Servomotor für Ackermann-Lenkung: MG996R;  
  Motortreiber: L298N;  
  Mikrokontroller: Raspberry Pi 4B+;  
  kamera Module: Raspberry Pi camera;  
  
  Das Design dieses Projekts ist grob in drei Teile gegliedert, Datenerfassung, neuronales Netzwerktraining und Modellladen.
  
  Die Idee der Beispielsammlung besteht darin, den aktuellen Bildschirm gleichzeitig mit dem Drücken einer Taste aufzuzeichnen und die Beschriftung der Taste hinzuzufügen. Zum Beispiel beim Drücken der Taste "Links abbiegen", den aktuellen Bildschirm aufzeichnen und Fügen Sie ein Label von "Links abbiegen" hinzu. . Dasselbe gilt für andere Richtungen, hier werden nur drei Bezeichnungen verwendet, nämlich: „vorwärts“, „links abbiegen“, „rechts abbiegen“. Um die Interferenzen im Bild zu reduzieren, wird das Bild einer gewissen Verarbeitung unterzogen.Der allgemeine Prozess ist: Filtern – Umwandeln in Graustufen – Binärisieren und schließlich Verwenden des binarisierten Bildes als Probe.
  
  Hier kommt direkt das Machine-Learning-Modul von OpenCV zum Einsatz，um das Modell zu trainieren. Das trainierte Modell erreichte eine Genauigkeit von 92%。
  
  Mit diesem Modell kann der smart Car lange Zeit problemlos auf der gebauten Strecke fahren. 
  
  Hier zeigt das Ergebnis:
  ![image](https://github.com/HongshenLiu/ROS_autonomenFahren/blob/master/opencv_car/result.gif)

## Projekt 2: Autonome Navigation und Hindernisse vermeiden

Hardware:  

  Kinematik-Modell(Fahrgestell): Differentialantrieb;  
  2x Motor: TT-DC-Getriebemotor mit einem Übersetzungsverhältnis von 1:48;  
  2x Encoder: Hall-Encoder;  
  Motortreiber: L298N;  
  Mikrokontroller: Raspberry Pi 4B+;  
  Motorantrieb: Arduino mega 2560;  
  Imu: MPU6050;  
  lidar: Slam A1;  
  
In diesem Projekt erfolgte die Geschwindigkeitsregelung mit dem PID-Algorithmus auf dem Arduino-Board. Die Kommunikation zwischen Raspberry Pi und Arduino-Board, die Funktionen des Kartenaufbaus, der Navigation und der automatischen Hindernisvermeidung wurden realisiert. Die Daten vom imu, die durch Kalmanfilter gefiltert werden, hat mit den Encoderdaten fusioniert, damit der Kilometerzähler optimiert wurde.  

Hier zeigt das Ergebnis:
![image](https://github.com/HongshenLiu/ROS_autonomenFahren/blob/master/Smart_car/result.gif)

  

  
  
  
