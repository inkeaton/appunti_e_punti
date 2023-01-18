* Proviamo a tradurre il seguente programma scritto in C in istruzioni per il processore Amber 2

```c
// Algoritmo Euclideo
int main() {
	int a = 10;
	int b = 16;
	int gcd;
	do{
		if(a>b)
			a-=b;
		else b-=a;
	} while(a!=b);
	gcd = a;
}
```
* Questo programma calcola l'MCD fra 10 e 16, ovvero 2
* Prima di tutto salveremo 10 e 16 nei registri R0 ed R1, tramite due istruzioni MOV
	* MOV   1110 00 1 1101 0 0000 0000 0000 00001010
	* MOV   1110 00 1 1101 0 0000 0001 0000 00001010
* Dopo di che controlleremo se a > b facendo a - b e salvando nel registro di stato il valore della sottrazione
	* CMP   1110 00 0 1010 1 0000 0000 00000000 0001
* Adesso, se il risultato era positivo faremo a-b, se no faremo b-a. Per controllare useremo le condizioni 1100 e 1011
	* SUB   1100 00 0 0010 0 0000 0000 00000000 0001
	* SUB   1011 00 0 0010 0 0000 0001 00000000 0000
* Ora, se a != b, dobbiamo ritornare all'istruzione 3. Per farlo urilizziamo un istruzione BRANCH, che tornerà a 3 + 2 (ricorda la pipeline!) istruzioni indietro, ovvero 20 byte
	* B        0001  101 0 00000000000000000010100
* Infine, una volta usciti dal "loop", salveremo il risultato in R2, copiandolo da R0
	* MOV   1110 00 1 1101 1 0000 0010 00000000 0000
* In questo modo abbiamo codificato un programma c di 11 istruzioni in sole 8! Nonostante i possibili rallentamenti dovuti allo svuotamento della pipeline si deve riconoscere che questa architettura è ideale per programmi che contengono numerose istruzioni condizionali, basta che i frammenti dentro alle condizioni non siano ne troppo lunghi, ne troppo corti
* Naturalmente codificare in questo modo  è complicato e facilmente confondente, per questo motivo vengono implementati piccoli linguaggi assemblatori, i quali vengono poi tradotti dall'assembler