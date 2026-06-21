# Atalho iPhone

Página única (`index.html`) com atalhos para os projetos do Marcel, pensada para ser adicionada à Tela de Início do iPhone via Safari ("Adicionar à Tela de Início").

## Publicação

- Repositório remoto: `https://github.com/marcelmfpm-ai/ATALHOS`
- URL pública (GitHub Pages): `https://marcelmfpm-ai.github.io/ATALHOS/`
- Branch `main` é publicada diretamente pelo GitHub Pages — todo `git push` para `main` atualiza o site.

## Estrutura

- Os atalhos são agrupados em seções (`<section>` dentro de `<main class="groups">`), cada uma com um círculo colorido (`.dot`) e título: **Aulas**, **Sistemas**, **Grades**, **Estudo**.
- Cada atalho é um `.card`: um `.cardlink` (abre o link em nova aba) + `.actions` com dois botões que não disparam navegação — 📋 copia o link, 📤 abre o WhatsApp com o título e link prontos para compartilhar.
- Botão "📄 Gerar Word com todos os links" no fim da página lê todos os `.card` da DOM dinamicamente e gera um `.doc` (HTML disfarçado de Word) para download — não precisa de manutenção ao adicionar atalhos novos.

## Adicionar um novo atalho

Duplicar um bloco `.card` dentro da seção correta (ou criar nova seção com `.group-header` + `.dot`), preenchendo: emoji/cor em `.ic`, título em `.t`, domínio amigável em `.u`, `href` no `.cardlink`, e `data-url`/`data-title` nos dois botões de `.actions`.

## Credenciais

- Push para o GitHub usa um Personal Access Token salvo no Keychain do macOS via `git credential approve` (helper `osxkeychain`). Não há token em texto no repo.
