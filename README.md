# Electronic Schematic Recognizer

Electronics becomes a lot easier if you can simulate circuits before making them. But there is a large learning curve to getting started with simulation, nit the least being learning a new software to make the schematic in. One of the most common and best circuit simulation tools is Spice with variants from various electronics companies, e.g. LTSpice from Linear Technologies.

![LTSpice Interface](https://github.com/tinkrmind/electrical-schematic-recognizer/blob/master/screengrabs/LTSpice.PNG)

As you can see from the image above, the LTSpice interface leaves a lot wanting. And it is not really going to change anytime soon.

Electronic Schematic Recognizer is an attempt to reduce the barrier to entry to circuit simulation by digitizing hand drawn schematics which can later be converted to spice models. Here are some of the results from the project:

![Circuit Result 1](https://github.com/tinkrmind/electrical-schematic-recognizer/blob/master/screengrabs/circuitResult1.PNG)

![Circuit Result 2](https://github.com/tinkrmind/electrical-schematic-recognizer/blob/master/screengrabs/circuitResult2.PNG)

## Process

To start with, I reduced the scope of the problem to recognize capacitors, resistors, batteries, current supplies, voltmeters, and leds. I then hand drew hundreds of symbols of these elements on paper and scanned them. The original scans are in assets folder on the github. I wrote an openCV python script to segment the individual symbols into separate square images. Finally I used [this](https://github.com/gskielian/JPG-PNG-to-MNIST-NN-Format) excellent repo to convert the images into an MNIST database that can be used for training a CNN model.

![Segmenting individual Circuit elements](https://github.com/tinkrmind/electrical-schematic-recognizer/blob/master/screengrabs/secondBoundingBoxSuccess.JPG)

Given a new circuit, I use the same openCV script to segment the electrical symbols and then recognize the symbols using the trained CNN model.
