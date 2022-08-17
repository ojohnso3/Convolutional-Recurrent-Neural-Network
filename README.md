# NeuroVision: A Convolutional Recurrent Neural Network

### Summary
I built a Convolutional Recurrent Neural Network (CRNN) model that aimed to mimic neural activity in the primary visual cortex. I applied unsupervised learning techniques and used the Moving MNIST dataset as inputs to both reconstruct the original image and predict future video frames.

### Components
A Variational Autoencoder (VAE) with a Recurrent Neural Network (RNN) in the latent space. 

(1) The VAE is composed of the encoder model, latent space, decoder model, and loss function. The encoder condenses the image pixels into the smaller latent space, which is then expanded back by the decoder into a reconstruction of the original image. The loss function is a negative log likelihood with a regularizer, which prevents the encoder from cheating. There is also a reconstruction loss that encourages the decoder to actually learn how to reconstruct the data. 

(2) The latent space RNN consists of multiple consecutive Long Short-Term Memory (LSTM) cells. The LSTMs serve to prevent a vanishing gradient, as it stores an internal memory state which is simply added to the processed input.

I trained the model using gradient descent to optimize loss with respect to parameters of the encoder / decoder.

### Optimizations
First, I incorporated a present reconstruction via a second decoder and loss variable, Then, I added a predictive prior distribution that is trained through a second RNN and contributes to the loss function with a KL Divergence term. I combined these two optimizations into a third model, which is the version included in this repository.
