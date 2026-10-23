# Oficina: Boas Práticas no GitHub

Semana de Informática DCOM 2026 · 100% no navegador, sem instalar nada

Bem-vindo! Hoje você vai fazer na prática o fluxo que times de desenvolvimento usam todos os dias: **branch → commit → pull request → code review → merge**. Siga este roteiro no seu ritmo, módulo por módulo.

---

## Antes de começar

- [ ] Use uma **janela normal** do navegador (não anônima).
- [ ] Faça login em [github.com](https://github.com) e confirme o 2FA no celular.
- [ ] Ficou sem conta ou sem 2FA? Avise o instrutor e sente com um colega como **copiloto**: vocês alternam quem digita a cada módulo.

### Regras da sala

1. **Travou? Chame o instrutor.**
2. **Checkpoint:** ao fim de cada módulo, comente na [issue de Check-in da turma](../../issues/1) a mensagem indicada (ex.: `M1 ok`).

### Onde cada coisa acontece

| Repositório | De quem | O que você faz nele |
| --- | --- | --- |
| `oficina-github-dcom` (este aqui) | Instrutor | Só **comenta** na issue de check-in. Nada de commit, fork ou PR aqui. |
| `oficina-github` | **Seu**, na sua conta | Quase toda a oficina: M1, M2, M3, M5. No M4, recebe a issue e o PR do colega. |
| `oficina-github` do colega | Seu colega de dupla | No M4: você abre uma issue e um PR nele. |
| Fork do repo do colega | Seu (cópia) | No M4: onde você faz a mudança antes do PR. |

---

## Check-in

Comente na [issue de Check-in](../../issues/1) com o seu nome completo:

```text
Seu Nome
```

---

## M1 — Primeiro repositório

1. Clique no **+** (canto superior direito) → **New repository**.
2. Preencha:
   - **Repository name:** `oficina-github`
   - **Visibility:** **Public** (necessário para o GitHub Pages e para proteger a branch no plano gratuito)
   - Marque **Add a README**
   - **.gitignore template:** `Node`
   - **License:** `MIT License`
3. Clique em **Create repository**.
4. Abra o `README.md`, clique no **lápis** e substitua o conteúdo por uma descrição do projeto (troque `Seu Nome` pelo seu nome):

   ```markdown
   # oficina-github

   Site pessoal criado na Oficina de GitHub da Semana de Informática DCOM 2026.

   ## Sobre o projeto
   Página de apresentação publicada com o GitHub Pages.

   ## Tecnologias
   - HTML
   - CSS

   ## Autor
   Seu Nome
   ```

   > 💡 O README é o **cartão de visitas do projeto**: diz o que ele é, com o que foi feito e quem o fez.
5. Clique em **Commit changes**, escreva a mensagem abaixo e confirme (commit direto na `main` só desta vez):

   ```text
   docs: descreve o projeto no README
   ```

6. Clique no ícone de relógio (**commits**) e abra o seu commit: veja o diff em verde e vermelho.

> 💡 **Mensagens de commit (Conventional Commits):** `feat:` nova funcionalidade · `fix:` correção · `docs:` documentação · `style:` visual/formatação · `chore:` manutenção.

**Desafio extra:** clique na engrenagem da seção **About** e preencha descrição e topics.

✅ **Checkpoint:** comente `M1 ok` + o link do seu repositório.

---

## M2 — Editor no navegador: github.dev

Você vai trabalhar com **duas abas**: uma no github.dev (para editar) e outra no github.com (para abrir o pull request).

1. Com o seu repositório `oficina-github` aberto, **duplique a aba**: clique com o botão direito na aba do navegador → **Duplicar**.
2. Na aba duplicada, troque **só** `github.com` por `github.dev` na barra de endereço e tecle Enter:

   ```text
   github.com/SEU-USUARIO/oficina-github   →   github.dev/SEU-USUARIO/oficina-github
   ```

3. Na barra inferior do editor, clique em **main** → **Create new branch** → `feat/pagina-inicial`.
4. Crie o arquivo `index.html`:

   ```html
   <!DOCTYPE html>
   <html lang="pt-BR">
   <head>
     <meta charset="UTF-8">
     <title>Meu primeiro site no GitHub</title>
     <link rel="stylesheet" href="style.css">
   </head>
   <body>
     <h1>Olá! Eu sou SEU NOME</h1>
     <p>Este site foi criado na Oficina de GitHub da Semana de Informática DCOM 2026.</p>
     <section>
       <h2>Sobre mim</h2>
       <p>Escreva aqui um pouco sobre você.</p>
     </section>
   </body>
   </html>
   ```

   ⚠️ Use `href="style.css"` **sem barra no início**, senão o estilo quebra no GitHub Pages.

5. Crie o arquivo `style.css`:

   ```css
   body {
     font-family: sans-serif;
     max-width: 720px;
     margin: 40px auto;
     padding: 0 16px;
     line-height: 1.6;
   }
   ```

6. No painel **Source Control** (ícone de ramificação, à esquerda): revise o diff dos dois arquivos, escreva a mensagem e clique em **Commit & Push**:

   ```text
   feat: adiciona página inicial
   ```

7. Volte para a **aba do github.com** e recarregue a página (**F5**). Clique no banner **Compare & pull request**, escreva uma descrição (o quê e por quê) e clique em **Create pull request**.
8. Clique em **Squash and merge** → **Confirm** → **Delete branch**.
9. **Publique seu site:** **Settings** → **Pages** → Source: **Deploy from a branch** → Branch: `main`, pasta `/ (root)` → **Save**.
10. Acompanhe na aba **Actions** (amarelo = publicando, verde = publicado). Em 1–2 minutos o site estará em:

    ```text
    https://SEU-USUARIO.github.io/oficina-github/
    ```

✅ **Checkpoint:** comente `M2 ok` + o link do seu site.

---

## M3 — Conflito de merge pelo navegador

Você vai **provocar** um conflito e resolvê-lo.

1. No seu repositório, clique no seletor de branch (botão **main**), digite `docs/titulo` e clique em **Create branch docs/titulo from main**.
2. Ainda no branch `docs/titulo`, edite a **linha 1** do `README.md` pelo lápis:

   ```markdown
   # Oficina GitHub - versao do branch
   ```

   Commit: `docs: altera titulo no branch`
3. Volte para a **main** e edite a **mesma linha 1** com outro texto:

   ```markdown
   # Oficina GitHub - versao da main
   ```

   Commit direto na `main` (de propósito, para causar o conflito).
4. Abra um pull request de `docs/titulo` para `main`. O GitHub vai avisar que há conflito.
5. Clique em **Resolve conflicts**. Apague as três linhas de marcadores (`<<<<<<<`, `=======`, `>>>>>>>`), deixe o texto final que você quiser, clique em **Mark as resolved** e **Commit merge**.
6. Faça o merge do PR e confira o histórico de commits.

> 💡 Conflito não é erro: é o Git pedindo uma decisão humana. PRs pequenos e frequentes evitam conflitos.

✅ **Checkpoint:** comente `M3 ok` + o link do PR com o conflito resolvido.

---

## M4 — Colaboração em dupla

Você terá **dois papéis ao mesmo tempo**:
- **Contribuidor** no repositório do seu colega;
- **Mantenedor** do seu próprio repositório.

### Como contribuidor

1. **Issue:** no repositório `oficina-github` do colega → aba **Issues** → **New issue**. Escolha uma sugestão da tabela abaixo e use o modelo. Anote o número da issue (ex.: `#3`).
2. **Fork:** no repositório do colega, clique em **Fork** → **Create fork**.
3. **Mudança:** duplique a aba do seu fork e, na cópia, troque `github.com` por `github.dev` (como no M2). Crie o branch `feat/contato`, faça a alteração e clique em **Commit & Push**.
4. **Pull request:** na aba do fork no github.com, recarregue (**F5**) e clique no banner **Compare & pull request** (ou selecione o branch `feat/contato` e clique em **Contribute → Open pull request**). Confira se o destino é a `main` **do colega**. Na descrição, escreva:

   ```text
   Closes #3
   ```

   (troque `3` pelo número da sua issue)
5. **Ajuste:** quando o colega pedir mudanças, edite no mesmo branch `feat/contato` do seu fork. O PR se atualiza sozinho.

### Como mantenedor

1. No seu repositório → aba **Pull requests** → abra o PR do colega → **Files changed**.
2. Clique no **+** ao lado de uma linha e deixe um comentário construtivo.
3. Finalize em **Review changes → Request changes**.
4. Depois do ajuste: **Review changes → Approve** → **Squash and merge**.
5. Confira: a issue fechou sozinha? Em 1–2 minutos, a mudança apareceu no seu site do Pages?

### Sugestões de issues

| # | Título da issue | Arquivo |
| --- | --- | --- |
| 1 | Adicionar seção "Contato" com link para o perfil do GitHub | `index.html` |
| 2 | Adicionar lista "Tecnologias que estou estudando" | `index.html` |
| 3 | Exibir a foto do perfil com texto alternativo | `index.html` |
| 4 | Adicionar rodapé com o ano e link para o repositório | `index.html` |
| 5 | Melhorar o `<title>` e incluir `<meta name="description">` | `index.html` |
| 6 | Trocar a cor de fundo e a fonte da página | `style.css` |
| 7 | Adicionar no README uma seção "Como ver o site" com o link do Pages | `README.md` |

Dica para a sugestão 3: `<img src="https://github.com/USUARIO.png" alt="Foto de USUARIO" width="120">`

### Modelo de issue

```markdown
## O que
Adicionar uma seção "Contato" na página inicial.

## Por que
Visitantes do site não têm como encontrar o autor.

## Critério de aceite
- [ ] A seção aparece no fim da página
- [ ] Tem link para o perfil do GitHub
```

> 💡 **Code review é sobre o código, nunca sobre a pessoa.** Prefira "sugiro…", "o que acha de…?", "por que não…?".

**Desafio extra:** no review, use o botão **Suggest changes** (ícone ±) para propor o código exato. O contribuidor aceita com **Commit suggestion**.

✅ **Checkpoint:** comente `M4 ok` + o link do PR mergeado.

---

## M5 — Proteger a main

1. No seu repositório: **Settings** → **Rules** → **Rulesets** → **New ruleset** → **New branch ruleset**.
2. Configure:
   - **Ruleset name:** `protege-main`
   - **Enforcement status:** **Active**
   - **Target branches:** **Add target** → **Include default branch**
3. Marque:
   - **Restrict deletions**
   - **Block force pushes**
   - **Require a pull request before merging**, com **Required approvals = 0** (assim você ainda consegue mergear seus próprios PRs)
4. Deixe a **Bypass list** vazia e clique em **Create**.
5. **Teste:** abra o `README.md` na `main` e clique no lápis. Ao salvar, o GitHub não deixa commitar direto na `main` e oferece criar um branch e abrir PR.

> 💡 Boa prática não depende de disciplina: a regra fica no repositório.

✅ **Checkpoint:** comente `M5 ok`.

---

## Encerramento

- [ ] Deixe um feedback de uma linha na [issue de Check-in](../../issues/1).
- [ ] **Faça logout do GitHub** (foto do perfil → **Sign out**). O computador é compartilhado!
- [ ] Feche o navegador.

---

## Cola rápida

### Quando algo não funciona

| Problema | Solução |
| --- | --- |
| O github.dev não abre | Confira se trocou exatamente `github.com` por `github.dev` e se está logado. Use janela normal, não anônima. |
| Não aparece o banner **Compare & pull request** | Recarregue a aba do github.com (**F5**). Ou abra a aba **Pull requests** → **New pull request**. |
| O site do Pages dá erro 404 | Espere a execução ficar verde na aba **Actions**. Confira se o `index.html` está na raiz da `main`. |
| O site não mostra minha mudança | A mudança só entra no ar depois do merge na `main`. Recarregue com **Ctrl + F5**. |
| O CSS não aparece no site | Use `href="style.css"`, sem barra no início. |
| Opção Pages pede upgrade | O repositório precisa ser **Public**: **Settings → General → Change visibility**. |
| Erro ao fazer Commit & Push no github.dev | Aguarde alguns minutos e tente de novo (limite temporário da API). |

### Glossário

| Termo | Significado |
| --- | --- |
| **Repositório** | Pasta do projeto com todo o histórico de mudanças. |
| **Commit** | Uma "foto" do projeto, com autor, data e mensagem. |
| **Branch** | Linha de trabalho paralela; a `main` é a principal. |
| **Pull request (PR)** | Pedido para levar as mudanças de um branch para outro, com conversa e revisão. |
| **Merge** | Juntar as mudanças de um branch em outro. |
| **Fork** | Cópia do repositório de outra pessoa na sua conta. |
| **Issue** | Registro de uma tarefa, melhoria ou bug. |
| **Code review** | Revisão do código por outra pessoa antes do merge. |

---

## Para continuar aprendendo

- **GitHub Codespaces — experimente!** É um ambiente de desenvolvimento completo na nuvem, com terminal Linux e Git prontos, aberto direto no navegador. No seu repositório: **Code** → aba **Codespaces** → **Create codespace on main**. No terminal, pratique `git status`, `git add`, `git commit` e `git push`. Contas gratuitas têm uma cota mensal (60 horas por mês numa máquina de 2 núcleos). Quando terminar, pare ou exclua o codespace em [github.com/codespaces](https://github.com/codespaces) para não gastar a cota.
- [GitHub Skills](https://learn.github.com/skills): cursos gratuitos e interativos, feitos dentro do próprio GitHub.
- [GitHub Student Developer Pack](https://education.github.com/pack): benefícios gratuitos para quem tem vínculo estudantil verificado, incluindo o GitHub Pro e mais uso do Codespaces.
- **README de perfil:** crie um repositório **público** com o mesmo nome do seu usuário e escreva um `README.md`. Ele aparece no topo da sua página de perfil.

Bom código! 🚀
