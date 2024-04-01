Optimization is much more difficult as the search space is discrete (i.e. cannot use the gradient descent formula for continuous parameters)

## EfficientNet
- Scale the depth (number of layers), width (number of channels) and resolution (input image size)
- Idea is that as a model hyperparameter (e.g. model depth) changes, the width and resolution needs to be adjusted accordingly as well


NAS requires alot of models to be trained, so we need to look at fast [[Performance Estimation ]]methods.
#dl