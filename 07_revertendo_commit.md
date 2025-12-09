# Alterando ou revertendo commits 

## Comando: --amend

--amend é um comando utilizado para sobrescrever as alterações no commit atual, seja adicionar ou alterar um arquivo já existente ou apenas modificar a descrição do commit atual.

Para modificar a descrição:
```bash
git commit --amend -m "nova descricao"
```

Para sobrescrever as alterações em arquivos:
```bash
git add .
git commit --amend -m "sobrescrevendo commit"
```
```bash
git commit --amend --no-edit
```

ao utilizar a flag '--amend' após o `git commit`, o git entende que deseja alterar o commit já realizado, não criar um novo commit.

## Comando: reset
