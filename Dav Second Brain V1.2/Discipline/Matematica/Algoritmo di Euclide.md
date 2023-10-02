#uni #dimostrazione 27/09/2023
## Cosa è
Procedimento algebrico che permette di calcolare il [[Massimo Comune Divisore]] tra due numeri $a$ e $b$interi attraverso un numero finito di passi basati sul calcolo di alcune divisioni.

---
## Come funziona
Poniamo:
$a>=b$
$a=b*r +q$
Quindi $b<r<a$ 
Siccome  $McD(a,\ b)=McD(b,\ r)$ ([[Algoritmo di Euclide#Dimostrazione McD]]) ci conviene calcolare $McD(b,\ r)$ , poiché $b$ e $r$ sono entrambi minori di $a$ e quindi i calcoli sono più facili.
Svolgo $\frac{a}{b}$ , se $r=0$ mi fermo poiché $McD=b$ , altrimenti continuo con:
$\frac{b}{r}$, se $r_1=0$ mi fermo poiché $McD=r$, altrimenti continuo con:
$\frac{r}{r_1}$, se $r_2=0$ mi fermo...
	e via via finché non trovo un resto uguale a zero, l'McD è uguale all'ultimo denominatore usato.

---
## Dimostrazione McD
Dimostrazione che $$McD(a,\ b)=McD(b,\ r)$$Creo due [[Insiemi]]: 
$A=\{n\ tale\ che\ n|a\ e\ n|b \}$ `insieme dei divisori di a e b`
$B=\{n\ tale\ che\ n|b\ e\ n|r \}$ `insieme dei divisori di b e r`
Per dimostrare che gli McD dei due insiemi sono uguali devo dimostrare che gli insiemi stessi sono uguali, quindi devo dimostrare che:
	1 $A \subseteq B$
	2 $B \subseteq A$ 
:
### 1
Se $n|a$ allora $a/n = a_1$ e $a=n*a_1$
Se $n|b$ allora $b/n = b_1$ e $b=n*b_1$
Sostituisco nell'equazione generica che mette in relazione $a$ con $b$:
$a = b*q +r$
$n*a_1 = m *b_1*q+r$
$r=n*a_1 - n*b_1*q$
$r= n*(a_1-b_1*q)$
Segue che $n|r$.
Di conseguenza i valori $n$ di $A$ dividono anche $b$ e $r$, di conseguenza appartengono anche a $B$.
### 2
Se $n|b$ allora $b/n = b_1$ e $b=n*b_1$
Se $n|r$ allora $r/n = r_1$ e $r=n*r_1$
Sostituisco nell'equazione generica che mette in relazione $a$ con $b$:
$a = b*q +r$
$a=n*b_1*q+n*r_1$
$a=n*(b_1*q+r_1)$
Segue che $n|a$.
Di conseguenza i valori $n$ di $B$ dividono anche $a$ e $r$, di conseguenza appartengono anche a $A$.

Segue che A è  contenuto di B e B è contenuto di A quindi $A=B$, allora: $$McD(a,\ b)=McD(b,\ r)$$C.V.D.

## Programma
Questo programma commentato svolge questo procedimento, in C++:
```
#include <iostream>
using namespace std;

int main() {

    int n1;
    int n2;
    int q;
    int r;
    int mcd;

    start: // this is a label

    number1: //questa è una label, con goto il programma ritorna a quest ariga
    cout << "Insert first number" <<endl;
    cin >> n1;
    if (n1<=0) {
        cout<<"number must be positive"<< endl; //non accetta numeri negativi
        goto number1;} //questo va alla riga number1

    number2:
    cout<< "insert second number (must be smaller than first)" << endl;
    cin >> n2;
    if (n2<=0) {
        cout<<"number must be positive"<< endl; //numeri positiviiiii
        goto number2;}
    else if (n2>n1) {
     cout<< "Second number must be smaller than first! "<< endl;
     goto start;
    }

    mcd:

    q = n1/n2; // q è la divisione
    r = n1%n2; // r è il resto
    if (r==0) {
        mcd = n2;
        cout << "the McD is " << mcd << " !" << endl;
        return 0;
    }
    else {
        n1 = n2;
        n2 = r;
        goto mcd;
    }

}
```