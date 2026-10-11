# Vitrine CPS — protótipo v1 (estático)

Duas páginas de referência visual para o grupo aprovar antes de ir para o Django:

- `index.html` — página inicial (vitrinecps.com.br)
- `projeto.html` — página pública de um projeto (/projeto/<slug>/), com projeto de exemplo
- `fachada.webp` — fachada da Fatec tratada (P&B + placa vermelha, fundo transparente)

Tudo é exemplo: projetos, capas, nomes e textos de impacto. Links para rotas do sistema
(/grupo/, /como-votar/) estão desativados aqui e anotados no `title`.

## Publicar (Coolify, serviço estático)

1. Suba esta pasta num repositório (ex.: `vitrine-cps-prototipo`) ou aponte o Coolify para ela.
2. Coolify → New resource → Public/Private repository → build pack **Static** (raiz com `index.html`).
3. Domains: `https://prototipo.vitrinecps.com.br`.
4. Cloudflare Zero Trust → túnel → Public Hostname `prototipo.vitrinecps.com.br` → mesmo service dos outros apps.

As páginas têm `noindex`. Para desligar, apague o recurso no Coolify e o hostname no túnel.

## Porte para o Django (depois da aprovação)

- `:root` e regras de `<style>` de `index.html` → `static/css/base.css` (tokens + componentes;
  renomear `--azul` para `--cor-acento`; posições dos quadrados viram classes, sem `style=`).
- `<header class="topo">`, `<footer class="rodape">` → `templates/base.html` (bloco `nav` sobrescrevível).
- Hero + seções da home → view `vitrine:inicio` (nova rota `/`), projetos agrupados por `Turma`.
- `projeto.html` → `vitrine/templates/vitrine/projeto.html` + `_corpo_projeto.html`
  (área do projeto em `div.area-projeto`; tema por projeto é proposta para a próxima edição).
- Seção "Impacto": decidir entre campos novos (`impacto_social`, `impacto_ambiental`) ou convenção na `descricao`.
