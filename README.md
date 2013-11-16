systemy
=======

1. Podaj przykład skryptu wykorzystującego zmienne i zmienne środowiska np. USER, PWD, HOME.

```sh
#!/bin/bash
echo "Czesc $USER"
echo "twoj aktualny katalog to $PWD"
zmienna="a to twoj katalog domowy to $HOME"
echo $zmienna
echo "nazwa twojego hosta to: $HOSTNAME"
echo "korzystasz z systemu operacyjnego: $OSTYPE"
zmienna2=$(pwd)
echo "\"Ciapki\" – przyklad: $zmienna2"
exit 0
```


Przed uruchomieniem programu nadac prawa do pliku chmod 700!
uruchomic: ./zad1.sh

2. przykład skryptu korzystującego ze zmiennych specjalnych, czyli użyj $0, $1, $2, …, $9, $@, $*, $?, $$.
```sh
#!/bin/bash
echo "Nazwa biezacego skryptu: $0"
echo "Pierwszy przekazany parametr do skryptu: $1"
echo "Drugi przekazany parametr do skryptu: $2"
echo "..."
echo "Dziewiaty przekazany parametr do skryptu: $9"
# separatorem będzie spacja
echo "Skrypt uruchomiono z parametrami: $@"
# separator okresla zmienna $IFS
echo "Skrypt uruchomiono z parametrami: $*"
echo "Kod powrotu ostanio wykonywanego polecenia: $?"
echo "PID procesu biezacej powloki: $$"
exit 0
```
Przed uruchomieniem programu nadac prawa do pliku chmod 700!
uruchomic: ./zad2.sh 

3. Podać przykład skryptu korzystającego z tablic (Użyj declare, unset, *, @, # ).
```sh
owoc[0]="jablko"  //deklaracja pierwszego elem. tablicy
owoc[1]="gruszka" //--||-- drugiego --||-- 
owoc[2]="sliwka"  //--||-- trzeciego..
owoc[3]="wisnia"  //--||-- czwartego..
echo "Pierwszy element tablicy owoc to: ${owoc[0]}"
echo "Wszystkie elementy tablicy owoc to: ${owoc[*]}"
echo "Wszystkie elementy tablicy owoc to: ${owoc[@]}"
echo "Drugi element tablicy owoc ma ${#owoc[1]} znakow"
echo "Tablica owoc ma ${#owoc[*]} elementy"
imie=(Jola Ania Kasia Basia Magda)
echo "Wszystkie elementy tablicy imie to: ${imie[@]}"
unset imie  # usuniecie tablicy
echo "Tablica imie ma ${#imie[*]} elementow"
tab1=(`cat /etc/passwd`)
echo "Tablica tab1 ma ${#tab1[*]} elementow"
declare tab2=(`cat /etc/passwd`)
echo "Tablica tab2 ma ${#tab2[*]} elementow"
exit 0
```

4. Napisać skrypt obliczający sumę, różnicę i iloczyn dwóch wczytanych liczb całkowitych. (Użyj polecenia read.)
```sh
#!/bin/bash
echo -n "Podaj pierwsza liczbe: "
read liczba1
echo -n "Podaj druga liczbe: "
read liczba2
echo
suma=$[liczba1 + liczba2] #1 sposob
echo "Suma liczb wynosi: $suma"
roznica=$((liczba1-liczba2)) #2 sposob
echo "Roznica liczb wynosi: $roznica"
let iloczyn=liczba1*liczba2 #3 sposob
echo "Iloczyn liczb wynosi: $iloczyn"
iloraz=$[liczba1/liczba2]
echo "Iloraz liczb wynosi: $iloraz" #czesc calkowita
modulo=$[liczba1%liczba2]
echo "Modulo liczb wynosi: $modulo" #reszta
exit 0
```

5. Napisać skrypt sprawdzający, czy w katalogu głównym użytkownika istnieje plik .bashrc. (Użyj instrukcji warunkowej if.)
```sh
if [ -e ~/.bashrc ]
# lub rownowaznie: if test -e ~/.bashrc
then echo "Masz plik .bashrc"
else echo "Nie masz pliku .bashrc"
fi
exit 0
```
#LAB5

skrypt pobierający z wiersza poleceń 2 argumenty będące bokami prostokąta i obliczający jego pole. 
```sh
#!/bin/bash

pole=$[$1 * $2]
echo "Pole prostokata wynosi: $pole"
exit 0
```

skrypt obliczający a do potęgi n, a - liczba naturalna (bez zera), n - liczba naturalna (z zerem). Funkcja ma posiadać dwa argumenty a i n.
Przetestuj działanie tej funkcji.
```sh
#!/bin/bash
funkcja_potega()
{
echo "liczba a=: $1"
echo "do potegi: $2"
i=1
potega=1
while [ "$i" -le $2 ]
do
potega=$(($potega*$1))
i=$[i + 1]
done
echo "wynosi: $potega" 
}

funkcja_potega "$1" "$2"
exit 0
```

Srypt wczytujący 5 imion (użyj tablic), sortujący imiona w kolejności alfabetycznej (tak jak w książce telefonicznej) i wypisujący posortowane imiona na ekranie. 
```sh 
#!/bin/bash
imie[0]=$1
imie[1]=$2
imie[2]=$3
imie[3]=$4
imie[4]=$5
echo "${imie[*]}"
eval R=($(printf "%s\n" "${imie[@]}" | sort $u))
echo "${R[@]}"
exit 0
```

skrypt sprawdzający, czy istnieje podany jako parametr plik i wypisujący odpowiedni komunikat na ekranie. 
```sh
#!/bin/bash
if [ -e $1 ]
then echo "Masz plik $1"
else echo "Nie masz pliku $1"
fi
exit 0
```

skrypt, który wypisze na ekran zawartość pliku solar.txt
```sh
#!/bin/bash
cat solar.txt
exit 0
```

skrypt, który wypisze na ekran zawartość pliku podanego jago parametr.
```sh
#!/bin/bash
cat $1
exit 0
```
skrypt, który wypisze na ekran zawartość pliku podanego jago parametr, jeśli nie mam takiego pliku zostanie wyświetlony odpowiedni komunikat.
```sh
#!/bin/bash
if [ -e $1 ]
then cat $1
else echo "Nie masz pliku $1"
fi
exit 0
```

skrypt, który pobierze nazwę dwóch plików i dopisze zawartość pierwszego do drugiego.
```sh
#!/bin/bash
cat $1 > $2
exit 0
```


