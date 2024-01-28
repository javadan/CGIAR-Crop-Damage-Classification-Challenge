# CGIAR-Crop-Damage-Classification-Challenge
https://zindi.africa/competitions/cgiar-crop-damage-classification-challenge

First attempt at a Computer Vision competition.  Doesn't look like it's going very well.  108/352 before the buzzer.  

Got my best score with code that I subsequently lost.  .65 score with efficientvit_l2.r384_in1k and some random cropping and CutMix and some other augmentations.  
First time using FastAI.  It seems super buggy to me.  But nice when it works.  

Tried a few things

1. efficientvit_l2.r384_in1k, then caformer_s36.sail_in22k, then convnextv2_large.fcmae and ensembling, which got about .7 on the public LB.

2. Then tried image tiling, chopping up images into chunks and training on them.  I thought we'd get more detail from the high res images.  Validation score went up to 1.3, so apparently that was worse.

3. convnextv2 did the best of the 3 originals, so I tried using a convnextv2 fed the resized image, plus a histogram per image, which now that I think about it probably is all info already fed in via the pixels... score is TBD...  This one won't be valid for the comp because it seems to use up 11GB of RAM and 2.5GB of VRAM, and so it takes 3 hours to run inference, which is more than the rules allow.  Tried messing around with batch size and num_workers, but nothing fixed it.  Not sure what the issue was there.
