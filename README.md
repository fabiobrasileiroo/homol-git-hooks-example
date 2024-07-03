# post-commit

Este gancho é invocado por git-commit[1] . Não requer parâmetros e é invocado após um commit ser feito.
Este gancho destina-se principalmente à notificação e não pode afetar o resultado de git commit.

## Exemplo

``` bash
#!/bin/bash

# Defina os repositórios de homologação e produção
HOMOLOG_REPO_URL="git@github.com:fabiobrasileiroo/homol-git-hooks-example.git"
PROD_REPO_URL="git@github.com:fabiobrasileiroo/prod-git-hooks-example.git"

# Defina a branch que será usada para os pushes
BRANCH="dev"

# Realize o pull do repositório de produção para garantir que está atualizado
git pull $PROD_REPO_URL $BRANCH --allow-unrelated-histories

# Realize o push para o repositório de homologação
git push $HOMOLOG_REPO_URL $BRANCH

# Realize o push para o repositório de produção
git push $PROD_REPO_URL $BRANCH

# Informe que o hook foi executado com sucesso
echo "Commit enviado para os repositórios de homologação e produção."
```
