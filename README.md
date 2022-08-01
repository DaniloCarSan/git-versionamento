# VERSIONAMENTO

**main** - Contém a versão mais estável;

**dev** - Contém a versão de desenvolvimento onde se encontram as alterações que estarão na proxima versão;

**release** - ex:(v1.1.0) Contém a versão final do proximo lançamento.

**hotfix** - Contem a versão de correção urgentes

**bugfix** - Contem versão de correção de bugs que estarão na proxima versão

**feature** - Contem uma funcionalidade especifica para lançamento/teste/POC/MVP

**OBS: Estou pressupondo que já tenha uma conta no github e o git em seu coputador já esteja configurado**

## 1 - FLUXO: CRIAR RESPOSITÓRIO LOCAL E SINCRONIZAR COM O ONLINE

**1-** Criar um pasta e iniciar seu repositório
````
mkdir my-project-git
cd my-project-git
git init
````

**2-** Acessar o github e criar um repositrorio

**3-** Na pagina do seu repositório recem criado pegar os comandos e executar na pasta raiz de seu repositório
````
echo "# my-project-git" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/danilocarreiro/my-project-git.git
git push -u origin main
````

**4-** Criar um branch **dev** para o desenvolvimentos das funcionalidades e sincronizar com o repositório online
````
git branch dev
git checkout dev
git push origin dev
````

## 2 - FLUXO: Criar uma nova funcionalidade

**1-** Criar uma branch para a nova funcionalidade
````
git checkout dev
git branch feature-xyz
git checkout feature-xyz
git push -u origin feature-xyz
````

**2-** Desenvolver a nova funcionalidade e sincronizar alterações com o repositorio online
````
git add -A
git commit -m "create feature-xyz"
git push -u origin feature-xyz
````

**3-** Criar uma pull request pela interface do github para branch **dev** para nova funcionalidade ser incluída na proxima versão

**4-** Revisar a pull request e realizar o merge com a **dev** depois excluir(local/online) a branch da feature

**5-** Baixar a novas alterações da branch dev
````
git checkout dev
git pull -u origin dev
````

## 3 - FLUXO: Lançamento de uma nova realease

**1-** Criar uma branch com a versão final e realizar os testes e alterações minimas, então sincronizar a branch com o repositorio online
````
git checkout dev
git branch v1.0.0
git checkout v1.0.0
git push origin v1.0.0
````

**2-** Criar uma pull request pela interface do github para branch **main**

**3-** Revisar a pull request e realizar o merge na **main**

**4-** Criar a realease e tag de lançamento na branch **main**

**5-** Baixar a novas alterações na branch **main**
````
git checkout main
git fetch --all
git pull origin main
````
**5-** Realizar o merge com a branch **dev** e sincronizar as alterações
````
git merge main
git push origin dev
git pull origin dev
````

## 4 - FLUXO: Criar uma realease hotfix

**1-** Criar um branch a partir da branch **main**
````
git branch v1.0.1-hotfix
git checkout v1.0.1-hotfix
git push -u origin v1.0.1-hotfix
````

**2-** Realizar alterações e sincronizar
**3-** Seguir o fluxo de lançamento de uma nova realease

## 5 - FLUXO: Criar uma realease bugfix

**1-** Criar um branch a partir da branch **dev**
````
git branch bugfix-issue-2948
git checkout bugfix-issue-2948
git push -u origin bugfix-issue-2948
````
**2-** Realizar alterações e sincronizar

**3-** Seguir o fluxo de criação de uma funcionalidade

### FONTES

https://blog.ateliedocodigo.com.br/fluxo-de-versionamento-de-software-com-git-flow-b9f5195c679e?gi=f006620934d1

https://nvie.com/posts/a-successful-git-branching-model/

https://docs.github.com/pt/get-started/quickstart/github-flow
