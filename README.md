# COȘ DE GUNOI INTELIGENT 
<p align="center">
  <img src="https://user-images.githubusercontent.com/77394602/166941937-1ae8a83a-ef74-480b-8b5a-a39274446c3a.png" />
</p>

**Tema proiectului:**

Acest proiect este realizat prin programarea unui microcontroller Arduino Mega 2560. Deschiderea coșului de gunoi se face automat prin intermediul unui motor pas cu pas și al unui senzor de distanță. O altă funcționalitate a coșului de gunoi este detecția de supraplin. Atunci când coșul de gunoi este plin, acesta va avea un semnal sonor specific realizat de un buzzer. În interiorul coșului se află plasat un alt senzor pentru distanță. Când acesta detectează obiecte foarte apropiate de el, placa va emite prin buzzer un cântec.

**Elemente componente:**

  1.	Microcontroller Arduino Mega 2560
  2.	Motor Pas cu Pas 28BYJ-48 5V
  3.	Driver ULN2003 
  4.	2 x Senzor ultrasonic HC-SR04
  5.	Buzzer activ 5V
   
<p align="center">
<img src="https://user-images.githubusercontent.com/77394602/166943824-ceb78784-5843-4667-ae73-743d2b54c11a.png" />
<img src="https://user-images.githubusercontent.com/77394602/166944010-35ab1496-e524-45fc-9fb9-0495ea180fb9.png" />

</p>
   
**Program:**

Am utilizat limbajul de programare C++ alături de Software-ul open-source Arduino (IDE) care facilitează scrierea și încărcarea codului pe placă.
  
**Pentru controlul motorului**, este folosita biblioteca Stepper.h. Metodele folosite din această bibliotecă sunt: 

•	Stepper()
Creează o nouă instanță a clasei Stepper. Se foloseste la început, înaintea metodelor setup() și loop(). 
Ca parametrii am adăugat numărul de pași într-o revoluție a motorului (2048), alături de cei 4 pini folositi de pe plăcută in care am conectat driverul.

•	setSpeed()
Stabilește viteza motorului în rotații pe minut (RPM).

•	step()
Rotește motorul un anumit număr de pași, la o viteză determinată de cel mai recent apel al metodei setSpeed(). Această funcție este blocantă, adică va aștepta până când motorul termină mișcarea pentru a trece controlul la următoarea linie din cod.
Am programat coșsul de gunoi să se deschidă la 90 de grade și apoi să revină la poziția inițială.
motor.step(-stepsPerRevolution/4);
motor.step(stepsPerRevolution/4);

**Pentru calcularea distanțelor** necesare proiectului, am folosit 2 senzori. Senzorul cu ultrasunete HC-SR04 emite ultrasunete la 40 kHz care se deplasează prin aer și dacă există un obiect sau un obstacol pe calea lui, se va întoarce înapoi la modul. Distanța este calculată ținând cont de timp și de viteza sunetului, 
Pe un senzor sunt 4 pini: 2 pentru GND si +5V și 2 care se pot conecta la orice I/O digitală din placa Arduino (TRIG și ECHO).
duration = pulseIn(echoPin, HIGH);
distance = duration*0.034/2;

**Pentru melodia emisă prin buzzer**, am folosit funcția tone() alături de biblioteca pitches.h. Această bibliotecă conține toate valorile de intonație pentru notele muzicale. De exemplu, NOTE_C4 este Do mijlociu și NOTE_FS4 este Fa diez. Această tabelă de note a fost scrisă inițial de Brett Hagman.
Funcția tone() generează o undă cu frecvența specificată pe un pin. Aceasta continuă până la un apel al funcției noTone(). Pinul este conectat la un buzzer.
tone() a primit ca parametrii: pinul la care este conectat buzzerul, melodia - notă cu notă- și durata.
Melodia aleasă este definită de doi vectori: unul cu notele necesare acesteia și unul cu durata notelor.

        



