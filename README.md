# Vremenska aplikacija

Izdelal sem testno nalogo, po poslanih navodilih.

Kodo lahko prenesete iz GitHuba in mapo odprete v izbranem programu. Ko se nahajate v izbrani mapi od aplikacije, jo lahko pozenete sami z naslednjimi ukazi (potreben NPM):

```
npm install
```
```
npm run serve
```
 Lahko jo pa preizkusite na moji domeni: https://nejcklopcic.space/weather/


## Delovanje in uporaba aplikacije

V iskalno polje vpišite naslov mesta, za katerega želite, da se izpiše vreme. V kolikor so podatki za željeno mesto na voljo, bo vmesnik vrnil vreme in pod zgodovino iskanj dodal vaš iskani niz. V kolikor mesto ni na voljo, bo vmesnik uporabnika o tem obvestil. Vnos praznih polj je onemogočen.

Vmesnik beleži zadnjih 5 uspešnih vremenskih poizvedb in jih prikaže na zaslon. S klikom na katerokoli izmed zgodovin se v iskalno polje prepiše niz (mesto), na katerega ste kliknili. Prav tako se zgodovina popravi in se niz (mesto), na katerega ste kliknili, postavi na prvo mesto v zgodovini iskanj.

Pri prikazu vremena lahko vidimo:

 - Trenutno temperaturo
 - Občutek
 - Najnižjo temperaturo v dnevu
 - Najvišjo temperaturo v dnevu
 - Vlažnost

Aplikacijo sem izdeloval po navodilih in jo še malo dopolnil z CSSjem. Želel sem tudi čim bolje razvrstiti elemente, obvestiti uporabnika o napaki in preprečiti prazen vnos v polje.

Sama koda je sestavljena iz glavne strani in treh komponent. Search, Search History in Show Weather. Imena sem poimenoval logično po temu, kar določena komponenta dela.

V kolikor imate dodatna vprašanja me kontaktirajte.


## Zanimivosti pri izdelovanju aplikacije: 

Na svetu obstaja mesto "Solata" (Italija) - Sprva sem mislil da mi program ne deluje pravilno
Na svetu obstaja veliko mest z imenom Banana.

