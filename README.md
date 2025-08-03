# Google Chrome Buildpack

This buildpack installs Google Chrome in Heroku-compatible environments, making it easy to use browsers in web applications for automated testing or scraping.

## Usage

**Important:** This buildpack must be used in conjunction with [apt-buildpack](https://github.com/fagiani/apt-buildpack/), as Chrome dependencies must be installed first.

### 1. Add the buildpacks to your app
The order of the buildpacks is important. `apt-buildpack` must come before `google-chrome-buildpack`:

```sh
project.toml
. . .
[build]
builder = "heroku/buildpacks:20"

[[build.buildpacks]]
uri = "fagiani/apt"

[[build.buildpacks]]
uri = "fagianijunior/google-chrome"
. . .
```
### 2. Configure o arquivo Aptfile
No diretório raiz do seu projeto, crie um arquivo chamado Aptfile com o seguinte conteúdo:

```
fonts-liberation
libasound2
libatk-bridge2.0-0
libatk1.0-0
libcups2
libgbm1
libxcomposite1
libxdamage1
libxfixes3
libxkbcommon0
libxrandr2
chromedriver
```
Esses pacotes são necessários para garantir o funcionamento correto do Google Chrome e do Chromedriver.

### 3. Deploy
$ pack build myapp 

O Chrome e o Chromedriver estarão disponíveis no PATH da aplicação.

Referências
[apt-buildpack](https://github.com/fagiani/apt-buildpack/)

Licença
MIT