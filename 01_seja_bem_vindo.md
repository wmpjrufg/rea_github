# Introdução aos Fundamentos do Git

Antes de mergulhar nos aspectos operacionais do Git, é essencial compreender a lógica que sustenta qualquer sistema de controle de versão moderno. Em projetos de engenharia, ciência de dados, desenvolvimento de _software_ ou documentação técnica, a necessidade de registrar, organizar e recuperar alterações é um requisito estratégico para assegurar rastreabilidade, governança e produtividade. Nesse contexto, o Git se consolidou como a principal tecnologia de versionamento distribuído, permitindo que equipes e indivíduos controlem a evolução de seus artefatos com elevado nível de confiabilidade e escalabilidade.  
  
# Controle de versões  

Um sistema de controle de versão é uma solução projetada para gerenciar, de forma estruturada e rastreável, todas as modificações realizadas em um conjunto de arquivos ao longo do tempo. Um controle de versão simplificado poderia ser por representado por um usuário mudando o nome do arquivo a medida que o mesmo fosse alterado.

# Diferença entre Git e GitHub

**Git** e **GitHub** são elementos complementares, porém conceitualmente distintos. O **Git** é um sistema de controle de versão distribuído, instalado localmente na máquina do usuário, responsável por registrar, gerenciar e rastrear todas as alterações realizadas em um projeto. Ele opera de forma descentralizada, permitindo que cada colaborador mantenha uma cópia completa do repositório e execute operações como `commit`, `branch`, `merge` e `rebase` sem depender de conexão com a internet.

Já o **GitHub** é uma plataforma online que hospeda repositórios **Git** na nuvem e adiciona uma camada de serviços colaborativos e de governança do ciclo de desenvolvimento. A plataforma oferece funcionalidades corporativas para trabalho em equipe, como gerenciamento de permissões, pull requests, revisão de código, acompanhamento de tarefas, pipelines de integração e entrega contínua, análises automatizadas e integração com outras ferramentas.  
  
Em síntese, o **Git** é a tecnologia de versionamento; o **GitHub** é o ambiente que potencializa sua utilização em escala, proporcionando colaboração, rastreabilidade e visibilidade para equipes e comunidades de desenvolvimento.

# O que são repositórios e _branchs_

Um conceito muito importante no âmbito do Git são os repositórios e ramificações (em inglês _branchs_ e nome mais usado). Um repositório, em um contexto geral, é um local onde algo é armazenado, organizado e mantido. O termo pode ser aplicado a diversas áreas, mas é frequentemente usado na área de tecnologia da informação e desenvolvimento de _software_.  
  
Já as _branchs_ são caminhos separados de desenvolvimento que permitem que você trabalhe em diferentes recursos, correções de _bugs_ ou melhorias de forma independente, sem interferir no código principal. Cada branch representa uma linha de desenvolvimento separada com sua própria cópia do código-fonte e histórico de alterações.  

# Configurações Gerais  

Após fazer o download e instalação das aplicações precisamos configurar nosso Git na máquina. Este passo é fundamental, já que a ferramenta de versionamento precisa reconhecer a máquina e o autor das alterações que serão posteriormente agregadas ao repositório remoto. Este passo pode ser feito de duas formas diferentes, sendo uma configuração global, ou seja, válida para qualquer repositório que está na máquina ou de forma individual. Inicialmente vamos configurar apenas duas informações, que já serão suficiente para prosseguirmos com as atualizações

Vamos aplicar as modificações globais e estas aparecerão no histórico do Git:

```bash
git config --global user.name "meu_nome"
```
  
## _Exemplo_
```bash
git config --global user.name "einsten123"
```

Feito isso, a segunda informação que precisamos é o email, que é o mesmo criado para a conta do GitHub.

```bash
git config --global user.email <meu_email@email.com>
```

### _Exemplo_
```bash
git config --global user.email "einsten123@ufcat.edu.br"
```
  
Pronto nosso ambiente Git já está configurado e preparado para o uso. Para verificar as credenciais inseridas utilize os comandos de forma individual:

```bash
git config --global user.name
git config --global user.email
```
  
# Meu primeiro repositório
  
##  Criando direto no GitHub  
O primeiro passo para começarmos a trabalhar com a ferramenta é a criação de um repositório, que servirá para armazenar projetos que serão controlados pelo GitHub. Para inicializar um repositório vamos usar os seguinte passos:

- Vá para [https://github.com](https://github.com)
- Clique em `New repository`
- Preencha:
  - Nome: exemplo: meu-projeto
  - Opções: deixe como público ou privado
  - `README.md` desmarque essa opção se for fazer copia de um repositório local existente
  - Clique em _Create repository_

Após criar o repositório remoto, o GitHub exibirá os comandos necessários para estabelecer a vinculação com seu repositório local. Existem múltiplos protocolos de acesso disponíveis, como `HTTPS`, `SSH` e `GitHub CLI`, cada um com características específicas de autenticação e segurança. Neste material, adotaremos o protocolo `HTTPS`, por ser o método mais direto para usuários iniciantes e permitir a clonagem do repositório a partir de um link no formato: `https://github.com/seu-usuario/meu-projeto.git`.

### Clonando localmente  
  
A clonagem de um repositório consiste em criar, na máquina local, uma réplica completa do repositório remoto, incluindo todo o histórico de versões, ramificações, commits, arquivos e pastas existentes naquele momento. Em outras palavras, trata-se de uma cópia integral do projeto, permitindo que o usuário trabalhe de forma independente, execute alterações, crie _branchs_ e sincronize novamente com o servidor sempre que necessário.  

Para clonar localmente escolhe a pasta onde deseja salvar os arquivos com o seguinte comando:

```bash
git clone https://github.com/seu-usuario/meu-projeto.git
```  
  
> Evite salvar um repositório em pastas que são sincronizadas com Google Drive, One Drive ou qualquer serviço dessa natureza, pois reduz a velocidade em algumas utilizações.
  
##  Criando localmente e armazenando no GitHub  
 
Para inicializar o Git no seu projeto local, abra o terminal de comandos do computador e insira os seguintes comandos:
  
```bash
cd caminho/do/seu-projeto       # Vai para a pasta do seu projeto
git init                        # Inicia o Git no projeto
git add .                       # Adiciona todos os arquivos pré-existentes
git commit -m "primeiro commit" # Faz o commit inicial a ser explicado a frente
```  
   
Em seguida, para se conectar ao repositório do GitHub copie a URL do seu repositório do GitHub, como: `https://github.com/seu-usuario/meu-projeto.git` em seguida, no terminal:
  
```bash
git remote add origin https://github.com/seu-usuario/meu-projeto.git    # Vai conectar a pasta ao repositório online 
git branch -M main                                                      # Renomeia a branch principal
git push -u origin main                                                 # Envia o projeto para o GitHub
```  
  