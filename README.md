systemy
=======

1. Podaj przykład skryptu wykorzystującego zmienne i zmienne środowiska np. USER, PWD, HOME.
``` sh
``` sh 
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
```
Przed uruchomieniem programu nadac prawa do pliku chmod 700!
uruchomic: ./zad1.sh
=======
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

=======
