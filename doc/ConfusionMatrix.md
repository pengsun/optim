## ConfusionMatrix Overview##

For multi-class classification, `ConfusionMatrix` compares the predictions (aka outputs) with the targets (aka labels) and calculates the mis-classification error in several measures, including confusion matrix, total accuracy, associated FAR/FFR, etc.
<!--
Whenever fed with (prediction, target) pair or pairs,`ConfusionMatrix` updates its internal book keeping for misclassification.
Handy methods are provided to print or plot the confusion matrix. 
-->

## Examples ##
Create a new `ConfusionMatrix` and initialize it
``` lua
conf = optim.ConfusionMatrix({'cat','dog','person'})  -- for a three-class classification
conf:zero()                            -- reset
```
Then update `conf` by feeding prediction-target pair either one-by-one
``` lua
for i = 1, N do
    predictions[i] = someNet:forward(inputs[i])
    conf:add(predictions[i], targets[i] )    -- accumulate errors
end
```
or in a batch
``` lua
predictions = someNet:forward(inputs)
conf:batchAdd(predictions, targets)  -- calculate errors with a batch
```
Finally, the confusion matrix can be showed in different ways
``` lua
image.display(conf:render()  -- plot confusion matrix as image
print(conf)                  -- print matrix as formatted text
```
One can also get other mis-classification measures by accessing the state variables
``` lua
conf.updateValids() -- REQUIRED before accessing any state varible!
print('accuracy = ' .. 100*conf.totalValid .. '%')
```

More complete, ready-to-run examples can be found in [Torch 7 demo repository](https://github.com/torch/demos), e.g., 
[file 1](https://github.com/torch/demos/blob/master/train-on-cifar/train-on-cifar.lua), 
[file 2](https://github.com/torch/demos/blob/master/train-a-digit-classifier/train-on-mnist.lua)

## ConfusionMatrix State Variables ##
`ConfusionMatrix` maintains the confusion matrix with a state variable [mat](#mat), 
which get updated when calling [add()](#add) or [batchAdd()](#batchAdd).
Other state variables (i.e., [totalValid](#totalValid), TODO ) for various mis-classification measures are also available, 
which get updated when calling [updateValids()](#updateValids)

### mat ###
TODO

### totalValid ###
TODO:

## ConfusionMatrix Methods ##
### add(prediction, target) ###
TODO

### batchAdd(predictions, targets) ###
TODO

### updateValids() ###
TODO

### [clsFrr, clsFar, frr, far] farFrr() ###
TODO

### [str] __tostr__() ###