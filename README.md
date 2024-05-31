Исходный код модели нейросети взят из репозитория jomjol на Github: https://github.com/jomjol/neural-network-digital-counter-readout
В код внесены некоторые правки для того, чтобы он работал с новыми версиями используемых библиотек

Задача нейросети заключается в определении цифр на изображениях и сопоставлении им соответствующих значений. В случае, если цифру невозможно определить (например, когда барабан счётчика находится между двумя цифрами), нейросеть должна отсеивать изображение (присваивая ему значение NaN).

Счётчик выглядит следующим образом:

<img src="./images/counter_complete.png" width="250">  

Нейросеть ставит в соответствие каждому из полученных изображений одно из 11 значений: 10 цифр - от 0 до 9, или NaN

| Picture        | Value           | Picture        | Value           | Picture        | Value           | Picture        | Value           |
| ------------- |:-------------:| ------------- |:-------------:|------------- |:-------------:| ------------- |:-------------:|
| <img src="./images/counter2.jpg" width="60"> | 2 | <img src="./images/counter6.jpg" width="60"> | 6 |<img src="./images/counter9.jpg" width="60"> | 9 | <img src="./images/counterNaN.jpg" width="60"> | NaN |

Изображения нейросеть должна получать с изображения с камеры, наблюдающей за счётчиком. Из этого изображения "вырезаются" фрагменты, содержащие цифры, и далее обрабатываются нейросетью.

В папке приложен датасет с примерами (примерно по 150 для каждой из цифр, около 3700 для значения NaN). С помощью кода ImagePreparation они переведены в RGB-изображения с разрешением 32х20. С использованием этого датасета можно легко обучить нейросеть.

Тренировка нейросети производится в ходе выполнения кода Train_CNN_Digital_Readout, реализованного с использованием библиотек TensorFlow и Keras (открытые библиотеки для машинного обучения и взаимодействия с нейросетями). На выходе получаем файл в формате .h5, который можно использовать далее в качестве вводного данного в требующем использования нейросети проекте (например, в программе для считывания данных с счётчика воды).

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



