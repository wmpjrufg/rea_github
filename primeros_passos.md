# 🚀 Guia Básico de Git e GitHub

Este guia é focado nos comandos essenciais para começar a usar o Git para controle de versão, seja em projetos locais ou colaborando no GitHub.

## 1. Configuração Inicial (Apenas uma vez)

Antes de tudo, você precisa se apresentar ao Git. Isso é usado para registrar quem fez cada alteração.

* `git config --global user.name "Seu Nome"`
    * **O que faz:** Define o nome de usuário que aparecerá nos seus commits.
* `git config --global user.email "seu.email@example.com"`
    * **O que faz:** Define o e-mail que aparecerá nos seus commits.
* `git config --list`
    * **O que faz:** Verifica todas as configurações ativas.

---

## 2. Como Começar um Repositório

Você pode começar um projeto do zero ou "baixar" um projeto que já existe em um local remoto (como o GitHub).

* `git init`
    * **O que faz:** Inicializa um repositório Git em um diretório que já existe. Ele cria uma pasta oculta `.git` para rastrear tudo.
* `git clone <url-do-repositorio>`
    * **O que faz:** Clona (baixa uma cópia completa) de um repositório remoto para a sua máquina local.

---

## 3. O Ciclo Básico (Seu Trabalho Local)

Este é o fluxo que você mais usará: modificar, adicionar e "commitar" (salvar) suas alterações.

* `git status`
    * **O que faz:** Mostra o estado atual do seu repositório. Informa quais arquivos foram modificados, quais estão prontos para commit (na "staging area") e quais não estão sendo rastreados.
* `git add <nome-do-arquivo>`
    * **O que faz:** Adiciona um arquivo específico à "staging area" (área de preparação), preparando-o para ser salvo no próximo commit.
* `git add .`
    * **O que faz:** Adiciona **todas** as alterações (arquivos novos e modificados) no diretório atual para a staging area.
* `git commit -m "Sua mensagem descritiva"`
    * **O que faz:** Salva permanentemente as alterações que estão na staging area no histórico do seu repositório.

### O que é um "Bom" Commit?

O comando é sempre `git commit`, mas a **mensagem** é crucial. Para novos usuários, o mais importante é que a mensagem seja **clara e descritiva**.

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

Branches (ramos) permitem que você trabalhe em novas funcionalidades ou correções sem afetar a linha principal de desenvolvimento (normalmente chamada de `main` ou `master`).

* `git branch`
    * **O que faz:** Lista todas as branches locais.
* `git branch <nome-da-nova-branch>`
    * **O que faz:** Cria uma nova branch , mas não muda para ela.
* `git checkout <nome-da-branch>` ou `git switch <nome-da-branch>`
    * **O que faz:** Muda para a branch especificada. `switch` é uma alternativa mais moderna.
* `git checkout -b <nome-da-nova-branch>` ou `git switch -c <nome-da-nova-branch>`
    * **O que faz:** Um atalho que **cria** e **muda** para a nova branch de uma só vez.
* `git branch -d <nome-da-branch>`
    * **O que faz:** Deleta uma branch local que já foi mesclada (integrada).

---

## 5. Sincronizando com o Remoto (GitHub)

Estes são os comandos para "atualizar" seu código, seja enviando suas mudanças ou recebendo as de outros.

* `git remote add origin <url-do-repositorio-remoto>`
    * **O que faz:** Adiciona um "apelido" (normalmente `origin`) para a URL do seu repositório remoto.
* `git push origin <nome-da-branch>`
    * **O que faz:** **Envia** seus commits locais para o repositório remoto (GitHub).
* `git fetch origin`
    * **O que faz:** **Baixa** as atualizações do repositório remoto, mas **não as aplica** (mescla) automaticamente no seu código local. Você pode ver o que mudou (ex: `origin/main`) sem afetar seu trabalho. Isso é muito útil para evitar conflitos inesperados.
* `git pull origin <nome-da-branch>`
    * **O que faz:** **Recebe** as atualizações do repositório remoto. É um atalho para fazer `git fetch` (baixar) e `git merge` (mesclar) de uma só vez.

**Qual usar para atualizar?**
* **`git pull`**: É o mais comum e direto. Baixa e tenta mesclar.
* **`git fetch`**: É mais "seguro". Você baixa, vê o que mudou, e então decide como e quando mesclar (usando `git merge origin/main`, por exemplo).

---

## 6. Integrando Mudanças (Merge e Rebase)

Quando você termina o trabalho em uma branch, você precisa integrá-lo de volta à branch principal (ex: `main`).

* `git merge <nome-da-branch-a-mesclar>`
    * **O que faz:** (Primeiro, esteja na branch que vai *receber* as mudanças, ex: `git checkout main`). Este comando integra o histórico da branch especificada na sua branch atual.
    * **Tipos de Merge:**
        * **Fast-Forward:** Se a `main` não teve nenhuma mudança enquanto você trabalhava na sua branch, o Git apenas "avança" a `main` para apontar para o seu último commit. É limpo e linear.
        * **Merge Commit (3-way merge):** Se a `main` *também* teve mudanças, o Git cria um novo "commit de merge" especial que une os dois históricos.
* `git rebase <nome-da-branch-base>`
    * **O que faz:** (É uma alternativa ao `merge`). Ele reescreve o histórico da sua branch, colocando seus commits *depois* dos commits mais recentes da branch base. Isso cria um histórico linear (sem "commit de merge").
    * **Cuidado:** **Nunca** use `rebase` em branches que já foram compartilhadas/enviadas para o remoto (como a `main`), pois isso reescreve o histórico.

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
    * **O que faz:** Mostra o histórico completo de commits.
* `git log --oneline`
    * **O que faz:** Mostra um histórico resumido, com um commit por linha.
* `git log --graph --oneline --decorate`
    * **O que faz:** Versão muito útil que mostra o histórico com um gráfico ASCII das branches e merges.

---

## 9. Desfazendo Alterações

É normal cometer erros. O Git tem várias ferramentas para "voltar no tempo".

* `git restore <nome-do-arquivo>`
    * **O que faz:** Descarta alterações em um arquivo no seu diretório de trabalho (antes de `git add`).
* `git restore --staged <nome-do-arquivo>`
    * **O que faz:** Tira um arquivo da "staging area" (desfaz um `git add`), mas mantém as alterações no arquivo. (O documento antigo usava `git reset HEAD <arquivo>`, mas `restore --staged` é o comando moderno).
* `git reset HEAD~1`
    * **O que faz:** Desfaz o último commit, mas **mantém** as alterações daquele commit na sua staging area e diretório de trabalho. Útil se você "commitou" cedo demais.
* `git reset --hard HEAD~1`
    * **O que faz:** **CUIDADO!** Desfaz o último commit e **descarta permanentemente** todas as alterações associadas a ele.
* `git revert <hash-do-commit>`
    * **O que faz:** Cria um **novo commit** que faz o exato oposto de um commit antigo. É a forma mais segura de desfazer algo que já está no histórico remoto (no GitHub), pois não reescreve o histórico.

---

## 10. Ignorando Arquivos (.gitignore)

Você não quer "commitar" arquivos de log, dependências (como `node_modules/`) ou arquivos de configuração com senhas.

* **Como fazer:** Crie um arquivo chamado `.gitignore` na raiz do seu projeto.
* **O que colocar dentro:** Liste os arquivos ou pastas que o Git deve ignorar.
    * Exemplo: `*.log` , `node_modules/` , `.env`.

