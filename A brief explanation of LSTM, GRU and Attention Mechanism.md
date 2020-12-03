# A brief explanation of LSTM, GRU and Attention Mechanism



To Deal with Sequential problem we need algorithm that can deal with sequence vectors. RNN or recurrent neural networks were the algorithm which were given as an answer to this question. The RNN or recurrent neural network were networks which were passed a new input and the previously predicted output  to predict the next output . Although RNN performed really well in task involved with sequential data they were still not able to perform good in problem were the length of sequential data is long as it had no concept of saving the $$n-$$ $$k^t$$$$^h$$ memory . That is where LSTM comes as an answer with the concept of cell state which act like a memory.



## LSTM - Long Short Term Memory 

LSTM or Long short term memory has it building block in RNN but they are capable of retrieving the context of sequential data due to cell state. 

![image-20201203171307440](C:\Users\yamini.rawat\AppData\Roaming\Typora\typora-user-images\image-20201203171307440.png)



Cell state or the $$C$$$$_{t}$$ associates it self with the whole LSTM architecture. The neural nets inside the architecture decide if something is to be forgotten or added to the cell state. The cell state intern help in deciding the output  according to the context saved in it.



1. **Forget gate:** The first part of LSTM is a forget gate . The input $$h_{t-1}$$ and $$x$$ are given to neural net which decide if anything from the cell has to forgotten. It is passed through a sigmoid activation function. The output of the sigmoid then gets multiplied with the cell state $$C_{t-1} $$.
2. **Addition gate:** Next part is to add things to cell state . Here first we decide what value to update given by $$i_{t}$$. then we  get $$\tilde{C}_t $$ which the state that has to added from a neural network followed by a tanh squashing function. The multiplication of both these units are addded to cell state.

3. **Output gate:**  The output gate decides finally what will be the output of the LSTM. Here a neural net output after passing through sigmoid gate activation is multiplied with the output of the cell state given to tanh function. This way an output considering the cell state is determined. 



## GRU- Gated Recurrent Unit 

After the LSTM a number of algorithm based on LSTM came out . One of them was GRU which is quite popular as it combined the forget and addition gate to one update gate. It also updated the memory twice once with Reset gate and then with the hidden state . It results in a simpler model than LSTM.

![image-20201203175118070](C:\Users\yamini.rawat\AppData\Roaming\Typora\typora-user-images\image-20201203175118070.png)



## **Attention Mechanism**

Encoder decoder was mainly used for neural machine translation where it was used for translating one language to other.  Attention mechanism is an extension of encoder decoder.

In attention we use mainly three units an encoder , a decoder and attention mechanism.

In attention we will have input vector which coupled with feedback $$s$$ will passed through neural network will give $$\alpha$$ which when multiplied with inputs vector will give us the context we have to give attention to and will be given to output to predict final output.

Below diagram show attention mechanism.

![image-20201203230207814](C:\Users\yamini.rawat\AppData\Roaming\Typora\typora-user-images\image-20201203230207814.png)

In this let us assume we have input $$x_{1}$$ , $$x_{2}$$ , $$x_{3}$$ , $$x_{4}$$ which when given to encoder gives  $$h_{1}$$, $$h_{2}$$  $$h_{3}$$, $$h_{4}$$ .

 $$h_{1}$$, $$h_{2}$$,$$h_{3}$$, $$h_{4}$$ along with $$s_{0}$$ are given to a fully- connected layer , then to a softmax to give  $$\alpha_{1}$$, $$\alpha_{2}$$,$$\alpha_{3}$$, $$\alpha_{4}$$ .

$$\alpha$$ is are know as attention weights and used to calculated the context vector.

Now the  $$\alpha_{1}$$, $$\alpha_{2}$$,$$\alpha_{3}$$, $$\alpha_{4}$$ are multiplied with $$h_{1}$$, $$h_{2}$$,$$h_{3}$$, $$h_{4}$$ to give $$c_{1}$$ . $$c_{1}$$ is the context . Next the context along with $$s_{0}$$ is given to decoder and a $$s_{1}$$ or $$y_{1}$$ is predicted . $$s_{1}$$ is feedback to get concatenated with  $$h_{1}$$, $$h_{2}$$  $$h_{3}$$, $$h_{4}$$  and so forth we make next predictions.

 

## Conclusion

Although attentions mechanism gives good results and are building block of latest outperforming algorithms and techniques like transformers we have to consider the computation cost involved in running these algorithms. Regardless the results shown by these algorithms are incredible.

## References 

[Christopher Olah's github blog](https://colah.github.io/posts/2015-08-Understanding-LSTM)

[Rohan Shravan's END program](https://canvas.instructure.com/courses/2393516/assignments/18930563)

