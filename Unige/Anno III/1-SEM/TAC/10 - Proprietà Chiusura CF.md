+ Vediamo le proprietà di chiusura dei linguaggi Context Free:
	+ $L_1 \cup L_2 \quad \to \quad$ Context Free
	+ $L_1 \cdot L_2 \quad \to \quad$ Context Free
	+ $L^* \quad \to \quad$ Context Free
	+ $\bar{L} \quad \to \quad$ NON Context Free
	+ $L_1 \cap L_2 \quad \to \quad$ NON Context Free
		+ *dimostrazioni e altro nei fogli, 3/11/23*
---
+ Esistono degli algoritmi per ottenere automaticamente degli automi PDA da una grammatica context-free, una volta che questa è stata riscritta in forma normale di Greibach
+ Purtroppo essi sono in tempi cubici ($O(n^3)$)
+ Fortunatamente, nella pratica, i compilatori utilizzano algoritmi maggiormente efficienti, tramite l'utilizzo di assunzioni aggiuntive