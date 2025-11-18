# Configurações gerais  

Após fazer o *download* e instalação das aplicações precisamos configurar nosso Git na máquina.

Este passo é fundamental, já que a ferramenta de versionamento precisa reconhecer a máquina e o autor das alterações que serão posteriormente agregadas ao repositório remoto.

Este passo pode ser feito de duas formas diferentes, sendo uma configuração global, ou seja, válida para qualquer repositório que está na máquina ou de forma individual. Inicialmente vamos configurar apenas duas informações, que já serão suficiente para prosseguirmos com nosso curso.

Vamos aplicar as modificações globais e estas aparecerão no histórico do Git. Para isso devemos digitar o seguinte comando:

> **Nota**
> Neste curso utilizaremos como padrão de editável da sintaxe do comando a tag `< >`. Ou seja, tudo que for editável pelo usuário será expresso dentro do símbolo `< >`.

```bash
git config --global user.name "meu_nome"
```
  
### _Exemplo_
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
  
Pronto nosso ambiente Git já está configurado e preparado para o uso. Para verificar as credenciais utilize o comando `git config --list`.  