# S2DGL
S2DGL A simple 2D rendering library using OpenGL.

## Setup
Just copy the cpp and header files to your project.
Call S2DGL::init();
create a S2DGL::Renderer2D
## Dependencies
+[GLAD](https://glad.dav1d.de/) (Any OpenGL loader works, i prefer GLAD)
*[GLM](https://github.com/g-truc/glm)
-[stb_image](https://github.com/nothings/stb/blob/master/stb_image.h)
*[stb_truetype](https://github.com/nothings/stb/blob/master/stb_truetype.h)
## Example
```
#include <glad/glad.h>
#include <glfw/glfw3.h>
#include "S2DGL.h"

int main()
{
	// Initialize GLFW
	glfwInit();
	GLFWwindow *window = glfwCreateWindow(840, 640, "Window", nullptr, nullptr);
	glfwMakeContextCurrent(window);
	gladLoadGLLoader((GLADloadproc)(glfwGetProcAddress));

	// Initialize S2DGL
	S2DGL::init();
	S2DGL::Renderer2D renderer;
	renderer.create();

	// Main loop
	while (!glfwWindowShouldClose(window))
	{
		int w = 0; int h = 0;
		glfwGetWindowSize(window, &w, &h);
		renderer.updateWindowMetrics(w, h);

		// Handle input and update

		// Clear screen
		renderer.clearScreen({0.0, 0.0, 0.0, 1});

		// Render objects
		renderer.renderRectangle({100, 250, 100, 100}, Colors_White, {}, 0);

		// Add more rendering here...

		// Flush renderer (dump your rendering into the screen)
		renderer.flush();

		// Swap buffers and poll events
		glfwSwapBuffers(window);
		glfwPollEvents();
	}
	//cleanup
	return 0;
}
```
