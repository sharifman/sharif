# Dokument�ci�
# Neptun    
Naddaf Sharif Alexander     
GU5I9D  
#1.K�vetelm�nyanal�zis  
##1.1. C�lkituz�s, projektind�t� dokumentum     
Olyan weboldal k�sz�t�se, ahol a tanul�k t�rgyakat vehetnek fel �s a tan�r �j t�rgyakat �rhatnak ki.       

######Funkcion�lis k�vetelm�nyek:  
* Bejelentkez�s
* Csak bejelentkezett felhaszn�l�k �ltal el�rheto funkci�k:      
    - Tan�rok sz�m�ra:    
    -- Saj�t t�rgy l�rehoz�sa   
    -- Saj�t t�rgy t�rl�se  
    -- Saj�t t�rgy szerkeszt�se        
    - Di�kok sz�m�ra:    
    -- T�rgy felv�tele  
    -- T�rgy lead�sa     
    - Admin sz�m�ra     
    -- Tan�r felhaszn�l� l�trehoz�sa/t�rl�se    
    -- Di�k felhaszn�l� l�trehoz�sa/t�rl�se     
    -- Terem l�trehoz�sa/t�rl�se        

######Nem funkcion�lis k�vetelm�nyek:
*	**K�nnyu �ttekinthetos�g:** Sz�nekkel t�pus szerint csoportos�t�s
*	**Haszn�lhat�s�g:** K�nnyu �ttekinthetos�g, �sszeru elrendez�s, k�nnyen kezelhetos�g
*	**Megb�zhat�s�g:** jelsz�val v�dett funkci�k, �s a jelszavak v�delme a h�tt�rben. Hib�san bevitt adatok eset�n a program j�l l�that�an jelezzen a felhaszn�l�nak, �s emelje ki a hib�s beviteli mezoket. A j�l bevitt adatok maradjanak az urlapban.
*	**Karbantarthat�s�g:** k�nnyen lehessen bov�teni, a k�l�nb�zo t�pus� f�jlok k�l�n csoportos�tva, �sszeruen legyenek felbontva, a k�nnyebb fejleszthetos�g miatt


##1.2.	Haszn�latieset-modell, funkcion�lis k�vetelm�nyek

**Vend�g**: Csak a publikus oldalakat �ri el
*	Fooldal
*	Bejelentkez�s

**Bejelentkezett Tan�r**:       
*	�j T�rgy l�trehoz�sa
*	Saj�t T�rgy t�rl�se/szerkeszt�se       

**Bejelentkezett Tanul�**:     
*	T�rgy felv�tele
*	Felvett t�rgy lead�sa  

**Bejelentkezett Admin**:  
*	Tan�r/Tanul� felhaszn�l� l�trehoz�sa
*	Megl�vo Tan�r/Tanul� t�rl�se/szerkeszt�se
*	Terem l�trehoz�sa
*	Megl�vo terem t�rl�se/szerkeszt�se

![](1.png)

**Megl�vo recept szerkeszt�se:**

1.	A felhaszn�l� az oldalra �rkezve, bejelentkezik Tanul�k�nt
2.	Bejelentkez�s ut�n list�zhatja a T�rgyakat.
3.	Kiv�laszt egy T�rgyat
4.	Az adott t�rgyn�l r�nyom a felv�tel gombra

![](2.png)

#2.	Tervez�s

##2.1.	Architekt�ra terv

####2.1.1. Oldalt�rk�p

**Publikus:**
* Fooldal
* Bejelentkez�s

**Bejelentkezett:**
* Fooldal(Tan�r,Tanul�,Admin)
* T�rgyak list�z�sa(Tanul�,Admin)
   * T�rgy Kiv�laszt�sa(Tanul�,Admin)
        * T�rgy Felv�tele/Lead�sa(Tanul�)
        * T�rgy T�rl�se/Szerkeszt�se(Admin)
* Saj�t T�rgyak list�z�sa(Tanul�,Tan�r)
    * T�rgy kiv�laszt�sa(Tanul�,Tan�r)
        * T�rgy l�trehoz�sa/t�rl�se/szerkeszt�se(Tan�r)
        * T�rgy felv�lte/lead�sa(Tanul�)
* Tanul�k/Tan�rok List�z�sa(Admin)
  * Felhaszn�l� kiv�laszt�sa
    * Felhaszn�l� Szerkeszt�se/T�rl�se
  * Felhaszn�l� l�trehoz�sa 
 
######2.1.3. V�gpontok


* GET/: fooldal


* GET/login: bejelentkezo oldal
* POST/login: bejelentkezo adatok felk�ld�se
* GET/logout: kijelentkezo oldal


* GET/targy/lista: t�rgylista oldal
* GET/targy/uj: �j t�rgy l�trehozasa
* POST/targy/uj: �j t�rgy felv�tel�hez sz�ks�ges adatok felk�ld�se
* GET/targy/azon: targy adatok
* GET/targy/torles=azon: t�rgy t�rl�se
* GET/targy/szerk=azon: t�rgy m�dos�t�sa
* POST/targy/szerk=azon: t�rgy m�dos�t�sa, adatok felk�ld�se


* GET/felh/lista: felhaszn�l�lista oldal
* GET/felh/uj: �j felhaszn�l� l�trehoz�sa
* POST/felh/uj: �j felhaszn�l� l�trehoz�s�hoz sz�ks�ges adatok felk�ld�se
* GET/felh/azon: felhaszn�l� adatok
* GET/felh/torles=azon: felhaszn�l� t�rl�se
* GET/felh/szerk=azon: felhaszn�l� m�dos�t�sa
* POST/felh/szerk=azon: felhaszn�l� m�dos�t�sa, adatok felk�ld�se


* GET/terem/lista: teremlista oldal
* GET/terem/uj: �j terem l�trehoz�sa
* POST/terem/uj: �j terem l�trehoz�s�hoz sz�ks�ges adatok felk�ld�se
* GET/terem/azon: terem adatok
* GET/terem/torles=azon: terem t�rl�se
* GET/terem/szerk=azon: terem m�dos�t�sa
* POST/terem/szerk=azon: terem m�dos�t�sa, adatok felk�ld�se

#####2.2. Felhaszn�l�i-fel�let modell

######2.2.1.Oldalv�zlatok:

**Fooldal**

![](Fooldal.jpg )

**t�rgyak oldal**

![](targyak.jpg )

**Bejelentkezo oldal**

![](bejelentkezes.jpg )

**T�rgy oldal**

![](targy.jpg )

 **Adatmodell �s Adatb�zisterv**
 
 ![](6.png)
 

