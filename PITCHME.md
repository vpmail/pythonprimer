
## Python előzetes

---

## Miért Python?

- általános, objektumorientált, alacsony belépési korlát, ragasztónyelv, moduláris, dimanikus, interpretált
- ingyenes, masszív közösség — közel valós idejű segítség a stackoverflow-n (is)
- adattudományokban, gépi tanulásban népszerű, R-et is jól kiegészíti
- online interpreter pl.: [https://repl.it](https://repl.it)
- online prezentáció:     [http://deckdown.org](http://deckdown.org)
- online markdown editor: [https://dillinger.io](https://dillinger.io)

---

## Alapinformációk

- verziók 2-es vs 3-as, sajnos nem mindegy, pl.  `print "Gomba"` vs `print("Ananász")`
- konzol: interaktív (mint az R)
	- van egy sima vanília, QtConsole és webes, a Jupyter Notebook (ahogy az lenni szokott, mindegyiknek van előnye és hátránya is)
- vagy script

---

## Alapvető szintaktika, adattípusok

- arithmetika: kétféle osztás a számábrázolás miatt, modulo azaz `%`, `math` modul
- bool logika
	- `True`, `False`
	- `not`, `and`, `or` — precedencia
- adattípusok: sztring, dátum és idő, szám — `int`, `float` —, logikai (`bool`)
- konverziók: `float()`, `str()`, `int()`

---

- sztringek
	- többsoros sztring: `'''valami'''`
	- konkatenáció: `+`
	- formázás `%`-kal, zero padding
	- escape karakter: `\`
	- indexelés: 0-tól indul (⇔ GNU R, de itt is tömbszerűen viselkedik, R-ben vektor a neve)
	- kapcsolódó eljárások: `len()`, `str()`, `.upper()`, `.lower()`
- dátum és idő
	- `.now()` metódus, `.year`, `.month`, `.day` tulajdonságok, zero padding `%`-os formázás
	
---
	
## Adatszerkezetek

---

### Listák

```

zoo_animals = ["pangolin", "cassowary", "sloth", "tiger"]
empty_list = []
zoo_animals[0] 		# indexelés
zoo_animals[3]="cat"	# indexelve értékadás

```

- lista metódusok: pl. `empty_list.append("majom")`

---

- slicing: 
`letters = ['a', 'b', 'c', 'd', 'e']; slice = letters[1:3]`
	- szintaktikailag olyan, mint az R-ben, de máshogyan működik: 0-val indul és a `:N`-t már nem tartalmazza!
	- pl. `suitcase = ["sunglasses", "hat", "passport", "laptop", "suit", "shoes"]; last =  suitcase[4:6];`
	- visszatérve a sztringekre: karakterek listái, így hasonlóan szeletelhetők
	- további példák: `suitcase[:3]; suitcase[2:]; # Ki mit tippel? Ezek mit jelentenek?`
	- fordítva is működik: 
	
```

animals = ["aardvark", "badger", "duck", "emu", "fennec fox"]
duck_index = animals.index("duck")

```

---

- az `.append()`-et már láttuk, de van `.insert()` is, ami kéri az indexet is: `animals.insert(duck_index, "cobra"); print(animals)`
- lista elemein való művelet: `for` ciklus:
	- `for variable in list_name:`
- lista rendezése: `.sort()`

```

animals = ["cat", "ant", "bat"]
animals.sort()
for animal in animals:
  print(animal)
  
```

- a listák bővíthetők, elemeik megváltoztathatók (mutable), pl. `.remove()` metódus
- a sztringek is listák, pl. `for` ciklussal végig lehet rajtuk iterálni

---

### Szótárak

- olyan mint a lista, csak kulccsal (névvel) és nem index-szel tudunk az elemekre hivatkozni
- szintaktikája kapcsos zárójel, pl.: `residents = {'Puffin' : 104, 'Sloth' : 105, 'Burmese Python' : 106}`
- mint a listák, a szótárak is bővíthetők, elemeik megváltoztathatók (mutable)
- a szótár különböző típusokat tárolhat, sztringeket, egészeket, bool értékeket, sőt akár listákat is!
- a szótár nem rendezett, pl. egy `for` ciklus kb. véletlenszerűen halad át rajta

---

- iterálás szótárakon
	- `.items()` — a sorrend véletlenszerű!
		- tuple-k listáját adja vissza: a kulcsok és értékek párosai
			- a tuple szintén egy adatszerkezet, egy megváltoztathatatlan lista, () jel határolja és bármilyen adattípust tartalmazhat
	- `.keys()`, `.values()`
	
---
			              
## Függvény deklaráció

```

def using_control_once():
  if True:
    return "Success #1"

```

- identáció fontos
- függvény hívás
- paraméterek (pl. `n`) és argumentumok (pl. `10`)

---
	
## Feltételvizsgálat és elágaztatás

```

if 8 < 9:
  print("Eight is less than nine!")
else:
  print(False)

```

- identáció jelentősége, kettőspont, kódblokk, egyedi

---

- `elif`, `else`

```

def greater_less_equal_5(x):
  if x > 5:
    return 1
  elif x < 5:         
    return -1
  else:
    return 0

```

---

- van tipp?

```

print(greater_less_equal_5(4))
print(greater_less_equal_5(5))
print(greater_less_equal_5(6))

```

---

- `import`

```

import math
print(math.sqrt(25))

from module import function
from module import *

## de nem jó ötlet mindent importálni, névütközés léphet fel

```

- egyéb beépített (nem modul) függvények
	- `min()`, `max()`, `abs()`, `type()`
- egyéb modul függvények
	- `from random import randint`
	
---

## Hurkok

- amíg a `condition == True` addig kiértékelésre kerül a kódblokk (identáció) 
- `while condition:`
	- `break`
	- `continue`

---

## Egyéb mélyebb témák

- list comprehension: pl. `evens_to_50 = [i for i in range(51) if i % 2 == 0] # for/in/if`
- lista szeletelés: 

```

l = [i ** 2 for i in range(1, 11)]
## Should be [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

print(l[2:9:2])

```

---

- index elhagyása: az indexálandó lista első vagy utolsó elemét jelenti, jobbról nyílt intervallum! Pl. `print(range(1, 11)[::2])`
	- a negatív lépésköz jobbról balra haladást jelent
	
---

- lambda függvények, funkcionális programozás: függvényeket használhatunk, mint változókat, sőt ezek lehetnek névtelenek is (lambda):

```

my_list = range(16)
print(filter(lambda x: x % 3 == 0, my_list))

## többször használatos függvényt persze, továbbra is érdemes def-fel deklarálni

```

---

- bitszintű operátorok
	- minden számítógépen tárolt adat, kód bitekkel, azaz 0-kal és 1-kel kerülnek reprezentálásra
	- ezek az operátorok bitszinten működnek
	- érdekesek, de a gyakorlatunkban kevésbé hasznosak
- különböző számrendszerekben való ábrázolás: főleg bináris, hexadecimális jöhet itt szóba — nekünk nem különösebben fontos

---

## Objektumorientált

- az osztály egy adatstruktúra definíciója: pl. gyümölcs, dolgozó
- az objektum az osztály egy megvalósult példánya
- a Python objektum orientált nyelv, alapvetően objektumokon dolgozik
- egy objektum rendelkezhet adatokkal, tulajdonságokkal, metódusokkal

---

- pl. a `len("Valami...")`, kikeresi a sztring hosszúság tulajdonságát, és mint egész számot adja vissza
- minden sztring egy szülőosztály leszármazottja, annak tulajdonságaival (pl. hossz), metódusaival rendelkezik
- az osztály definíciója hasonlít a függvényhez: `class NewClass(object):` (ahol az object a szülőosztály, amitől örököl)
- sok megismételt kódolást (így hibalehetőséget) lehet így megspórolni, talán ez a koncepció lényege — az **újrahasznosítás**

---

- `__init__()` eljárás és `self` paraméter
- változók scope-jai: globális, osztályonkénti és példányonkénti
	- nagy a jelentősége, de most nem megyünk bele, ha valakit megőrjít a kíváncsiság, rákeres
- az öröklődés mellet az egyes szülőosztályok metódusait override-olni is lehet (ettől még el lehet érni a szülőosztály eredeti metódusát)
- valójában az `__init__()` is létező `object` metódus, csak általában override-oljuk
- `__repr__()` a reprezentációért felel

---

## „Ragasztó” nyelv

- talán minden programnyelvhez van összeköttetése
- különböző programozási nyelvek eltérő képességeit egy összefogó nyelvvel egyesíteni lehet
- magas szinten alacsony szintű eljárásokat tud összefogni

---

## Alkalmazás az MNB-ben

- a GNU R kiegészítésére alkalmas — a Python hívható R-ből, és fordítva
- alacsonyabb belépési korlát, az R tanulásában is hasznos
- képes adatbázis kapcsolatra pl. ODBC-n vagy natív konnektorokkal (akár Sybase, Oracle, MSSQL)

---

- van hozzá tudományos alkalmazásokra kifejlesztett csomag, a `scipy`: optimalizáció, lineáris algebra, numerikus integráció, Fourier transzformációk, statisztika stb.
- `statmodels` — kimondottan statisztika
- `pandas` — magas szintű adatszerkezet: `DataFrame`, amelyen fejlett (akár többszörös) indexálás, csoportosítás, `merge()`, `join()`, `concat()` műveletek végezhetők
  - `SQLAlchemy` segítségével sokféle adatbázisból közvetlenül `DataFrame`-be kérhetünk le adatokat

---

- a `numpy` — lineáris algebra, eloszlások, véletlenszám generálás
- `SymPy` — szimbolikus matematika
- `scikit-learn`, `keras` — gépi tanulás
- az objektumorientált volta miatt pl. a Svensson illesztés nagyon kulturáltan megvalósítható lenne
	- szignifikánsan gyorsabb futás várható
- fejlett grafikai képességek ⇒ akár dashboard alkalmazásokhoz is felhasználható
- más szakterületek is alkalmazhatják

---

## Szimulációs példa: várakozási paradoxon

- 10 percenként jár a busz
- joggal (pontosabban: naívan) feltételezhetjük, hogy átlagosan 5 percet kell várakoznunk rá
- ha megmérjük az utasok átlagos várakozási idejét, mégsem így van
- :-), sorry, ez van...
- nézzük meg a szimulációját! ([Forrás: http://jakevdp.github.io/blog/2018/09/13/waiting-time-paradox/](http://jakevdp.github.io/blog/2018/09/13/waiting-time-paradox/))

---

- `numpy` csomagot fogjuk használni

```
import numpy as np

N = 1000000  # number of buses
tau = 10  # average minutes between arrivals

rand = np.random.RandomState(42)  # universal random seed
bus_arrival_times = N * tau * np.sort(rand.rand(N))
```

- az intervallumok átlagai:

```

intervals = np.diff(bus_arrival_times)
intervals.mean()

```

- ami kb. 10.0

---

- most szimuláljuk a beérkező utasok várakozási idejét!
- függvényt deklarálunk hozzá:

---

```

def simulate_wait_times(arrival_times,
                        rseed=8675309,  # Jenny's random seed
                        n_passengers=1000000):
    rand = np.random.RandomState(rseed)
    
    arrival_times = np.asarray(arrival_times)
    passenger_times = arrival_times.max() * rand.rand(n_passengers)

    # find the index of the next bus for each simulated passenger
    i = np.searchsorted(arrival_times, passenger_times, side='right')

    return arrival_times[i] - passenger_times
    
```

---

- és végül a várakozási idők átlagát is kiszámolhatjuk:

```

wait_times = simulate_wait_times(bus_arrival_times)
wait_times.mean()

```

- ettől féltem :-(
- az említett forrás ezt sokkal tovább viszi, elmélet, és összegyűjtött adatokkal is vizsgálódik — szerintem nagyon érdekes
- a lényeg a Poisson—folyamat
- de a valóság — hál'istennek — ennél kedvezőbb, legalábbis Seeattle—ben, de szerintem Budapesten is
- a Poisson—folyamatnak nincs memóriája, de egy busz tud jobban sietni, ha késik — esetleg mentesítő járatot is be lehet iktatni

---

## Köszönöm a figyelmet!
