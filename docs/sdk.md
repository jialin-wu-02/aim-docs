---
id: sdk
title: aim SDK
sidebar_label: SDK
---
aim SDK is a very simple and easy to learn tool that saves the info about the

```py
import aim
from aim import track
```

## Track

Tracking allows the user to save the intermediate values of tensors, scalars and other debugging metrics. It looks like this:
```py
aim.track('name-of-the-component', params)
```

### Loss
Loss is tracked in the following way:
```py
track(aim.loss, 'name of the loss', '0.2') # 0.2 is the loss
```

### Misclassification
Misclassifications allow to track the correct lable, image and what actually was classified. It looks like this:

First, save the image:
```py
img = track(aim.image, image_tensor)
```
Track the misclassification:
```py
track(aim.misclassifiction, 'name of the component', img, <label>, <NN output>)
```

### Checkpoint & Meta Info
Tracking checkpoints allows to save checkpoints at different epochs to be able to pick the best.
Aim SDK allows to save arbitrary type of data along with checkpoints. Here is how it works:
```py
track(aim.checkpoint, 'saved checkpoint name', 'epoch_name',
      model, epoch, lr_rate=learning_rate,
      meta={
        'any data': 'any value'
      })
```
