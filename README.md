# Vježba 1: Inicijalizacija NextJS projekta i uvod u JS

Cilj ove vježbe je inicijalizirati NextJS projekt i upoznati se s Javascript jezikom.

## Javascript ekosustav i NodeJS

Javascript ekosustav okolina je Javascripta koja se sastoji od biblioteka, softverskih paketa, editora i ostalih resursa koji omogućuju i olakšavaju razvoj JS aplikacija.

[Izvor](https://www.altexsoft.com/blog/engineering/javascript-ecosystem-38-tools-for-front-and-back-end-development/)

U ovom poglavlju fokusirat ćemo se na _package manager_ aplikaciju koja omogućuje jednostavan i brz pristup repozitoriju gotovog koda kako ne bismo nepotrebno rješavali riješene probleme. Korištenje ovim paketima besplatno je jer su dani kao _open source_ softver.

Kao što znamo, Javascript je jezik koji se isključivo izvršava unutar _web_-pretraživača (Chrome, Firefox i sl.), međutim postoji run-time okruženje za pokretanje Javascript koda izvan okvira pretraživača, a to je okruženje **NodeJS**.

## NodeJS

Pojednostavljeno, NodeJS je program koji može pokretati Javascript kod s tvrdog diska slično kao što Java run-time može pokrenuti Javu. Princip rada je jednostavan: NodeJS enkapsulira **V8** engine, što je upravo Javascript engine koji koristi Chrome pretraživač. Možemo reći da je NodeJS izvadio motor automobila i pokreće taj motor izvan automobila i koristi se njime za druge namjene. Ta namjena najčešće je _web_-server, stoga se NodeJS često zove "Javascript za servere". Način izvršavanja jako je sličan izvršavanju Java koda.

 <div align="center">
  <img src="https://www.freecodecamp.org/news/content/images/2019/06/1_sYPllpcAZLHmpuQSRPuO0Q.png" />
 </div>

Nećemo ulaziti detaljnije u izvedbu jer nije u okviru onog što se radi na ovom kolegiju, ali za one koje zanima ovdje je [izvor](https://www.freecodecamp.org/news/what-exactly-is-node-js-ae36e97449f5/).

## NPM: Package manager

Instalacija NodeJS-a neophodna je za rad s modernim Javascriptom čak i ako ne radimo serverske aplikacije. Jedan od razloga je _NPM_. NPM je **Node Package Manager**. To je dio instalacije NodeJS-a i JS ekosustava, a njegova svrha je instalacija softverskih paketa i upravljanje stablom ovisnosti paketa (dependency tree) što brže i efikasnije. NPM se može pozvati iz komandnog prozora nakon instalacije NodeJS-a. Koristit ćemo se njime da bi instalirali NextJS.

## Što je NextJS

Ukratko, **NextJS** je metaframework za ReactJS za izradu full stack web aplikacija s mogućnostima SSR-a (Server Side Rendering). Početnicima to ne znači ništa pa pokušajmo ovako. NextJS je alat koji se naslanja na ReactJS i pojednostavljuje i poboljšava njegovo korštenje za neke primjene. Jedna od njih je ova koju ćemo raditi, a to je static/server side stranica. Primijetimo da je podjela Client/Server po sredini NextJS okvira na slici.

<img src="https://nextjs.org/static/images/learn/foundations/next-app.png" />

Bit će jasnije kad započnemo s radom, ali prije toga trebamo instalirati alate.

## Instalacija

Potrebno je instalirati 3 stvari:

- Node i NPM (idu skupa)
- Git
- VSCode

### NodeJS i NPM

Za _windows_ korisnike, potrebno je skinuti NodeJS instaler sa [službene stranice](https://nodejs.org/en/). Uvijek skidamo LTS verziju ("long term support"). Non-LTS verzije su **nešto kao** "beta" verzije.

Nakon instalacije, možemo potvrditi da je sve prošlo u redu koristeći terminal:

```bash
$ node -v
--
$ npm -v
```

Ako neka od naredbi daje _error_ umjesto verzije softvera, instalacija nije prošla uredno. Za Windows je čest _error_ da se `node.exe` ne doda u _system path variable_. Simptom je da se naredba "node" ne može pronaći (not found ili not recognized error). Problem je lako [riješiti](https://stackoverflow.com/questions/27864040/fixing-npm-path-in-windows-8-and-10).

Kao i za sve na Windowsu, postoji setup.exe za instalaciju gita. Ovdje je [link](https://git-scm.com/download/win) za Windows setup file.
Default postavke su u redu, ali treba paziti da je `add to your PATH` **označen**. Inače, doći će do problema opisanog ispod. Ako je sve prošlo u redu, `git --version` treba raditi:

```bash
$ git --version
```

Kao i kod Node-a moguće je da git.exe ne bude dodan u path. Problem se rješava istim [postupkom](https://www.computerhope.com/issues/ch000549.htm) kao i za Node. Stackoverflow pitanje [ovdje](https://stackoverflow.com/questions/31167181/adding-git-to-path-variable-cant-find-github-under-appdata-local)

### VSCode (or not)

U redu, sad je sve spremno, ali kako i gdje pišemo kod?

Ne postoji ograničenje za korištenje editora, ali preporučuje se [VSCode](https://code.visualstudio.com/). Alternativa su [Atom](https://atom.io/) i [WebStorm](https://www.jetbrains.com/webstorm/), koji toplo preporučujem ako vam se ne sviđa VSCode. Inače se plaća, ali ga studenti FESB-a [mogu dobiti besplatno](https://www.jetbrains.com/community/education/#students). Smatra se najboljim editorom trenutačno, a u stopu ga slijedi VSCode.

Za hardcore linuxaše preporučam NeoVIM sa TS/JS setupom.

## NextJS instalacija

Nikad lakša!

1. U terminalu napravimo folder za projekt
2. Uđemo u folder sa `cd folderName`
3. Pratimo upute na linku ispod koje su zapravo samo  
   `npx create-next-app@latest .`
4. Ukoliko ste klonirali ovaj branch onda će README file smetati. Možemo ga izbrisati ili napraviti `npx create-next-app@latest noviFolder`

Upute  
https://nextjs.org/docs

## Folder structure

Službeno objašnjenje [Here](https://nextjs.org/docs/basic-features/pages), ali ukratko:

1. `pages` folder: Tu se nalaze stranice naše aplikacije.
2. `node_modules`: Sadrži sve potrebne pakete i module za rad NextJS-a uključujući React
3. `public` folder će biti finalni kod aplikacije. Ovaj kod onda možemo pokrenuti ili prebaciti na USB, server ili neku drugu lokaciju za pohranu i serviranje naše stranice.
4. `styles` sadrži globalni CSS
5. `.nešto` datoteke su config datoteke za pojedine alate. Više o tome i ostalim folderima u daljnjem radu

## Stvorimo novi page

Unutar pages foldera stvorimo datoteku `moja-stranica.js`.

Zalijepimo sljedeći kod unutra:

```jsx
import React from "react";

const MojaStranica = () => (
  <div>
    <h1>Moja stranica</h1>
  </div>
);

export default MojaStranica;
```

Ako u browseru idemo na `/moja-stranica` vidjet ćemo novu stranicu.
