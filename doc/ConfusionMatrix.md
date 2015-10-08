## ConfusionMatrix Overview##

For multi-class classification, `ConfusionMatrix` calculates the mis-classification error in the form of confusion matrix and associated FAR/FFR.
Whenever fed with (prediction, target) pair or pairs,`ConfusionMatrix` updates its internal book keeping for misclassification.
Handy methods are provided to print or plot the confusion matrix. 

## Examples ##
Suppose `instances` and `targets` are both some `torch.Tensor` corresponding to `N` instances, then the updating can be either one-by-one
``` lua
conf = optim.ConfusionMatrix( {'cat','dog','person'} )  -- new matrix three classes
conf:zero()                                             -- reset matrix
for i = 1, N do
    conf:add( net:forward(instance[i]), targets[i] )    -- accumulate errors
end
```
or in a batch
``` lua
conf = optim.ConfusionMatrix( {'0', '1'} )        -- new matrix with two classes
conf:zero()                                       -- reset matrix
conf:batchAdd( net:forward(instances), targets )  -- calculate errors with a batch
```
Finally, the matrix can be showed in different ways
```
image.display(conf:render()  -- plot confusion matrix as image
print(conf)                  -- print matrix as formatted text
```

More examples can be found in [Torch 7 demo repository](https://github.com/torch/demos), e.g., 
[file 1](https://github.com/torch/demos/blob/master/person-detector/train.lua), 
[file 2](https://github.com/torch/demos/blob/master/train-a-digit-classifier/train-on-mnist.lua)

## ConfusionMatrix State Variables ##
`ConfusionMatrix` maintains the confusion matrix with a state variable [mat](#mat)
### mat ###
TODO

TODO: totalValid?

## ConfusionMatrix Methods ##
### add(prediction, target) ###
TODO

### batchAdd(predictions, targets) ###
TODO

### [clsFrr, clsFar, frr, far] farFrr() ###
TODO

### [str]  ###