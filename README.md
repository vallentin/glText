
# glText [![Build Status][glTextBuildStatus]][glTextCI] ![Release][glTextVersionBadge] ![Supported OpenGL 3.3][glTextOpenGLVersionsBadge] ![License][glTextLicenseBadge]

[glText][glText] is a simple cross-platform single header text rendering
library for OpenGL. [glText][glText] requires no additional files
(such as fonts or textures) for drawing text, everything comes pre-packed
in the header.


## Example

```c
// Initialize glText
gltInit();

// Creating text
GLTtext *text = gltCreateText();
gltSetText(text, "Hello World!");

// Drawing text
gltColor(1.0f, 1.0f, 1.0f, 1.0f);
gltDrawText2D(text, x, y, scale);

// Deleting text
gltDeleteText(text);

// Destroy glText
gltTerminate();
```


## Optimization

Each time `gltDraw*()` functions are called, `glGetIntegerv(GL_VIEWPORT, ...)`
is called. To avoid this and optimize that call away, define `GLT_MANUAL_VIEWPORT`
before including `gltext.h`.

```c
#define GLT_MANUAL_VIEWPORT
#include "gltext.h"
```

Then when the viewport is resized manually call:

```c
gltViewport(width, height)
```


## Manual Model, View, Projection Matrix

The example uses [LinearAlgebra](https://github.com/MrVallentin/LinearAlgebra).

```c
GLfloat fontScale = 0.01f;

GLfloat x = 0.0f;
GLfloat y = 0.0f;

x -= gltGetTextWidth(text, fontScale) * 0.5f;
y -= gltGetTextHeight(text, fontScale) * 0.5f;

mat4 proj = mat4::perspective(70.0f, viewportWidth, viewportHeight, 0.1f, 10.0f);

mat4 view = ...;

mat4 model = mat4::identity;
model.translate(x, y + gltGetTextHeight(text, fontScale));
model.scale(fontScale, -fontScale);

mat4 mvp = proj * view * model;

gltDrawText(text, (GLfloat*)&mvp);
```


## Aligned Text

```c
// Where horizontal is either:
// - GLT_LEFT (default)
// - GLT_CENTER
// - GLT_RIGHT

// Where vertical is either:
// - GLT_TOP (default)
// - GLT_CENTER
// - GLT_BOTTOM

gltDrawText2DAligned(text, x, y, scale, horizontal, vertical);
```


## No Dependencies

[glText][glText] has no external dependencies besides [OpenGL][OpenGL] and the standard C libraries.
By default [glText][glText] uses `stdlib.h`, `string.h` and `stdint.h`.

If `GLT_DEBUG` is defined `assert.h` is needed. If `GLT_DEBUG_PRINT` is defined `stdio.h` is needed.


## Reporting Bugs & Requests

Feel free to use the [issue tracker][glTextIssues],
for reporting bugs, submitting patches or requesting features.

Before submitting bugs, make sure that you're using the latest version of [glText][glText].


## License

```
Copyright (c) 2013-2016 Christian Vallentin <mail@vallentinsource.com>

This software is provided 'as-is', without any express or implied
warranty. In no event will the authors be held liable for any damages
arising from the use of this software.

Permission is granted to anyone to use this software for any purpose,
including commercial applications, and to alter it and redistribute it
freely, subject to the following restrictions:

1. The origin of this software must not be misrepresented; you must not
   claim that you wrote the original software. If you use this software
   in a product, an acknowledgment in the product documentation would be
   appreciated but is not required.

2. Altered source versions must be plainly marked as such, and must not
   be misrepresented as being the original software.

3. This notice may not be removed or altered from any source
   distribution.
```


[glText]: https://github.com/MrVallentin/glText
[glTextLicense]: https://github.com/MrVallentin/glText/blob/master/LICENSE

[glTextReleases]: https://github.com/MrVallentin/glText/releases

[glTextBuildStatus]: https://drone.io/github.com/MrVallentin/glText/status.png
[glTextCI]: https://drone.io/github.com/MrVallentin/glText/latest

[glTextVersionBadge]: https://img.shields.io/badge/release-v1.1.6-blue.svg
[glTextLicenseBadge]: https://img.shields.io/badge/license-%20free%20to%20use%2C%20share%2C%20modify%20and%20redistribute-blue.svg

[glTextOpenGLVersionsBadge]: https://img.shields.io/badge/OpenGL-3.3-blue.svg

[glTextIssues]: https://github.com/MrVallentin/glText/issues

[OpenGL]: https://en.wikipedia.org/wiki/OpenGL
