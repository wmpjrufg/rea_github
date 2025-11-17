# 🚀 Guia Básico de Git e GitHub

Este guia é focado nos comandos essenciais para começar a usar o Git para controle de versão, seja em projetos locais ou colaborando no GitHub.

## 1. Configuração Inicial (Apenas uma vez)

Antes de tudo, você precisa se apresentar ao Git. [cite_start]Isso é usado para registrar quem fez cada alteração[cite: 5, 6].

* `git config --global user.name "Seu Nome"`
    * [cite_start]**O que faz:** Define o nome de usuário que aparecerá nos seus commits[cite: 11].
* `git config --global user.email "seu.email@example.com"`
    * [cite_start]**O que faz:** Define o e-mail que aparecerá nos seus commits[cite: 13].
* `git config --list`
    * [cite_start]**O que faz:** Verifica todas as configurações ativas[cite: 15].

---

## 2. Como Começar um Repositório

Você pode começar um projeto do zero ou "baixar" um projeto que já existe em um local remoto (como o GitHub).

* `git init`
    * [cite_start]**O que faz:** Inicializa um repositório Git em um diretório que já existe[cite: 18]. [cite_start]Ele cria uma pasta oculta `.git` para rastrear tudo[cite: 20].
* `git clone <url-do-repositorio>`
    * [cite_start]**O que faz:** Clona (baixa uma cópia completa) de um repositório remoto para a sua máquina local[cite: 22, 24].

---

## 3. O Ciclo Básico (Seu Trabalho Local)

Este é o fluxo que você mais usará: modificar, adicionar e "commitar" (salvar) suas alterações.

* `git status`
    * [cite_start]**O que faz:** Mostra o estado atual do seu repositório[cite: 28]. [cite_start]Informa quais arquivos foram modificados, quais estão prontos para commit (na "staging area") e quais não estão sendo rastreados[cite: 30].
* `git add <nome-do-arquivo>`
    * [cite_start]**O que faz:** Adiciona um arquivo específico à "staging area" (área de preparação), preparando-o para ser salvo no próximo commit[cite: 32, 33].
* `git add .`
    * [cite_start]**O que faz:** Adiciona **todas** as alterações (arquivos novos e modificados) no diretório atual para a staging area[cite: 34].
* `git commit -m "Sua mensagem descritiva"`
    * [cite_start]**O que faz:** Salva permanentemente as alterações que estão na staging area no histórico do seu repositório[cite: 39].

### O que é um "Bom" Commit?

[cite_start]O comando é sempre `git commit`[cite: 38], mas a **mensagem** é crucial. [cite_start]Para novos usuários, o mais importante é que a mensagem seja **clara e descritiva**[cite: 39].

Com o tempo, você verá padrões chamados **Commits Convencionais**. Eles ajudam a organizar o histórico, especialmente em equipes. Eles usam prefixos como:

* **feat:** (Nova funcionalidade)
* **fix:** (Correção de um bug)
* **docs:** (Mudanças na documentação)
* **style:** (Mudanças de formatação, sem lógica)
* **refactor:** (Reescrever código sem mudar o que ele faz)
* **chore:** (Tarefas de manutenção, build, etc.)

**Exemplo:** `git commit -m "fix: corrige o cálculo de login do usuário"`

---

## 4. Trabalhando com Branches (Ramificações)

[cite_start]Branches (ramos) permitem que você trabalhe em novas funcionalidades ou correções sem afetar a linha principal de desenvolvimento (normalmente chamada de `main` ou `master`)[cite: 41].

* `git branch`
    * [cite_start]**O que faz:** Lista todas as branches locais[cite: 44].
* `git branch <nome-da-nova-branch>`
    * [cite_start]**O que faz:** Cria uma nova branch [cite: 47][cite_start], mas não muda para ela[cite: 48].
* `git checkout <nome-da-branch>` ou `git switch <nome-da-branch>`
    * [cite_start]**O que faz:** Muda para a branch especificada[cite: 50, 53]. [cite_start]`switch` é uma alternativa mais moderna[cite: 53].
* `git checkout -b <nome-da-nova-branch>` ou `git switch -c <nome-da-nova-branch>`
    * [cite_start]**O que faz:** Um atalho que **cria** e **muda** para a nova branch de uma só vez[cite: 55, 57].
* `git branch -d <nome-da-branch>`
    * [cite_start]**O que faz:** Deleta uma branch local que já foi mesclada (integrada)[cite: 59, 60].

---

## 5. Sincronizando com o Remoto (GitHub)

Estes são os comandos para "atualizar" seu código, seja enviando suas mudanças ou recebendo as de outros.

* `git remote add origin <url-do-repositorio-remoto>`
    * [cite_start]**O que faz:** Adiciona um "apelido" (normalmente `origin`) para a URL do seu repositório remoto[cite: 86, 87].
* `git push origin <nome-da-branch>`
    * [cite_start]**O que faz:** **Envia** seus commits locais para o repositório remoto (GitHub)[cite: 91].
* `git fetch origin`
    * [cite_start]**O que faz:** **Baixa** as atualizações do repositório remoto, mas **não as aplica** (mescla) automaticamente no seu código local[cite: 99]. [cite_start]Você pode ver o que mudou (ex: `origin/main`) sem afetar seu trabalho[cite: 100]. Isso é muito útil para evitar conflitos inesperados.
* `git pull origin <nome-da-branch>`
    * **O que faz:** **Recebe** as atualizações do repositório remoto. [cite_start]É um atalho para fazer `git fetch` (baixar) e `git merge` (mesclar) de uma só vez[cite: 95, 96].

**Qual usar para atualizar?**
* **`git pull`**: É o mais comum e direto. Baixa e tenta mesclar.
* **`git fetch`**: É mais "seguro". Você baixa, vê o que mudou, e então decide como e quando mesclar (usando `git merge origin/main`, por exemplo).

---

## 6. Integrando Mudanças (Merge e Rebase)

Quando você termina o trabalho em uma branch, você precisa integrá-lo de volta à branch principal (ex: `main`).

* `git merge <nome-da-branch-a-mesclar>`
    * **O que faz:** (Primeiro, esteja na branch que vai *receber* as mudanças, ex: `git checkout main`). [cite_start]Este comando integra o histórico da branch especificada na sua branch atual[cite: 66].
    * **Tipos de Merge:**
        * **Fast-Forward:** Se a `main` não teve nenhuma mudança enquanto você trabalhava na sua branch, o Git apenas "avança" a `main` para apontar para o seu último commit. É limpo e linear.
        * [cite_start]**Merge Commit (3-way merge):** Se a `main` *também* teve mudanças, o Git cria um novo "commit de merge" especial que une os dois históricos[cite: 68].
* `git rebase <nome-da-branch-base>`
    * **O que faz:** (É uma alternativa ao `merge`). [cite_start]Ele reescreve o histórico da sua branch, colocando seus commits *depois* dos commits mais recentes da branch base[cite: 79]. [cite_start]Isso cria um histórico linear (sem "commit de merge")[cite: 80].
    * [cite_start]**Cuidado:** **Nunca** use `rebase` em branches que já foram compartilhadas/enviadas para o remoto (como a `main`), pois isso reescreve o histórico[cite: 80].

---

## 7. Guardando Mudanças Temporariamente (Stash)

Às vezes, você está no meio de uma alteração, mas precisa mudar de branch urgentemente (para corrigir um bug, por exemplo). Você não quer "commitar" um trabalho incompleto.

* `git stash`
    * **O que faz:** Salva temporariamente suas alterações modificadas (que não foram commitadas) em uma "pilha" (stash) e limpa seu diretório de trabalho.
* `git stash list`
    * **O que faz:** Mostra o que você guardou no stash.
* `git stash pop`
    * **O que faz:** Reaplica as últimas alterações que você guardou e as remove da pilha.
* `git stash apply`
    * **O que faz:** Reaplica as alterações, mas as mantém no stash (caso queira aplicar em outro lugar).

---

## 8. Analisando o Histórico

* `git log`
    * [cite_start]**O que faz:** Mostra o histórico completo de commits[cite: 105].
* `git log --oneline`
    * [cite_start]**O que faz:** Mostra um histórico resumido, com um commit por linha[cite: 106].
* `git log --graph --oneline --decorate`
    * [cite_start]**O que faz:** Versão muito útil que mostra o histórico com um gráfico ASCII das branches e merges[cite: 108].

---

## 9. Desfazendo Alterações

É normal cometer erros. O Git tem várias ferramentas para "voltar no tempo".

* `git restore <nome-do-arquivo>`
    * [cite_start]**O que faz:** Descarta alterações em um arquivo no seu diretório de trabalho (antes de `git add`)[cite: 113].
* `git restore --staged <nome-do-arquivo>`
    * [cite_start]**O que faz:** Tira um arquivo da "staging area" (desfaz um `git add`), mas mantém as alterações no arquivo[cite: 117]. [cite_start](O documento antigo usava `git reset HEAD <arquivo>`[cite: 35], mas `restore --staged` é o comando moderno).
* `git reset HEAD~1`
    * [cite_start]**O que faz:** Desfaz o último commit, mas **mantém** as alterações daquele commit na sua staging area e diretório de trabalho[cite: 120]. Útil se você "commitou" cedo demais.
* `git reset --hard HEAD~1`
    * [cite_start]**O que faz:** **CUIDADO!** Desfaz o último commit e **descarta permanentemente** todas as alterações associadas a ele[cite: 122, 123].
* `git revert <hash-do-commit>`
    * [cite_start]**O que faz:** Cria um **novo commit** que faz o exato oposto de um commit antigo[cite: 125]. [cite_start]É a forma mais segura de desfazer algo que já está no histórico remoto (no GitHub), pois não reescreve o histórico[cite: 126].

---

## 10. Ignorando Arquivos (.gitignore)

[cite_start]Você não quer "commitar" arquivos de log, dependências (como `node_modules/`) ou arquivos de configuração com senhas[cite: 139, 146, 152].

* [cite_start]**Como fazer:** Crie um arquivo chamado `.gitignore` na raiz do seu projeto[cite: 141].
* [cite_start]**O que colocar dentro:** Liste os arquivos ou pastas que o Git deve ignorar[cite: 141].
    * [cite_start]Exemplo: `*.log` [cite: 144][cite_start], `node_modules/` [cite: 147][cite_start], `.env`[cite: 152].

