# Datt3400---Cyber_Flow-

![2023-04-16 (3)](https://user-images.githubusercontent.com/122418286/232347247-056c86d8-921f-4f5a-80d7-ad4fa155b37f.png)
![2023-04-16 (1)](https://user-images.githubusercontent.com/122418286/232347243-dd0a4d54-9c61-4063-a2fe-b61525b999d6.png)

How it works:
This code is a p5.js sketch that creates an interactive 3D cube visualization that responds to music. The code starts by declaring variables for a camera, an array of cubes, noise scale, and a boolean to toggle between a dark and light background. The code also loads a music file using the loadSound() function in the preload() function and sets up a canvas with createCanvas() in the setup() function.

Next, the code initializes the amplitude and Fast Fourier Transform (FFT) objects, which are used to analyze the music and determine the visual response. The createEasyCam() function is used to create a movable camera in the 3D space, and the document.oncontextmenu function is used to prevent the right-click menu from appearing.

The code then generates an array of cubes in a grid pattern using nested for-loops in the setup() function. The colors of the cubes are determined by the color() function, and the position and size of each cube are randomly generated. The cubes are stored in the cubes array.

In the draw() function, the background color is set based on the dark boolean variable, and the amplitude of the music is obtained using the amplitude.getLevel() function. The fft.analyze() function is used to obtain the spectrum of the music, which is used to determine the size of each cube. The show() and update() methods of each cube are called to display and animate the cubes.

The mousePressed() function is used to change the background color and randomly move the cubes when the mouse is clicked. The mouseReleased() function is used to set the background color back to the original state when the mouse is released.

Finally, a Cube class is defined, which contains the properties and methods for each cube object. The constructor() function initializes the size, position, color, and stroke weight of the cube, and the show() and update() functions determine how the cube is displayed and animated.

My inspiration:

The genesis of my project can be traced back to the two groundbreaking art movements of the early 20th century, namely Cubism and Futurism. These two styles of art revolutionized the way artists perceived and represented reality, moving away from the traditional techniques of realism and naturalism towards an abstract and geometric approach. One of the most iconic shapes that these movements employed in their art was the cube, which served as a symbol of the dynamism, complexity, and fragmentation of modern life.

It is this innovative use of the cube shape that has inspired me to undertake this project. The cube, with its clean lines, sharp edges, and precise angles, embodies a sense of order and structure that is both visually striking and conceptually profound. Moreover, its three-dimensional nature allows for an exploration of space and perspective that is unique to the medium of sculpture.

As I delve deeper into the principles of Cubism and Futurism, I am fascinated by how these art forms sought to break down the conventions of representation and create new forms of visual language. By utilizing the cube in various ways, such as fragmentation, reassembly, and superimposition, these artists were able to challenge the viewer's perceptions and offer a fresh perspective on the world around them.

In my own work, I aim to channel this spirit of experimentation and innovation, using the cube as a starting point for exploring new possibilities in sculpture. By manipulating the cube shape through cutting, folding, and welding, I hope to create dynamic and visually engaging pieces that offer a unique perspective on space, form, and texture. Ultimately, my goal is to create a body of work that honors the legacy of Cubism and Futurism while pushing the boundaries of what is possible in contemporary sculpture.

Below are some images of the finished code from different angles and moments in the code:

First image:

![2023-04-16 (17)](https://user-images.githubusercontent.com/122418286/232346200-63c3bed2-9546-4365-abf9-a704d71f90cd.png)

After one click and zoomed out:

![2023-04-16 (20)](https://user-images.githubusercontent.com/122418286/232346209-84dc16a4-9499-46c6-a10d-d420463b0ea1.png)

While clicking and zoomed out:

![2023-04-16 (21)](https://user-images.githubusercontent.com/122418286/232346229-9a729711-3832-43ce-91a1-5cd1aedd042c.png)





