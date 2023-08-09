# ExpenseControlAngular

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.2.7.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

///////////////////////////////////////////   installa firebaseHosting

1) npm install -g firebase-tools ->  to install in a progect
2) firebase login  -> per accedere con il proprio account firebase
3) firebase init -> per inizializzare. Scelto firebase hosting per poter "pubblicare il sito"
                -> public directori scelto "dist" anzi che "public" perche in fase di compilazione tutto parte da dist/... forse crea conflitti dopo.
::Per poter hostare il progetto nel angular.json sevre modificare un certo "outputPath": dist -> perche di defoult e dist/[nomeProgetto]
    : npm run build -> una volta fatta la modifica si fa questo comando per rifare la build
    : firebase deploy -> per poter visualizzare il sito !!!!

///////////////////////////////////////////   Continues delivery : google cloud-> attivi un servizio che si chiama cloud build
Ogni volta che faccio push su github mi aggiorna anche la build fatta sul sito
E gratis fino a 120 minuti di utilizz, per un progetto normale si va sui 4 min totali

Una volta attivato il servizio si scieglie il la repository con la quale si vuole connettere.
                        In configuration: 
Si scieglie il file di configurazione di cloud Build(yaml o json)
Gli si sa una locazione al file, nel mio caso: /pipelines/build.yaml
Nel file va una configurazione abbastanza standart che indica step by step come deve fare la build

nel primo -Name del .yaml usa docker per avviare uno script,  non sono sicuro a cosa Tutto nei folder come indicato nel file
nel codice di quel file ci sono delle variavili ${cose}, dove serve il token e idProgetto,
    per il primo si fa :firebase login:ci -> si accede poi si ottiene il token,
    per il secondo, si trova della bash del progetto firebase.
Per questi due parametnri ci sono dei spazi apositi nel cloud build in impostazioni avanzate
Dopo fai crea per generare il triger