---

author: "Elia Tolin"

title: "Infinity Minesweeper - Un gioco in Flutter"

description: "Un esperimento ben riuscito, sviluppare un gioco in flutter ed è nato Infinity Minesweeper."

tags:

- App
- Flutter

categories:

- Flutter

date: 2023-06-01

image: "https://www.auroradigital.it/wp-content/uploads/2022/05/Feature-1.jpg"

latitude: 40.90025460

longitude: 14.27727490

altitude: 0.0000

---
Un gioco ridisegnato da Aurora.

![](https://www.auroradigital.it/wp-content/uploads/2022/05/Feature-1.jpg)

Siamo onesti, tutti nella vita almeno una volta abbiamo visto o giocato a campo minato.  
Vi do due indizi per ricordarvelo: Bombe e numeri.

![](https://cdn.mos.cms.futurecdn.net/f873f2282e16faeebdb4a09e2f3cef32.jpg)

Campo Minato su Windows XP

Nel dicembre 2021 è tornata la voglia di fare una partita e cercando su AppStore un Minesweeper (traduzione di Campo Minato in Inglese) ho notato che tutte le app sviluppate avevano la stessa grafica, identica, inoltre con layout poco moderni.

Allora da li si è accesa la lampadina e lo sviluppo di  **Infinity Minesweeper**  è partito.

Come Framework,  **Flutter**, scelta abbastanza scontata in quanto grande appassionato d'esso.

#### UI/UX

L'obiettivo è stato fin dall'inizio di creare una proposta con un' UI (User Interface) totalmente ridisegnata e la scelta è caduta tra un stile mixato tra  **Neumorphic e Material**.  
Riguardo a Neumorphic, probabilmente, anzi sicuramente, è stata una scelta insolita visto che si tratta di fatto di un gioco, ma si è cercato d'uscire dagli schemi.  
L'effetto voluto era qualcosa di pulito con anche un UX semplice.

![](https://www.auroradigital.it/wp-content/uploads/2022/05/Simulator-Screen-Shot-iPhone-13-Pro-Max-2022-02-19-at-09.38.13-473x1024.png)

Una delle prime versioni.

![](https://www.auroradigital.it/wp-content/uploads/2022/05/Simulator-Screen-Shot-iPhone-13-2022-04-04-at-14.21.32-473x1024.png)

#### Backend & Algoritmi

Finito lo sviluppo della parte del Frontend, è toccata la parte di Backend e sono iniziati i dolori, grandi dolori...  
Per ogni campo di gioco esiste il rischio che esso sia non risolvibile senza inciampare in una serie di caselle la cui possibilità di scelta per dove piazzare la bandiera non sia 50 / 50. Ecco a voi un'esempio:

![](https://upload.wikimedia.org/wikipedia/commons/c/cf/Minesweeper_guess_1_generic.svg)

Qui dove piazziamo la bandiera? Cioè secondo voi dov'è la bomba?  
Non è possibile andare a logica, si è in una situazione di stallo chiamata anche "Guessing".

Per evitare ciò in Infinity Minesweeper è stato integrato un algoritmo di No Guessing, cioè viene controllato ogni campo dopo averlo generato se questa problematica esiste oppure no.  
L'algoritmo è di Simon Tatham (potete trovare i suoi algoritmi  [qui](https://www.chiark.greenend.org.uk/~sgtatham/puzzles/)).  
Simon Tatham non è niente meno che anche il creatore di PuTTY.  
Il suo algoritmo è stato quindi estratto e convertito in Dart per poi utilizzarlo su Flutter, lacrimando sangue ma ne è valsa la pena.  

Durante lo sviluppo è seguita una campagna di test effettuata giornalmente, per trovare eventuali Bug che si creavano durante la scrittura di codice.  

#### GameCenter e Google Play Giochi

![](https://developer.apple.com/news/images/og/game-center-og-twitter.jpg)

Una scelta che è stata effettuata è stata di integrare i servizi di gioco delle piattaforme, per inserire una Leaderboard dove confrontarsi con gli altri giocatori stimolando a fare un tempo sempre migliore fino a scalare la classifica.

Per l'integrazione è stato utilizzato il package  [Games Services,](https://pub.dev/packages/games_services)  l'integrazione dei servizi non è stata affatto banale.  

Per iOS non sono stati riscontrati grandi problemi è filato tutto più o meno tutto liscio, mentre cosa nettamente contraria per la piattaforma Android dove le problematiche sono state molte.  
  
La prima riscontrata su Android è stata l'impossibilità di loggarsi con il servizio Giochi nell'applicazione, risolta dopo molte serenate e poesie. La problematica era derivante dalla chiave SHA1 di produzione che non corrispondeva a quella presente nella parte di Google Cloud.  
Seconda problematica è stata l'impossibilità di inviare gli score nelle classifiche, anch'essa risolta in modo molto similare alla precedente, cambiando la chiave SHA1 sempre.

#### Monetizzazione

![](https://bookface-images.s3.amazonaws.com/logos/9e4e84730f397134deb894a9ffcfab9c58396ec8.png)

Per la monetizzazione è stata fatta la scelta di includere una politica pubblicitaria.  
Tramite AdMob viene generata la pubblicità che è possibile togliere tramite un piccolo contributo nella sezione Acquisti.  
Le opzioni era la possibilità di acquisti di diversi temi o possibilità di continuare la partita in caso d'errore, magari entrambi tramite l'acquisto di gettoni utilizzabili nel gioco. Ma entrambi le scelte non mi facevano impazzire in quanto Infinity Minesweeper ha come obiettivo il portare una valida alternativa alle più "professionali" scelte online.  
  
Per gli acquisti è stata utilizzata la piattaforma Revenue Cat.

#### Considerazioni finali

![](https://www.auroradigital.it/wp-content/uploads/2022/05/Icon-final.png)

Il divertimento dello sviluppo di quest'App è stato veramente tanto nonostante alcune problematiche non divertenti, ma sicuramente Aurora continuerà a rilasciare nuove Features e miglioramenti di Infinity Minesweeper.

L'applicazione ad oggi è presente da poco sia su PlayStore che AppStore in lingua Italiana e Inglese.

Ovviamente il tutto è  [OpenSource](https://github.com/EliaTolin/infinity_sweeper).

[![](https://specifications-pro.com/wp-content/uploads/2019/12/%D9%85%D8%AA%D8%AC%D8%B1.jpg)](http://onelink.to/eqehvm)