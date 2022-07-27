# mini_keras
This project creates a framework similar to keras written purely using numpy. The design of the framework is done while keeping extensibility at highest priority.

Going into a bit more detail:
* The layer interface is at the heart of all necessary computation to convert an input to an output
* Subclasses like nn_layer (standard neural network layer), sigmoid, relu extend the layer class
* Some salient points about the layer interface:
  * It has 2 main attributes: params, grads
  * The subclasses are expected use values stored at params to convert an input to an output
  * The grads are expected to store the gradient of params
  * Layer objects are callable. It converts the input to an output
  * Layer also has grad_out function which is expected to compute the gradient of input given input and gradient of output 

* The optimizer interface provides a uniform interface whose objects are callable. It takes in cur_grad of a variable as input and returns a grad which is used for updating the variable
* The subclasses are SGD, Adam and RMS_Prop
