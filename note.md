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


## 3. Save and restore models
- save checkpoints during training is useful in that it allows you to use a trained model without having to retrain it, or to pick-up training where it was interrupted. 
###  
    checkpoint_path = "training_1/cp.ckpt"
    checkpoint_dir = os.path.dirname(checkpoint_path)
    # Create checkpoint callback
    cp_callback = tf.keras.callbacks.ModelCheckpoint(checkpoint_path,
                                                 save_weights_only=True,
                                                 verbose=1)

    model = create_model()

    model.fit(train_images, train_labels,  epochs = 10,
          validation_data = (test_images,test_labels),
          callbacks = [cp_callback])  # pass callback to training
- build a fresh, untrained model
  > model = create_model()
  > loss, acc = model.evaluate(test_images, test_labels)
- load weight from a saved checkpoint
  > model.load_weights(checkpoint_path)
- save the entire model (in HDF5 format)
  > model.save('my_model.h5')
- load the saved model
  > new_model = keras.models.load_model('my_model.h5')
  > new_model.summary()
