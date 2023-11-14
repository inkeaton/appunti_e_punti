![[Esercizi 6-10.png]]

1. $[A-Z]^2 \cdot [0-9]^3 \cdot [A-Z]^2$  
2. $0 \cdot [x X] \cdot [0-9 A-Fa-f]^+$
3. $(0 | [1-9]  [0-9]^*) [lL]?$ 
4. $[0-9]^* \backslash . [0-9]^+ | [0-9]^+ \backslash . [0-9]^*$
5.  $"([^{\wedge} " \backslash \backslash]| \backslash \backslash [" \backslash \backslash])^*"$


* \\d sta per $[0-9]$ 
* $[A-Z]^2$ si può scrivere come $[A-Z]\{2\}$  
* $[AB]| \epsilon$ può essere scritto come $[AB]?$ 