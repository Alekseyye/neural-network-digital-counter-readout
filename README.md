Исходный код модели нейросети взят из репозитория jomjol на Github: https://github.com/jomjol/neural-network-digital-counter-readout
В код внесены некоторые правки для того, чтобы он работал с новыми версиями используемых библиотек

Задача нейросети заключается в определении цифр на изображениях и сопоставлении им соответствующих значений. В случае, если цифру невозможно определить (например, когда барабан счётчика находится между двумя цифрами), нейросеть должна отсеивать изображение (присваивая ему значение NaN).

Счётчик выглядит следующим образом:

<img src="./images/counter_complete.png" width="250">  

Нейросеть ставит в соответствие каждому из полученных изображений одно из 11 значений: 10 цифр - от 0 до 9, или NaN





## Neural Network Approach

Convolutional Neural Networks (CNN) are very promiment in image processing. Especially in classification of image content, e.g. identify objects (dog, cat, car, bike, ...) or classify hand written letters.

Here a classic approach is used to classify the picture into 11 output classes representing the 10 digits from 0 to 9 and the "NaN". 

| Picture        | Value           | Picture        | Value           | Picture        | Value           | Picture        | Value           |
| ------------- |:-------------:| ------------- |:-------------:|------------- |:-------------:| ------------- |:-------------:|
| <img src="./images/counter2.jpg" width="60"> | 2 | <img src="./images/counter6.jpg" width="60"> | 6 |<img src="./images/counter9.jpg" width="60"> | 9 | <img src="./images/counterNaN.jpg" width="60"> | NaN |


### Labeled Training Data

The images are coming from a camera system described elsewhere ([Overview](https://github.com/jomjol/water-meter-measurement-system), [HW](https://www.thingiverse.com/thing:3238162), [SW](https://github.com/jomjol/water-meter-picture-provider)). One major effort is to label the pictures with the target value. The labeling is done by hand. For each digit about 150 images are collected. For the "NaN" category about 3700 images were taken. The picture are rescaled to 32x20 pixels with RGB color (3 channels).

The resized pictures as well as the original pictures (zipped in file "data_raw_all.zip") are included in the dataset. The pictures are stored in a subfolder for each digit (and NaN).

The criteria for "good" and "bad" images are described here: [Labeling-Criteria.md](Labeling-Criteria.md)

## Training the network

The training is done using Keras in a python environment. For training purpuses the code is documented in Jupyter notebooks. The environment is setup using Ananconda with Python 3.7[1]. 

The training is descibed in detail in an Jyupither Notebook: **[How to Train the Network](Train_Network.md)**.

The trained network is stored in the Keras H5-format and used as an input for a simple usage in the main project for a water meter readout: [https://github.com/jomjol/water-meter-system-complete](https://github.com/jomjol/water-meter-system-complete)

Hopefully you have fun with neural networks and find this useful. 

**Any questions, hints, improvements are very welcome through the GitHub channel**

Best regards,

**jomjol**


[1]: The following book is found very useful for background, basic setting and different approaches:  
Mattheiu Deru and Alassane Ndiaye: Deep Learning with TensorFlow, Keras, und Tensorflow.js



