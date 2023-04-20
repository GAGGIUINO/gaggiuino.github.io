<div align="center">

[![Gaggiuino](/images/GAGGIUINO_LOGO_transp.png)](https://gaggiuino.github.io/#/)

[![Discord Chat](https://img.shields.io/discord/890339612441063494)](https://discord.gg/eJTDJA3xfh "Join Discord Help Chat")
</div>

# Gaggiuino Documentation

This repo holds the documentation for the [Gaggiuino] project. It uses [docsify] to render static pages via [GitHub Pages].

## Local Development and Testing

### Using Docsify

First, install docsify globally:

```
npm i docsify-cli -g
```

Run a local web server on the `./docs` folder:

```
docsify serve docs
```


### Using Python

If Python is installed on your computer, it can run a web server to preview the web pages locally.

```
cd docs && python3 -m http.server 3000
```

Then, the site can be viewed at: http://localhost:3000/


## Contributing Changes

Pull requests are appreciated, please see the [GitHub Flow documentation] for more information on how to do that.

[Gaggiuino]: https://github.com/Zer0-bit/gaggiuino
[docsify]: https://docsify.js.org/
[GitHub Pages]: https://pages.github.com/
[GitHub Flow documentation]: https://docs.github.com/en/get-started/quickstart/github-flow
