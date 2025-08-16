# Aprendendo Git e Github
Um guia geral de `Git e Github` para pessoas iniciantes que desejam trabalhar em equipe.\
Foi dividido nos seguintes tópicos:
- [Conceitos Fundamentais](#conceitos-fundamentais)
- [Comandos Essenciais](#comandos-essenciais)
- [Tipos de Commit](#tipos-de-commit)
- [Fluxo de Trabalho (Passo a Passo)](#fluxo-de-trabalho-passo-a-passo)
- [Resolvendo Issues (tarefas)](#resolvendo-issues-tarefas)

## Conceitos Fundamentais
- `Git:` É o programa no seu computador que gerencia o histórico do seu projeto. É como o sistema de "Save Points" do jogo. Ele funciona offline, na sua máquina.

- `GitHub:` É a plataforma online (o site) onde você "sobe" seu projeto para guardar uma cópia de segurança e para que seu colega possa acessá-lo. É o "servidor na nuvem" do jogo.

- `Repositório (Repo):` É a pasta do seu projeto. Contém todos os seus arquivos de código (.c, .h) e o histórico de alterações (uma pasta oculta .git).

- `Clone:` É o ato de baixar o repositório do GitHub pela primeira vez para a sua máquina. É "instalar o jogo".

- `Commit:` É um "Save Point". Uma fotografia do seu código em um momento específico, guardada com uma mensagem que descreve o que você fez.

- `Branch:` É uma linha do tempo paralela de desenvolvimento.

- ` main:` A linha do tempo principal, a versão oficial e estável do seu projeto. Deve estar sempre funcionando.

- `Branch de Feature (ex: feat/menu-principal):` Uma linha do tempo temporária que você cria para trabalhar em uma nova funcionalidade sem bagunçar a main. É o seu "rascunho".

- `Merge:` É o ato de juntar o histórico de uma branch em outra. É quando seu rascunho (sua branch de feature) é aprovado e se torna parte da história oficial (a main).

- `Pull Request (PR):` Um pedido formal no site do GitHub para fazer um "merge". É o momento em que você apresenta seu trabalho para seu colega e pede uma revisão do código antes de integrá-lo à main.

- `Conflito:` Acontece quando você e seu colega alteram a mesma linha de um mesmo arquivo. O Git não sabe qual versão escolher e pede sua ajuda para resolver a "briga".

## Comandos Essenciais

|Comando	                               |O que faz
|----------------------------------------|------------------------------------------------------------------------------------------------------------------
|`git init`	                             |Cria um repositório Git novo e vazio na sua máquina. Ele não tem **nenhuma conexão remota**                      |
|`git remote add origin <URL>`	         |Adiciona uma conexão remota com o repositório                                                                    |
|`git clone <URL>`	                     |Baixa um repositório do GitHub pela primeira vez e configura a conexão remota (origin) para você automaticamente.|
|`git status`	                           |Mostra o status dos seus arquivos (modificados, novos, etc.).                                                    |
|`git add .`	                           |Prepara todas as suas alterações para serem salvas no próximo commit.                                            |
|`git commit -m "tipo: mensagem"`        |Cria o "Save Point" com uma mensagem descritiva.                                                                 |
|`git pull`	                             |Baixa e mescla as atualizações do GitHub na sua branch atual.                                                    |
|`git push`	                             |Envia seus commits para o GitHub.                                                                                |
|`git checkout <nome-da-branch>`	       |Muda para outra branch que já existe.                                                                            |
|`git checkout -b <nome-da-nova-branch>` |Cria uma nova branch e já muda para ela.                                                                         |
|`git fetch`                             |Baixa as "novidades" do GitHub, mas não aplica (só atualiza seu "mapa").                                         |
|`git branch`	                           |Lista todas as branches que você tem localmente.                                                                 |

## Tipos de Commit
- `feat:` (Feature) Usado quando você adiciona uma nova funcionalidade ao programa.

- `fix:` (Bug Fix) Usado quando você corrige um erro (bug).

- `docs:` (Documentation) Usado para mudanças na documentação (comentários no código, o arquivo README.md, etc.).

- `style:` (Styling) Usado para mudanças que não afetam a lógica, como formatação, indentação, espaços em branco, ponto e vírgula, etc.

- `refactor:` (Refactoring) Usado para melhorias no código que não adicionam uma funcionalidade nem corrigem um bug. Ex: renomear uma variável para ser mais clara, ou dividir uma função grande em duas menores.

- `chore:` (Chores) Usado para tarefas de manutenção, como atualizar arquivos de configuração, scripts de compilação, etc. (Menos comum para um projeto simples em C, mas bom conhecer).

## Fluxo de Trabalho (Passo a Passo)
Este é o roteiro que deve ser seguido para cada nova funcionalidade ou correção. Exemplo: "Criar a funcionalidade de buscar receita".

### Etapa 1: Preparação
**1.** **_Garanta que sua main está atualizada (Sincronizar):_**
```
git checkout main
git pull
```
> Sempre comece um novo trabalho a partir da versão mais recente da `main`.

**2.** _**Crie sua branch de trabalho (Isolamento):**_
```
git checkout -b feat/buscar-receita
```
> Agora você está em um ambiente seguro para trabalhar sem afetar o projeto principal.

### Etapa 2: Desenvolvimento

**3.** **Escreva seu código:** Crie ou modifique os arquivos .c e .h necessários para a busca funcionar.

**4.** **Salve seu progresso (Commits):** Faça commits pequenos e lógicos.

`Primeiro commit:` _Adicionou a função de busca_
```
git add .
git commit -m "feat: implementa a lógica de busca de receita por nome"
```

`Segundo commit:` _Integrou ao menu_ (mais código)
```
git add .
git commit -m "feat: adiciona a opção de busca ao menu principal"
```

### Etapa 3: Colaboração e Revisão

**5.** **_Envie sua branch para o GitHub (Compartilhar):_**

```
git push -u origin feat/buscar-receita
```

> O `-u` só é necessário na **primeira vez** que você envia a branch.

**6.** **_Abra o Pull Request (PR):_**

- Vá ao site do <ins>GitHub</ins>.

- Clique no botão verde *"Compare & pull request"*.

- Dê um **_título claro, descreva o que você fez_** e designe seu colega como revisor (Reviewer).

**7.** Revisão de Código (Trabalho em Equipe):

- Seu colega irá revisar o código no GitHub.

- Se houver pedidos de alteração: *Volte para o Passo 3*. Faça as alterações, crie novos commits e dê git push novamente. O PR será atualizado automaticamente.

- Se estiver tudo OK: Seu colega vai "Aprovar" o PR e a branch vai fazer parte da main.

### Etapa 4: Limpeza (Organização)

- No GitHub: Clique no botão para deletar a branch remota.

- No seu computador: Volte para a main, puxe as atualizações (que agora incluem seu próprio trabalho) e apague a branch local.
```
git checkout main
git pull
git branch -d feat/buscar-receita
```
> O ciclo recomeça para a próxima tarefa!

## Resolvendo Issues (tarefas)
Issues são usadas para rastrear qualquer tipo de tarefa, ideia, melhoria ou bug.

### As principais vantagens de usar Issues:

- **Organização Centralizada:** Em vez de decidirem tarefas pelo WhatsApp ou de cabeça, tudo fica registrado em um único lugar. Fica claro para a equipe o que precisa ser feito.

- **Definição de Responsabilidade:** Cada Issue pode ser atribuída a uma pessoa. Fica claro quem está trabalhando em quê, evitando que façam a mesma coisa.

- **Histórico e Discussão:** Toda a conversa sobre uma tarefa (dúvidas, sugestões) fica dentro da própria Issue, servindo como um registro de como as decisões foram tomadas.

- **Conexão com o Código:** Esta é a parte mais poderosa. Você pode **_ligar uma Issue diretamente a branches, commits e Pull Requests_**, criando um rastro completo desde a ideia até a implementação.

### Como criar uma Issue

**Passo 1:** Acessando a Área de Issues
- No seu repositório no GitHub, clique na aba "Issues", que fica ao lado de "Code" e "Pull Requests".

**Passo 2:** Criando uma Nova Issue
- Clique no botão verde "New issue".

- Você verá dois campos principais: Título e Descrição.

**Título:** Deve ser um resumo claro e direto da tarefa.
- Exemplo ruim: função

- Exemplo bom: Implementar a função para editar uma receita existente

**A Descrição:** Aqui você detalha a tarefa. 
- Use o formato Markdown para organizar. Uma ótima prática é criar uma lista de subtarefas (checklist).

Template de Descrição que vocês podem usar:

```Markdown
## Descrição
Precisamos criar a funcionalidade que permita ao usuário editar os dados de uma receita que já foi cadastrada. O usuário deve primeiro buscar a receita pelo ID.

## Tarefas a Fazer
- [ ] Criar uma função `buscarReceitaPorId(id)`.
- [ ] Criar um submenu de edição (ex: "O que você quer editar? 1-Nome, 2-Ingredientes...").
- [ ] Implementar a lógica para alterar o nome da receita.
- [ ] Implementar a lógica para alterar a lista de ingredientes.
- [ ] Adicionar a opção "Editar Receita" no menu principal.
```

**Passo 3:** Ferramentas da Barra Lateral

- Assignees (Responsáveis): Clique aqui e escolha quem da dupla será o responsável por esta tarefa. A foto da pessoa aparecerá na Issue.

- Labels (Etiquetas): São etiquetas coloridas para categorizar suas tarefas. É MUITO útil para organizar. 

Quando tudo estiver preenchido, clique em **_"Submit new issue"_**.

### Resolvendo Issues

Cenário: Você (ou seu colega) acabou de criar a Issue #5: "Implementar a função de editar receita" e atribuiu a você.

- **Crie uma Branch a partir da Issue:** Ao criar sua branch, inclua o número da Issue no nome. Isso liga a branch à Issue automaticamente no GitHub.

```
git checkout -b feat/5-editar-receita
```
> O "5" é o número da Issue

- **Faça seus Commits:** Trabalhe no código e faça seus commits normalmente.

```
git commit -m "feat: adiciona a função buscarReceitaPorId (#5)"
```
>(Dica: mencionar (#5) no commit também cria um link para a Issue)

- **Abra o Pull Request:** Quando terminar, envie sua branch (git push) e abra um Pull Request. Na descrição do PR, use uma palavra-chave mágica como **_Closes, Fixes ou Resolves_**.

Exemplo de descrição do PR:

```Markdown
Este PR implementa a funcionalidade completa de edição de receitas.

Closes #5
```
**O que acontece?**

- O PR ficará vinculado à Issue #5.

- Quando este Pull Request for revisado, aprovado e sofrer merge na branch main, o GitHub automaticamente **fechará a Issue #5** para você!

> Este fluxo de trabalho (`Issue` -> `Branch` -> `Commits` -> `Pull Request` -> `Merge` e `Fechamento Automático da Issue`) cria um sistema perfeitamente rastreável, onde qualquer pessoa pode ver a ideia original (na Issue), acompanhar o desenvolvimento (na branch e nos commits) e ver a revisão final (no PR).