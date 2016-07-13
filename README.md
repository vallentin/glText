
# glText [![Build Status][glTextBuildStatus]][glTextCI] ![Release][glTextVersionBadge] ![Supported OpenGL 3.3][glTextOpenGLVersionsBadge] ![License][glTextLicenseBadge]


## Example

```c
// Creating text
GLTtext *text = gltCreateText();
gltSetText(text, "Hello World!");

// Drawing text
gltColor(1.0f, 1.0f, 1.0f, 1.0f);
gltDrawText2D(text, x, y, scale);

// Deleting text
gltDeleteText(text);
```


## Reporting Bugs & Requests

Feel free to use the [issue tracker][glTextIssues],
for reporting bugs, submitting patches or requesting features.

Before submitting bugs, make sure that you're using the latest version of [glText][glText].


## License

```
glText <https://github.com/MrVallentin/glText>

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

[glTextVersionBadge]: https://img.shields.io/badge/release-v1.1.4-blue.svg
[glTextLicenseBadge]: https://img.shields.io/badge/license-%20free%20to%20use%2C%20share%2C%20modify%20and%20redistribute-blue.svg

[glTextOpenGLVersionsBadge]: https://img.shields.io/badge/OpenGL-3.3-blue.svg

[glTextIssues]: https://github.com/MrVallentin/glText/issues
