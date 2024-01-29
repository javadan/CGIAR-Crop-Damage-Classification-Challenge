# CGIAR-Crop-Damage-Classification-Challenge
https://zindi.africa/competitions/cgiar-crop-damage-classification-challenge

First attempt at a Computer Vision competition.  Doesn't look like it's going very well.  101/353.  Meh.

Got my best score with code that I subsequently lost (i.e. overwrote, with newer code).  
My top result was .65 with efficientvit_l2.r384_in1k and some random cropping and CutMix and some other augmentations.  
First time using FastAI.  It seems super buggy to me.  But nice when it works.  
e.g. Save as .pth or export as .pkl?: sometimes it won't let you export as .pkl and sometimes it won't let you load from .pth.
e.g. Using some complex batch_tfms like CutMix? Then some things like lr_find and some item_tfms options won't work.



Image_tiling_CGIAR_2023.ipynb - image tiling, chopping up images into chunks. I thought we'd get more detail from the high res images.  Validation score went up to 1.3, so apparently that was worse.

CNN_and_histogram_CGIAR_2023.ipynb WIP- ran out of time  
1. basic efficientvit_l2.r384_in1k, (about .7 ish on public LB) then
2. caformer_s36.sail_in22k, (about .7 ish on public LB) ,then
3. convnextv2_large.fcmae with attempt to merge histograms, which in hindsight, is, i dunno. That data is already encoded in the pixels.  Right?   We're gonna have to ask GPT4 about this one, and maybe even Claude.  GPT4 suggests isotonic regression.  There's always more to learn.

got weird output.  still meaningful output?

    logits:
    ID	DR	G	ND	WD	other
    ID_SJBCSZ	-1.5997245	-0.21110994	-4.5409064	-0.5731514	-4.0951037  
    ID_4UMPJL	-1.5987856	-0.21640371	-4.540986	-0.56841195	-4.09604  
    ID_AB4DZF	-1.5956886	-0.21697117	-4.5416307	-0.570616	-4.0943494  
    ID_H257JS	-1.6071882	-0.20562026	-4.5432496	-0.56928974	-4.099599  
    ID_JKST46	-1.5893495	-0.22358689	-4.5396028	-0.5720792	-4.091543  
    
    probs:  
    ID,DR,G,ND,WD,other  
    ID_SJBCSZ,0.16802011,0.44741762,0.010551222,0.36050996,0.016381206
    ID_4UMPJL,0.16815141,0.44610924,0.010550389,0.36160335,0.01636613  
    ID_AB4DZF,0.16858506,0.44596905,0.010543662,0.36109468,0.016393365  
    ID_H257JS,0.16697936,0.4487753,0.010526786,0.36140072,0.016308933  
    ID_JKST46,0.16947544,0.44433498,0.01056484,0.3607572,0.016438674  
    ID_5KX2YU,0.16885884,0.4465738,0.010558716,0.3595843,0.016424658  

hmm.  a mystery for another day?  
I'll ask GPT4 if this can be salvaged.  Their answer is mystical, " it might indicate an issue with the model or the data".  Indeed, it does.  Exercise left for the reader?  (this is an art project now.)
Here are dalle's takes on activation functions, in no particular order

    Sigmoid Activation Function

    Tanh (Hyperbolic Tangent) Activation Function

    ReLU (Rectified Linear Unit) Activation Function

    Leaky ReLU Activation Function

    ELU (Exponential Linear Unit) Activation Function

    Softmax Activation Function

    Swish Activation Function

    Mish Activation Function

    SELU (Scaled Exponential Linear Unit) Activation Function

    GELU (Gaussian Error Linear Unit) Activation Function


![2e1cee55-db5b-455c-bbd7-e67bf79c1c70](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/0345960b-aa4c-45a4-abe6-2a57b55606a4)
![DALL·E 2024-01-28 22 17 38 - Close-up illustration of the GELU (Gaussian Error Linear Unit) activation function  Include the graph of the function, its mathematical formula, and a](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/da8c8174-a6e1-41bd-9c5d-c99e9440f017)
![DALL·E 2024-01-28 22 17 40 - Close-up illustration of the SELU (Scaled Exponential Linear Unit) activation function  Include the graph of the function, its mathematical formula, a](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/8a731f1b-87fa-4766-bef7-b99f318b011b)
![DALL·E 2024-01-28 22 17 50 - Close-up illustration of the Leaky ReLU activation function  Include the graph of the function, its mathematical formula, and a brief description high](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/e26a20c7-2899-4e9b-9726-aff8a900c4ab)
![DALL·E 2024-01-28 22 17 55 - Close-up illustration of the Tanh (Hyperbolic Tangent) activation function  Include the graph of the function, its mathematical formula, and a brief d](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/b053f7af-f14d-4f67-921a-699c4c412f09)
![DALL·E 2024-01-28 22 17 42 - Close-up illustration of the Mish activation function  Include the graph of the function, its mathematical formula, and a brief description highlighti](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/5b769150-4bb1-4671-910b-395a5c50260a)
![DALL·E 2024-01-28 22 17 46 - Close-up illustration of the Softmax activation function  Include the graph of the function, its mathematical formula, and a brief description highlig](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/b97b6039-d55a-4791-b86e-016afce36509)
![DALL·E 2024-01-28 22 17 58 - Close-up illustration of the Sigmoid activation function  Include the graph of the function, its mathematical formula, and a brief description highlig](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/954a0365-3e5a-4515-9c3e-726939449c71)
![DALL·E 2024-01-28 22 17 44 - Close-up illustration of the Swish activation function  Include the graph of the function, its mathematical formula, and a brief description highlight](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/4ff4480e-5b13-4d1f-ac46-d9988b45a7fb)
![DALL·E 2024-01-28 22 17 48 - Close-up illustration of the ELU (Exponential Linear Unit) activation function  Include the graph of the function, its mathematical formula, and a bri](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/dc4b16fc-53d5-4ec1-a952-5679861f502d)
![DALL·E 2024-01-28 22 17 53 - Close-up illustration of the ReLU (Rectified Linear Unit) activation function  Include the graph of the function, its mathematical formula, and a brie](https://github.com/javadan/CGIAR-Crop-Damage-Classification-Challenge/assets/3356298/067724dd-ac96-4e9e-996b-3b2d4bc01f38)



