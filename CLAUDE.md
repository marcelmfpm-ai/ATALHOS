# Atalho iPhone

Página única (`index.html`) com atalhos para os projetos do Marcel, pensada para ser adicionada à Tela de Início do iPhone via Safari ("Adicionar à Tela de Início").

## Publicação

- Repositório remoto: `https://github.com/marcelmfpm-ai/ATALHOS`
- URL pública (GitHub Pages): `https://marcelmfpm-ai.github.io/ATALHOS/`
- Branch `main` é publicada diretamente pelo GitHub Pages — todo `git push` para `main` atualiza o site.

## Estrutura

- Título do app/página é "Atalhos" (`<title>`, `<h1>`, `apple-mobile-web-app-title`, `manifest.webmanifest`).
- Os atalhos são agrupados em seções (`<section>` dentro de `<main class="groups">`), cada uma com um círculo colorido (`.dot`) no título e uma borda colorida (`.group-cards` com `style="border-color:..."`, mesma cor do `.dot`) ao redor dos cards do grupo: **Aulas**, **Sistemas**, **Grades**, **Estudo**.
- Cada atalho é um `.card`: um `.cardlink` (abre o link em nova aba) + `.actions` com dois botões que não disparam navegação — 📋 copia o link, e um botão com o logo oficial do WhatsApp (SVG inline, verde `#25D366`) que abre o WhatsApp com o título e link prontos para compartilhar.
- No grupo **Sistemas**, todos os cards seguem o padrão visual "lupa sobre o que se busca": emoji principal no `.ic` + badge `.ic-badge` com 🔍 sobreposto (canto inferior direito), já que todos são sistemas de consulta.
- Botão "📄 Gerar Word com todos os links" baixa um `.doc` (HTML disfarçado de Word) com todos os cards. Botão "Compartilhar Word no WhatsApp" (verde) usa a Web Share API (`navigator.share` com `files`) para anexar esse mesmo arquivo direto na folha de compartilhar do iOS — só funciona em HTTPS (não em `file://`) e depende do WhatsApp estar registrado como destino de compartilhamento do sistema (funciona no iPhone; no Mac o WhatsApp Desktop não se registra nesse menu, então o botão cai no fallback de download). Ambos os botões chamam `buildWordBlob()`, que lê os `.card` da DOM dinamicamente — não precisa de manutenção ao adicionar atalhos novos.

## Adicionar um novo atalho

Duplicar um bloco `.card` dentro da seção correta (ou criar nova seção com `.group-header` + `.dot` + `.group-cards` com a cor correspondente), preenchendo: emoji/cor em `.ic`, título em `.t`, domínio amigável em `.u`, `href` no `.cardlink`, e `data-url`/`data-title` nos dois botões de `.actions`.

## Credenciais de login expostas nos cards

- O card "EPOL Treino" (grupo Sistemas) mostra login/senha em texto puro (`.meta .cred`) por decisão explícita do usuário, mesmo sabendo que o site é público (repositório e GitHub Pages públicos). Não remover essa informação sem confirmar de novo — e não replicar esse padrão em outros cards sem perguntar antes, dado o risco de exposição.

## Credenciais

- Push para o GitHub usa um Personal Access Token salvo no Keychain do macOS via `git credential approve` (helper `osxkeychain`). Não há token em texto no repo.
