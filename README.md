# c.a.-to-model-the-solar-surface

## The project in a nutshell

We created a simulation of the movements of the sun’s surface using just this one image as input:
![CtDed-hc](https://user-images.githubusercontent.com/72736453/119827899-8b654e00-bef1-11eb-8a1e-78ea59dcbba3.png)



To create a mutable, self-organizing texture that resembles the one given above, we rely on Neural Cellular Automata. The idea is that every pixel on an initially white canvas will obey the same rule, which will update their values in each iteration depending on their neighbours’. Such update rule is learned using Artificial Neural Networks.

Voilá! An artificial sun.

https://www.dropbox.com/s/f30n33568prnyf0/gray_750it_1152px.mp4?dl=0


For the sake of comparison, here on the right is a real timelapse of the Sun and on the right our simulation:

https://www.dropbox.com/s/bh7s8q4cvpzi1p6/gray_300it_576px_loop.mp4?dl=0
https://www.dropbox.com/s/qf1e2po0is4eluw/original_loop.mp4?dl=0



How the update rule is learned

Once the so-called “perception vector”, which gathers the information about the pixel and its surroundings, is calculated, it goes through a two-dimensional convolution layer, a ReLU activation and a second two-dimensional convolution layer. The architecture’s weights will be updated according to the difference between the texture extracted from the output and the one extracted from the target image.
(more on style capture here; more about the model here)


Future improvement

The model works with 128 x 128 px images. An increase would make even the 16 Gb GPU on Google Collaboratory run out of memory. The challenge then is to create a scalable model to preserve as much resolution as possible.

(Note that the target image had to be downscaled from 1152 x 1152 px to 128 x 128 px, and then, upscaled to the original size again. Thus, the quality loss is significant)

![2x zoom to the center](https://paper-attachments.dropbox.com/s_C35FADA98156F8CDFEE8E89231D02056212CAAE0ED98F3669E660C31B7C88472_1620214523525_resolution_lost.png)



Notes

The idea for this project belongs to Andrés Asensio, who supervised my undergraduate dissertation and I am lucky to keep on collaborating with.
