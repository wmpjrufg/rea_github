---
title: Uso do gitignore
layout: home
nav_order: 1
parent: Git e GitHub na prática
---

<h1>Uso do .gitignore</h1>

<p align = "justify">
Por padrão, o Git possui um arquivo chamado <a href="https://docs.github.com/pt/get-started/getting-started-with-git/ignoring-files"><i>.gitignore</i></a>, que serve para manter arquivos ou pastas fora do rastreamento do Git. Esta funcionalidade é útil quando queremos utilizar um arquivo/pasta apenas de forma local.
<br><br>
Para utilizar essa funcionalidade basta criar um arquivo com o nome <code>.gitignore</code> (caso ele não exista) no diretório em que deseja ocultar o arquivo/pasta. Então, todos os nomes de arquivos ou extensões que forem adicionados nele, não serão adicionados ao sistema de controle. Vamos ver alguns exemplos:
</p>

{: .warning }
> É necessário usar a nomenclatura completa com o `.` antes do nome `gitignore`.

Exemplo 1
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar todos os arquivos com a extensão <code>.log</code>. Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
*.log
```

Exemplo 2
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar todos as pastas com a nomenclatura <code>logs</code>. Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
**logs/
```

Exemplo 3
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar todos os arquivos com a extensão <code>.log</code>. Porém esse arquivo <code>.log</code> tem variações do tipo <code>debugA.log</code>, <code>debug10.log</code>. . Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
debug?.log
```

Exemplo 4
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar um arquivo específico com extensão <code>.ipynb</code> dentro de uma pasta do projeto. Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
testes/testando_funcao.ipynb
```

<p align = "justify">
   <i>
   Assim, apenas o arquivo <code>testando_funcao.ipynb</code> localizado dentro da pasta <code>testes/</code> será ignorado pelo Git. 
   <i>
</p>

Exemplo 5
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar uma *pasta inteira de build*, comum em projetos <code>Python<code>, <code>C<code>, <code>Java<code>, etc. Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
/build/
```

<p align = "justify">
   <i>
   Isso impede o Git de rastrear qualquer arquivo gerado automaticamente dentro da pasta <code>build/</code>.
   <i>
</p>

Exemplo 6
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar pastas de ambientes virtuais Python. Ambiente virtual não tem um nome fixo; ele pode se chamar <code>venv</code>, <code>.venv</code>, <code>env</code>, entre outros. Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
venv/
```

<p align = "justify">
   <i>
   Assim, não enviamos o ambiente virtual — que geralmente possui milhares de arquivos — para o Git. Neste exemplo estamos considerando o nome do ambiente como <code>venv</code>, mas ele poderia ter qualquer outro nome. Os mais comuns são <code>venv</code> e <code>env</code>.
   <i>
</p>

Exemplo 7
{: .label .label-yellow }

<p align = "justify">
  <i>
  Vamos supor que desejemos ignorar arquivos que contêm informações sensíveis, como chaves de API ou senhas. Como ficaria o arquivo <code>.gitignore</code>?:
  </i>
</p>

<p align = "justify">
Entrando dentro do arquivo <code>.gitignore</code> editamos da seguinte forma:
</p>

```shell
*.env
config_secret.json
```

<p align = "justify">
   <i>
   É importante evitar subir esses arquivos para proteger o projeto.
   <i>
</p>