# Personal Blog

Static blog built with **Hugo** using the [goKarna-hugo](https://github.com/olavob/gokarna-hugo) theme (maintained fork).

Visit the blog: https://olavob.github.io

## 🛠️ Tools Used

<!-- Hugo -->
<img src="https://img.shields.io/badge/Hugo-Static%20Site%20Generator-blue?logo=hugo" alt="Hugo">

<!-- goKarna Theme -->
<img src="https://img.shields.io/badge/Theme-goKarna--hugo-black?logo=github" alt="goKarna Theme">

<!-- Go -->
<img src="https://img.shields.io/badge/Go-Programming%20Language-00ADD8?logo=go&logoColor=white" alt="Go">

<!-- Git -->
<img src="https://img.shields.io/badge/Git-Version%20Control-F05032?logo=git&logoColor=white" alt="Git">

<!-- GitHub Pages -->
<img src="https://img.shields.io/badge/GitHub%20Pages-Hosting-121013?logo=github&logoColor=white" alt="GitHub Pages">

<!-- Disqus -->
<img src="https://img.shields.io/badge/Disqus-Comments%20System-2E9FFF?logo=disqus&logoColor=white" alt="Disqus">

## 🚀 How to Run Locally

Follow the steps below to run the blog on your machine:

### 1. Prerequisites

Install the following tools:

- **Git** → [git-scm.com](https://git-scm.com)
- **Go** → [golang.org/doc/install](https://golang.org/doc/install)
- **Hugo Extended** (latest version) → [gohugo.io/getting-started/installing/](https://gohugo.io/getting-started/installing/)

### 2. Clone the repository with the theme

```bash
git clone --recursive https://github.com/olavob/olavob.github.io.git
cd olavob.github.io
```

The --recursive flag is important to automatically download the theme submodule.
If you already cloned without --recursive, run:

```Bash
git submodule update --init --recursive
```

### 3. Start the development server

```Bash
hugo server -D
```

The blog will be available at: http://localhost:1313
The -D flag includes draft posts (draft: true)

### 4. Build for production

```Bash
hugo
```

The generated files will be in the public/ folder.
License
This work is licensed under the
Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0).

<img src="https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg" alt="CC BY-NC-SA 4.0">

You are free to share and adapt the content as long as you:

Give appropriate credit
Do not use it for commercial purposes
Distribute your modifications under the same license

See the full license: https://creativecommons.org/licenses/by-nc-sa/4.0/

Made with ❤️ using Hugo.