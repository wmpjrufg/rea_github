# Alterando ou revertendo commits 

## Comando: --amend

`--amend` é um comando utilizado para sobrescrever as alterações no commit atual, seja adicionar ou alterar um arquivo já existente ou apenas modificar a descrição do commit atual.

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

ao utilizar a flag `--amend` após o `git commit`, o git entende que deseja alterar o commit já realizado, não criar um novo commit.

## Comando: reset

`reset` é o comando utilizado para resetar o estado atual a um estado anterior, com objetivo de desfazer modificações incorretas.

Para resetar o estado do commit a um anterior e manter as alterações locais da mesma maneira:
```bash
git reset HEAD^1
```
sendo resetado para o commit imediatamente anterior, caso queira resetar para 2 commits atrás:
```bash
git reset HEAD^2
```
e assim por diante, caso queira resetar através do id do commit:
```bash
git log --oneline
git reset [ID_DO_COMMIT]
```

Para resetar o estado do commit e desfazer as alterações locais ou seja vincular o codigo local ao estado do commit a ser resetado utilize a flag `--hard`:
```bash
git reset --hard HEAD^[N]
OU
git reset --hard [ID_DO_COMMIT]
```

## Comando: revert
`revert` é o comando de reversão mais seguro. Diferentemente do `reset` o `revert` cria um novo commit e copia o estado anterior escolhido para esse novo commit, mantendo o commit atual e criando um novo com o estado anterior.

```bash
git revert HEAD^[N]
OU
git revert [ID_DO_COMMIT]
```


