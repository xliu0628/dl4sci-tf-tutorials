# Notes

## 1. How to improve the accuracy
  - change (usually) increase the number of hidden layers or # of neutrons in the hidden layer
  - change loss function

## 2. Overfitting and Underfitting 
- If you train for too long though, the model will start to overfit and learn patterns from the training data that don't generalize to the test data. 
- Prevent overfitting: more data; if not, regularization. 
- The more capacity the network has, the quicker it will be able to model the training data (resulting in a low training loss), but the more susceptible it is to overfitting (resulting in a large difference between the training and validation loss).
- two common regularization techniques: weight regularization, dropout
### - how weight regularization works
    - idea: put a constraint on the complexity of the model by adding to the loss function of the network a cost associated with having large weights. 
    - two types: L1 regularization and L2 regularization (also called "weight decay", more common). 
### - how dropout works: 
    - randomly dropping some output of the layer (i.e. set to zero) during training; but in test time, the fraction of dropping rate is used rather than some output features are actually dropped. 
    
