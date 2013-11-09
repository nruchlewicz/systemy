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

2. Podaj przykład skryptu korzystującego ze zmiennych specjalnych, czyli użyj $0, $1, $2, …, $9, $@, $*, $?, $$.
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
owoc[0]="jablko"
owoc[1]="gruszka"
owoc[2]="sliwka"
owoc[3]="wisnia"
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
