# Nexus 3 Artifact Upload [![Build Status](https://travis-ci.org/TOPdesk/nexus3-artifact-upload.svg?branch=master)](https://travis-ci.org/TOPdesk/nexus3-artifact-upload)
> A drop-in solution for the missing artifact upload UI for [Sonatype Nexus 3 Repository](https://www.sonatype.com/nexus-repository-oss).

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [Known issues](#known-issues)
- [License](#license)

## Installation
Our goal was to make installation as easy as possible: you need to *host* the *index.html* file on your Nexus 3 installation in a raw repository, that has public access. Yes, that is all.

#### Example:
- Consider having your Nexus 3 running at `https://nexus.mycompany.com/nexus` and a *raw* repository identified as `utils`
- Grab the `index.html` and upload it with `curl` (or whatever you like):
  ```bash
  $ curl -u <user>:<password> \
         --upload-file index.html \
         https://nexus.mycompany.com/nexus/repository/utils/uploader
  ```
  Note that user and password sould be an account that has write access to the utils repositroy.
- Done


## Usage
Visit `https://nexus.mycompany.com/nexus/repository/utils/uploader` and enjoy the integrated artifact uploader.
You can pick a repository, browse (or drop) a file, fill in the details, and press the upload button.

## Contributing
By all means! If you have a fix or an improvement, pull requests are welcome. We are also happy to get any feedback.

## Known issues
- This is really a basic implementation, some useful features are missing. You can upload files with Maven's GAV style, or do raw uploads to any other repository (in this case you need to know the proper URL).
- Input is not validated, it will try to upload with specified settings, and you will have a success, or an error based on what you did.
- You can use the login feature of Nexus, but if you are not logged in, you will be promted for Basic Auth by the browser. That will work for upload, if your setup allows that.
- The JavaScript code uses arrow functions, so it will not work with IE11, but you can experiment with Babel!

#### Browsers we tried

| Google Chrome 58.0 | Chromium 58.0 | Opera 45.0 | Microsoft Edge 38 | Mozilla Firefox 53.0 | IE11 |
| :----------------: | :-----------: | :--------: | :---------------: | :------------------: | :--: |
| ✔                  | ✔             | ✔          | ✔ (weird looks)   | ✔ (visual glitches)  | ✖    |

#### Checked Nexus 3 Versions
- PRO 3.2.1-01
- OSS 3.3.1-01

## License
<pre>MIT License

Copyright (c) 2017 TOPdesk

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.</pre>
