+ JSRay uses:
	+ A **runtime script inclusion monitor** mechanism to dynamically monitor the inclusion and execution of all JavaScript code on a page. 
		+ This mechanism can help track the **origin** of an included script and also construct the inclusion dependency among all the scripts. 
	+ a **runtime deletion monitoring** mechanism to detect all the dynamic script deletion operations. 
		+ It can further tag the scripts running in the JavaScript world to their corresponding containers in the page to accurately attribute the deletions.
	+ Also **dynamically monitors** JavaScript’s **access** **to sensitive browser APIs** for helping study the connection between the self-deleting scripts and any sus- picious behaviors
+ Self-deletion can also be used in client-side JavaScript: a script can delete its host HTML \<script\> element or any other host container (e.g., an HTML attribute) from the Document Object Model (DOM) tree. 
	+ Deleting the code container only detaches the script source from the DOM tree, and the deleted script still exists and runs in the JavaScript world
+ Since client-side JavaScript’s privilege is strictly restricted by modern browser security mechanisms, we consider mainly malicious scripts that access sensitive client-side data
+ We do not attempt to detect whether the self-deleting scripts are malicious JavaScript. Rather, we aim to understand the client-side JavaScript self-deletion technique and figure out whether the use of it is sus- picious
---
+ Main Problems:
	+ **Dynamic Code**: il codice generato dinamicamente è difficile da monitorare, specie se non incluso tramite link
	+ **Script Identification**: Il codice può essere incluso ed eliminato da una pagina in più modi. È necessario studiare ognuno di essi per comprendere la relazione fra script
	+ **Code Obfuscation**: Questi script possono avere codice offuscato per nasconderne il comportamento
--- 
+ **Tipi di cancellazione di script:**
	+ Cancellato da se stesso
	+ Cancellato da uno script padre
	+ Cancellato da uno script figlio
	+ Cancellato da un altro script non correlato
+ **Modalità di cancellazione script:**
	+ Cancellare l'elemento `<script>` che lo contiene dal DOM
		+ Tramite `Element.remove(), Element.replaceWith()` o rimuovendo l'elemento padre
	+ Rimuovendo o modificando l'attributo HTML che lo contiene (ad esempio `onload`)
		+ Esistono due tipi di attributi HTML capaci di contenere JS code:
			+ Inline Event Handlers: Eseguono il codice in seguito ad un evento ed all'invocazione dell'event handler
			+ URL Attributes: URL che contengono codice JS, che vengono eseguiti all'invocazione
		+ Questi eseguiti su eventi particolari non vengono considerati dall'articolo, ma solo quelli eseguiti `onload`
---
+ Our analysis reveals that JavaScript self-deletion is an anti- debugging technique that tries to prevent, or at least impede, any attempts at (manually) inspecting and debugging the JavaScript code on a website
+ Even though the current dynamic malware analysis tools are able to report the malicious activities observed on one website, the secu- rity analysts still need to manually locate the real culprits among a huge number of scripts because of the coarse-grained behavior attribution of the current tools.
+  Prior work [ 12 , 20, 33 , 35] describes the inclusion re- lationships of dynamic elements and analyzes the security problem in inclusion chains. However, their work focuses on the inclusion of first-party or third-party resources loaded on the page, i.e., re- sources have specific URLs and are included on the page. But it would also be necessary for tracking the origins of the scripts that do not have a source URL, including the dynamically included in- line scripts and the dynamically generated scripts via functions like eval().
---
+ JS viene **modificato** in modo che:
	+ Vengono **monitorate** le **API di creazione script**
		+ This can be done by hooking all the DOM APIs that can be used for creating new `<script>` elements, such as `document.createElement("script")` and `document.write("<script>...</script>")`, and checking the JavaScript call stack to find the parent script, as has been demonstrated by the prior work JSIsolate.
	+ il parser JS viene modificato in modo da **monitorare le chiamate alle funzioni di parsing**
		+ To identify the origin of a dynamically included inline script element, we set its parent script’s source URL (if available) as its origin, following the prior work
	+ Vengono **monitorati gli eventi JS per rilevare codice in attributi**
		+ To track the creation of inline event handlers, we monitor the calls of the browser’s internal event handler registration function. This function is called whenever a new event handler is being added in the browser. Similarly, we examine the JavaScript call stack to locate the parent script, if any. However, the event handlers will only be executed when the corresponding events are fired. Therefore, we also monitor the writes to the inline event handler attributes and record the source code for mapping the JavaScript objects to their DOM containers
		+ To support javascript: URL scripts, we also monitor all the writes to the relevant HTML attributes as JSIsolate. We identify the scripts that are setting the corresponding monitored attributes as the parent scripts. Since an attribute could be set by multiple scripts, we identify the parent script from the last write log.
---
+ We find that script deletion is common in the real world and most deleted scripts are self-deleting scripts. JSRay detected in total 5,089,340 script deletions on 369,525 websites, or 42.44% of the 870K reachable websites. These deletion operations are from 761,240 scripts, and 240,478 unique ones deduplicated by the hash value of the source code. Among the 5,089,340 deletion operations, 1,596,796 (31.38%) were self-deletion, which were found on 226,854 (61.39%) websites. The operations come from 311,402 scripts and 142,557 unique ones. We further categorize script deletion into the four classes defined in §3.1. Among all these deletions, 1,451,167 (28.51%) scripts were deleted by themselves; 142,697 (2.80%) scripts were deleted by ancestor scripts; 2,932 (0.06%) scripts were deleted by descendant scripts; and 3,492,544 (68.62%) scripts were deleted by other irrelevant scripts. 
+ By manually analyzing some of the samples, we find that the third-party deleting scripts were usually library functions that provided utilities for managing the DOM tree or the scripts. For example, jQuery provides a lot of li- brary functions for conveniently manipulating the DOM tree. Many of the deletions resulted from the calls of such utility functions by other scripts, which we did not identify as the deleting scripts. This also suggests that many of the fourth-class deletions could have actually been classified as self-deletions if we changed the way to identify the deleting scripts. However, we currently cannot man- ually confirm that all the 1,550,328 are like these. Additionally, it is challenging to distinguish whether third-party scripts actually delete some scripts or just provide functions for other scripts. We leave it as a future work to distinguish the legitimate library scripts from the real deleting scripts
---
+ the numbers of self-deleting script are positively correlated with the numbers of all included script on the websites.
+ In summary, our results show that self-deletion is quite com- mon on the web. Since it is also a very powerful client-side anti- analysis technique, we demonstrate the strong need of the dynamic JavaScript monitoring systems like JSRay for web security research and client-side JavaScript analysis.
---
+ Ragioni per cancellare:
	+ Hiding/Cleaning benign code
	+ Hiding suspicious activities
+ In summary, we find that most scripts deleted themselves for le- gitimate purposes like code cleaning, yet the self-deletion technique has also been used for hiding suspicious/malicious script behav- iors. This motivates us to further study the connection between self-deleting scripts and suspicious operations next
+ It indicates that self- deleting scripts are much more likely to be blocked by filter lists. In other words, they are more likely to be related to unwanted web content that many users would like to block.
+ In summary, we discover that the self-deleting scripts made more accesses to sensitive browser APIs on average than the normal scripts. They are also 5.6x more likely to be included in popular filter lists. Although not all the accesses are necessarily malicious, the uses of script deletion technique increase the difficulty in analyzing their operations. Our research makes an important first step in understanding their behaviors, and lays the necessary foundation for future research.
---
+ Sezioni dell'Articolo:
	1. Introduction
	2. Problem Statement
		1. Research Scope and Assumptions
		2. Research Challenges
	3. Script Deletion
		1. Classes of Script Deletion
		2. Script Deletion Tecniques
		3. Security Impact
	4. Detecting Script Deletion
		1. Overview
		2. Dynamic Script Inclusion Monitoring
		3. Javascript and DOM Mapping
		4. Script Deletion Monitoring
		5. Sensitive API Access Monitoring
		6. Implementation
	5. Measuring Script Deletion in the Wild
		1. Experimental Setup and Dataset
		2. Ethical Consideration
		3. Prevalence of Script Deletion
		4. Characterization of Self-Deletion
	6. Understanding Script Self-Deletion
		1. Deleted Contents and Deletion Reasons
		2. Self-Deletion and Suspiciuos Activities
	7. Related Work
	8. Conclusion
	9. Appendice
		1. Security impact analysis
		2. Case study