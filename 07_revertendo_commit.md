# Alterando ou revertendo commits 

## Comando |--amend|

--amend é um comando utilizado para sobrescrever as alterações no commit atual, seja adicionar ou alterar um arquivo já existente ou apenas modificar a descrição do commit atual.

Para apenas mudar a descrição:
```bash
git commit --amend -m "nova descricao"
```


Para sobrescrever as alteraçoes em arquivos:
```bash
git add .
git commit --amend -m "sobrescrevendo commit"
OU
git commit --amend --no-edit
```
