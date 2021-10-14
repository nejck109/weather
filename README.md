# Vremenska aplikacija

Izdelal sem testno nalogo, po poslanih navodilih.

Kodo lahko prenesete iz GitHuba in mapo odprete v izbranem programu. Ko se nahajate v izbrani mapi od aplikacije, jo lahko pozenete sami z naslednjimi ukazi:

```
npm install
```
```
npm run serve
```
 Lahko jo pa preizkusite na moji domeni: https://nejcklopcic.space/weather/


## Delovanje in uporaba aplikacije

V iskalno polje vpišite naslov mesta, za katerega želite da se izpiše vreme. V kolikor so podatki za željeno mesto na voljo, bo vmesnik vrnil vreme in pod zgodovino iskanj dodal vaš iskani niz. V kolikor mesto ni na voljo, bo vmesnik uporabnika o tem obvestil. Vnos praznih polj je onemogočen. 

Vmesnik beleži zadnjih 5 uspešnih vremenskih poizvedb in jih prikaže na zaslon. S klikom na katerokoli izmed zgodovin, se v iskalno polje prepiše niz (mesto) na katerega ste kliknili. Prav tako se zgodovina popravi, in se niz (mesto) na katerega ste kliknili postavi na prvo mesto v zgodovini iskanj.

Pri prikazu vremena lahko vidimo:
 - Trenutno temperaturo
 - Občutek
 - Najnižjo temperaturo v dnevu
 - Najvišjo temperaturo v dnevu
 - Vlažnost
