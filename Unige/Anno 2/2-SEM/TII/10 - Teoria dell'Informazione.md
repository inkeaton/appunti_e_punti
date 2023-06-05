* Dato un certo evento E con probabilità di accadere P, definiamo l'**informazione di Shannon** come:
	* $S(p) = \log_2 (\frac{1}{p})$ 
* Da questa definizione intuiamo che:
	* È sempre **positiva**
	* È se la **probabilità** di un evento è **minore**, la sua **informazione** è **maggiore**
	* L'informazione ottenuta da due eventi indipendenti avvenuti è uguale alla somma della informazione singola dei due
* È in parte legata al numero di **bit** necessari per scriverla
* Abbiamo visto esempi nel caso della **battaglia navale** e del problema della **bilancia**
---
* L'**entropia di Shannon** rappresenta invece quanto il valore di una VA è **incerto**, e viene calcolata nel seguente modo:
	* $H[X] = \sum_i p_i S(p_i)$ 
* Corrisponde al **valore atteso** dell'**informazione**
* Essa è **massima** quando i casi sono **equiprobabili**