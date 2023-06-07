---

author: "Elia Tolin"

title: "Integrazione di Fastlane: Ottimizza lo sviluppo di app Flutter"

description: "Automatizzare i processi di deploy delle tue app Flutter tramite Fastlane."

tags:

- Flutter

categories:

- Flutter

date: 2023-06-07

image: "https://www.auroradigital.it/wp-content/uploads/2023/06/image.png"

latitude: 40.90025460

longitude: 14.27727490

altitude: 0.0000

---

![](https://www.auroradigital.it/wp-content/uploads/2023/06/image.png)

## Fastlane e Flutter

Fastlane è un potente strumento che offre numerosi vantaggi per lo sviluppo di app Flutter. Grazie alla sua suite di strumenti automatizzati, Fastlane semplifica e ottimizza il processo di distribuzione dell'app, consentendo agli sviluppatori di risparmiare tempo prezioso e migliorare l'efficienza complessiva del ciclo di sviluppo. In questo articolo, esploreremo i vantaggi dell'integrazione di Fastlane in un'app Flutter e forniremo esempi pratici per illustrare i risultati ottenibili.

Scopriamo insieme i vantaggi che ci può dare durante i nostri sviluppi.

## Automazione delle attività ripetitive

Fastlane automatizza le attività ripetitive e noiose associate allo sviluppo e alla distribuzione di app Flutter. Attraverso l'utilizzo di script e configurazioni personalizzabili, gli sviluppatori possono automatizzare processi come la creazione di file di configurazione, la firma dell'app, la generazione di screenshot e molto altro ancora. Ciò significa che gli sviluppatori possono concentrarsi sullo sviluppo delle funzionalità dell'applicazione senza dover dedicare tempo a compiti manuali e ripetitivi.

## Distribuzione semplificata

Fastlane semplifica il processo di distribuzione dell'applicazione Flutter su diverse piattaforme, come Google Play Store e App Store di Apple. Attraverso l'integrazione di Fastlane con gli strumenti di distribuzione, gli sviluppatori possono creare configurazioni centralizzate che consentono di gestire le versioni dell'app, di caricare automaticamente gli aggiornamenti sulle piattaforme desiderate e di gestire le impostazioni di distribuzione, come i certificati e le chiavi di firma. Questo rende il processo di distribuzione più rapido, accurato e privo di errori.

![](https://www.auroradigital.it/wp-content/uploads/2023/06/image-2-1024x538.png)

## Gestione dei rilasci multipli

Fastlane semplifica anche la gestione dei rilasci multipli di un'app Flutter. Attraverso l'utilizzo di lane (corsie), gli sviluppatori possono creare configurazioni separate per ciascun tipo di rilascio, ad esempio versioni beta, release candidate e versioni stabili. Ciò consente di eseguire facilmente rilasci di diversi livelli di stabilità e di automatizzare le attività specifiche associate a ciascun tipo di rilascio. Ad esempio, è possibile configurare Fastlane per inviare automaticamente un'email di notifica al team di controllo qualità quando viene effettuato un rilascio beta.

## Generazione di screenshot dinamici

Fastlane offre la possibilità di generare screenshot dinamici per le app Flutter, semplificando notevolmente il processo di creazione di immagini di anteprima per le diverse dimensioni dei dispositivi. Utilizzando lo strumento di generazione degli screenshot di Fastlane, è possibile automatizzare la cattura di screenshot di alta qualità per dispositivi specifici, come telefoni o tablet, in diverse lingue e impostazioni regionali.

Questa funzionalità è estremamente utile per presentare al meglio le tue app su Google Play Store e App Store di Apple, poiché offre una vista completa e realistica delle funzionalità dell'app su dispositivi di diverse dimensioni. Puoi anche personalizzare gli screenshot dinamici includendo dati di prova o informazioni dinamiche per mostrare l'app in un contesto reale.

Ad esempio, immagina di avere un'app di e-commerce. Utilizzando Fastlane, puoi creare screenshot dinamici che mostrano prodotti diversi o dati di esempio provenienti dal tuo backend. Ciò ti consente di evidenziare le caratteristiche principali dell'app e offrire una panoramica completa delle sue funzionalità senza dover creare manualmente screenshot per ogni possibile combinazione di dispositivi, lingue e impostazioni regionali.  

![](https://www.auroradigital.it/wp-content/uploads/2023/06/image-1-670x1024.png)

## Script d'esempio

Abbiamo creato un piccolo script che tramite un'alias si può invocare per eseguire le seguenti azioni:

-   Clean e pub get
-   Test
-   Incremento versione di Build
-   Build iOS e build Android
-   Deploy sugli store

<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C+184%2C+195%2C+1%29&t=one-dark&wt=none&l=auto&width=680&ds=true&dsyoff=20px&dsblur=68px&wc=true&wa=true&pv=56px&ph=56px&ln=false&fl=1&fm=Hack&fs=14px&lh=133%25&si=false&es=2x&wm=false&code=echo%2520%2522%2523%2523%2523%2520START%2520%2523%2523%2523%2522%250A%250Aecho%2520%2522%2523%2523%2523%2520TESTS%2520%2523%2523%2523%2522%250Aflutter%2520test%2520%2526%2526%250A%250Aecho%2520%2522%2523%2523%2523%2520CLEAN%2520%2523%2523%2523%2522%250Aflutter%2520clean%2520%2526%2526%2520%250A%250Aecho%2520%2522%2523%2523%2523%2520PUB%2520GET%2520%2523%2523%2523%2522%250Aflutter%2520pub%2520get%2520%2526%2526%250A%250Aecho%2520%2522%2523%2523%2523%2520INCREMENT%2520VERSION%2520%2523%2523%2523%2522%250A%2523%2520Estrae%2520la%2520versione%2520corrente%2520dal%2520file%2520pubspec.yaml%250AVERSION%253D%2524%28grep%2520%27version%253A%2520%27%2520pubspec.yaml%2520%257C%2520sed%2520%27s%252Fversion%253A%2520%252F%252F%27%2520%257C%2520tr%2520-d%2520%27%255Cn%27%2520%257C%2520tr%2520-d%2520%27%255Cr%27%2520%257C%2520cut%2520-d%2522%2520%2522%2520-f1%29%250A%250A%2523%2520Estrae%2520la%2520build%2520e%2520la%2520minor%2520versione%250AMAJOR%253D%2524%28echo%2520%2524VERSION%2520%257C%2520cut%2520-d.%2520-f1%29%250AMINOR%253D%2524%28echo%2520%2524VERSION%2520%257C%2520cut%2520-d.%2520-f2%29%250APATCH%253D%2524%28echo%2520%2524VERSION%2520%257C%2520cut%2520-d.%2520-f3%2520%257C%2520cut%2520-d%252B%2520-f1%29%250ABUILD%253D%2524%28echo%2520%2524VERSION%2520%257C%2520cut%2520-d%252B%2520-f2%29%250A%250A%2523%2520Incrementa%2520la%2520build%2520e%2520la%2520minor%2520versione%250APATCH%253D%2524%28%28PATCH%2520%252B%25201%29%29%250ABUILD%253D%2524%28%28BUILD%2520%252B%25201%29%29%250A%250A%2523%2520Costruisce%2520la%2520nuova%2520versione%250ANEW_VERSION%253D%2522%2524MAJOR.%2524MINOR.%2524PATCH%252B%2524BUILD%2522%250A%250A%2523%2520Sostituisce%2520la%2520vecchia%2520versione%2520con%2520la%2520nuova%2520nel%2520file%2520pubspec.yaml%250Ased%2520-i%2520%27%27%2520%2522s%252Fversion%253A%2520%2524VERSION%252Fversion%253A%2520%2524NEW_VERSION%252F%2522%2520pubspec.yaml%2520%2526%2526%250A%250A%2523%2520Stampa%2520la%2520nuova%2520versione%250Aecho%2520%2522FROM%2520%2524VERSION%2520TO%2520%2524NEW_VERSION%2522%2520%2526%2526%250A%250Aecho%2520%2522%2523%2523%2523%2520BUILD%2520IPA%2520%2523%2523%2523%2522%250Aflutter%2520build%2520ipa%2520%2526%2526%2520%250A%250Aecho%2520%2522%2523%2523%2523%2520BUILD%2520APPBUNDLE%2520%2523%2523%2523%2522%250Aflutter%2520build%2520appbundle%2520%2526%2526%2520%250A%250Aecho%2520%2522%2523%2523%2523%2520DEPLOY%2520APPLE%2520%2523%2523%2523%2522%250Acd%2520ios%2520%2526%2526%2520%250Afastlane%2520ios%2520release%2520%2526%2526%250A%250Acd%2520..%2520%2526%2526%2520%250A%250Aecho%2520%2522%2523%2523%2523%2520DEPLOY%2520ANDROID%2520%2523%2523%2523%2522%250Acd%2520android%2520%2526%2526%250Afastlane%2520android%2520deploy%2520%2526%2526%250A%250Aecho%2520%2522%2523%2523%2523%2520FINISH%2520%2523%2523%2523%2522"
  style="width: 1024px; height: 1122px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe>

## Conclusioni

L'integrazione di Fastlane nell'ecosistema di sviluppo di app Flutter porta numerosi vantaggi. L'automazione delle attività ripetitive, la semplificazione della distribuzione, la gestione dei rilasci multipli e il monitoraggio delle metriche di distribuzione contribuiscono a migliorare l'efficienza e la qualità complessiva del processo di sviluppo. Aggiungendo Fastlane alla tua cassetta degli attrezzi di sviluppo, potrai risparmiare tempo prezioso e concentrarti su ciò che conta di più: creare app Flutter straordinarie.

Link allo script:  [https://github.com/EliaTolin/automatic_deploy_fastlane_flutter](https://github.com/EliaTolin/automatic_deploy_fastlane_flutter)

Contattaci per scoprire come integrarlo nei tuoi progetti!