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
###### Un gioco ridisegnato da Aurora.

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

![](data:image/png;base64,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)

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