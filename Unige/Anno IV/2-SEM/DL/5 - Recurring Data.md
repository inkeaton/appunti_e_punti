+ We now start considering particular types of network specialized to work with **recurrent data**, sequences of elements
	+ An important thing to consider specifically about **text**, is that the network cannot directly process text data, it needs to **convert** it to a numerical descriptor called **embedding**. The embedding itself must be meaningful, putting similar words near to each other
+ The problem to be dealt with can be formulated differently depending on the input and output of the network
	+ **One**-to-Many
	+ **Many**-to-**One**
	+ Many-to-**Many**
	+ **Delayed**-Many-to-Many
+ We have two families of models, classified on how they approach the generation of the prediction:
	+ **Auto-regressive models** compute directly based on input information
	+ **Hidden State models** use an intermediate layer to compute the prediction
+ **Problems** of dealing with sequences are:
	+ Handling sequences of **different lengths**
	+ Taking into account **short and long term dependences**
	+ Considering **order** between elements
	+ Considering **time**, which adds another dimension of complexity
### Recurrent Neural Networks
+ An **hybrid** between the two approaches
+ It adds the concept of **memory** to the NN: each hidden layer will receive in input both the input and the output of the **previous neuron**
+ The current neuron will be the current **hidden state**
	+ The first hidden state will be initialized randomly
+ The **weight matrices** are filters that determine how much importance to give to both the present input and the past hidden state
	+ Weights are **shared** between neurons, thing which will be **annoying** in the future
+ When looking at the back propagation, we could notice that a section of the gradient is composed of successive multiplication
+ This could result in **vanishing** or **exploding** gradients, which could increase training times
+ While the **latter** can be solved by **clipping**, there is **no** direct solution for the **vanishing** gradient
+ This causes us to **lose** track of **long-term** dependencies
+ We need to change architecture
### Long-Short Term Memory 
+ To fix this, we need to evolve our structure
+ We want a state which gets updated time-instant after time-instant. As such, we **add** a **cell state** along with the already present hidden state
	+ We can see the **hidden** state related to **short** term, and the **cell** state as related to **long** term
+ Each cell of the network gets reworked into a **gated** cell, structured in order to control the flow of information
+ The computation is divided in four **steps**:
	1. **Forget**: The network decides what past information can be discarded from the cell state, based on the current input and hidden state
	2. **Store Input**: Value how much the new information is worth remembering and see how much we must update
	3. **Update Cell State**: We store in the cell state the new information computed in the previous step
	4. **Output Hidden State**: We modify the hidden state, using the **cell** state as a sort of **weights** for the update
+ This model was **state-of-the-art**... **until 2017**!
### Transformers
+ Now, that's more like it!
+ **Originally** proposed for **language translation**, transformers are **now** used **everywhere** for very different tasks. They are **parallelizable**, and as such quite efficient
	+ The T in Chat-GPT stands for Transformer
+ As other models for **sequence transduction**, they are based on an **encoder-decoder** structure
+ A first important step is the **embedding** of the data.
	+ Starting from the tokens, it is first computed a conventional embedding of them, and then an encoding based on the position of the word (**Positional Encoding**)
	+ The two embeddings are summed 
+ The network is then composed of two sections:
	+ **Encoder**: The encoder's role is to create an embedding of the input data. Its output will be reversed into the decoder. It is composed of two sections:
		+ A **Multi-Head Self-Attention** layer, which computes the importance of each word to one (*more on this later*)
		+ A conventional **Feed-Forward Net**, which produces the final embeddings
	+ **Decoder**: The decoder's role is to produce an equivalent representation of the outputs and compare them with the inputs. It is composed of three sections:
		+ A **Masked Multi-Head Self-Attention** layer
		+ A **Encoder-Decoder-Attention** layer
		+ A conventional **Feed-Forward Net**, with in the end a **soft-max** activation function, in order to output a list of probabilities of matches
+ Some of the layers implement **Residual Connections** (Skip Connection), connections between the input of the layer and the activation function
	+ This helps **optimization**. It's like we were enlarging the information space
+ Now let's focus on **self-attention**: What the hell is it?
	+ Self-attention allows a neural network to understand a word in the **context** of the words around it.
	+ We need to understand the **words** around it and their **relationships**
+ The process is as follows:
	+ We encode each word (text) into a numerical embedding of size N
	+ We pass the T words embeddings through a **linear** layer, obtaining the values, each one of size D
		+ This result is called **Value**, the relevant content of a token. 
		+ Since the layer is **linear**, we can describe its action as a **matrix** of weights $W_V$
	+ We create a matrix of **Attention Weights** $W$, which works kinda like a covariance matrix of **relevance**
	+ We want to learn $W$. We can split it in two other matrix:
		+ The **Queries** matrix, with their weights $W_Q$
		+ The **Keys** matrix, with its weights $W_K$ 
	+ By multiplying $Q$ and $K$ we obtain the **Scores** $S$
	+ **Scaling** $S$ by the size of the data, and applying **softmax**, we'll obtain the matrix $W$
		+ Softmax will modify non-linearly the space, such that higher scores get heighten and lower scores are depressed
	+ The product of $W$ and $V$ is called **Single-Head Self-Attention**$$\text{attention = }\text{softmax}\left(\cfrac{QK^T}{\sqrt{D}}\right) V$$
+ This result can be **over-fit**. As such, we'll apply a simple trick to improve the performance
+ The procedure is applied multiple times on the data (In parallel), and the different results are in the end united with some operation (sum, avg, concatenation, etc). This is **Multi-Head Attention**
+ After this, the data is **added** with the **residual connections**, and **normalized**
+ The analogous layers in the decoder works similarly, but with two main differences:
	+ The first layer is a **Masked Multi-Head Attention Layer**. Since we do not have the future words, we use a mask of weights to suppress the irrelevant values of the scores $S$
		+  To do this we should be able to know the size of input and output. We cannot know that in advance, so we'll just set a **maximum size**
	+ The second layer is a normal multi-head, which uses data **both** from the **decoder** and **encoder**: $$\text{output = }\text{softmax}\left(\cfrac{Q_{\text{DEC}}K_{\text{ENC}}^T}{\sqrt{D}}\right) V_{\text{ENC}}$$
+ Both the encoder and decoder can be reused in different structures:
	+ The **encoder** can be used as a **representation learning section** of a classifier
	+ The **decoder** can be used to **generate data** by predicting the next outputs
+ Also, **analogous** approaches have been presented for **images** (ViT) and **video** (ViVit), where **patches** of the image are used **as tokens**
+ Compared to **CNNs**, the reasoning is done more **globally**, and the possibility of **parallelization** is quite good