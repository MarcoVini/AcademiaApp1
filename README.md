# Treino — PWA pessoal

Primeira versão de um diário de treino para celular. Feito em HTML, CSS e JavaScript, sem dependências ou backend.

## O que já tem
- Dois perfis locais
- Treinos Full Body A/B, com alternância automática após concluir a sessão
- Registro de carga, repetições e RIR por série
- Adicionar séries e exercícios
- Cronômetro de descanso de 60, 90 e 120 segundos
- Histórico de treinos
- Exportar/importar backup JSON
- Armazenamento local e cache básico para uso offline

## Como testar
Abra `index.html` no navegador para testar as funções básicas. O modo PWA instalável/offline exige hospedar os arquivos em HTTPS (por exemplo, GitHub Pages).

## Publicar gratuitamente no GitHub Pages
1. Entre em https://github.com e crie um repositório público chamado `treino-pwa`.
2. Envie os arquivos `index.html`, `manifest.json` e `sw.js` para a raiz do repositório.
3. Vá a Settings → Pages.
4. Em Build and deployment, escolha Deploy from a branch; selecione `main` e `/ (root)`; salve.
5. Aguarde a URL publicada. No Android, abra a URL no Chrome → menu ⋮ → “Adicionar à tela inicial” ou “Instalar app”.

## Importante
- Os dados ficam no armazenamento do navegador, no próprio aparelho. Limpar os dados do site pode apagar o histórico.
- Exporte backups periodicamente. O backup inclui os dois perfis e o histórico.
- O treino inicial é ilustrativo; ajuste os exercícios à sua ficha real.
- Este protótipo não sincroniza dados entre aparelhos.


## Atualização automática
O service worker foi atualizado para a versão `treino-pwa-v2`. Depois de publicar os arquivos na raiz do GitHub Pages, o app verifica atualizações ao abrir e quando volta para primeiro plano. Páginas HTML priorizam a versão online e usam o cache se estiver sem conexão. O histórico de treinos continua salvo no `localStorage` do navegador.


## Novidades: fichas personalizadas e alternativas
- Crie fichas com nomes próprios, além de Full Body A/B.
- Os treinos personalizados entram na rotação de próximos treinos.
- Cada exercício tem um botão de alternativas com sugestões por padrão de movimento/músculos.
- A substituição altera o exercício na ficha, mantendo a quantidade de séries.
- Dados antigos em localStorage são migrados na leitura; não apague os dados do navegador.
- Faça backup antes de publicar.


## Catálogo de exercícios
O formulário de exercícios agora inclui catálogo local pesquisável, filtro por grupo muscular e opção explícita de cadastrar um nome personalizado quando não encontrar um exercício. O catálogo funciona sem internet e sem serviços externos.


Versão v6: exclusão de fichas personalizadas (A/B protegidas, histórico concluído preservado) e busca integrada ao catálogo na mesma lista de opções.


## Redesign visual (v7)
- Tela inicial com resumo de frequência mensal/semanal, gráfico dos últimos 7 dias, próximo treino e atividade recente.
- Navegação inferior com Início, Treino, Histórico e Ajustes.
- Tema dark modernizado com verde-lima como destaque e componentes mais espaçados.
- Mantém os dados locais, as fichas A/B e personalizadas, catálogo, timer, histórico e backup.
- Ao publicar esta versão, substitua os arquivos da raiz do repositório pelo conteúdo desta pasta. Faça backup dos dados antes de atualizar.


## Redesign v9 — cartões recolhíveis e transições
- Os exercícios aparecem em cartões recolhíveis; o primeiro começa aberto e os demais ficam compactos.
- O resumo mostra quantidade de séries, séries concluídas e a última carga/repetição preenchida no treino atual.
- Abrir outro exercício recolhe o anterior; é possível deixar todos recolhidos.
- Animações curtas de expansão, troca de tela e abertura do painel de adição, respeitando a preferência do sistema por movimento reduzido.
- O cache do service worker foi atualizado para `treino-pwa-v9`.
- A sintaxe JavaScript e a integridade do ZIP foram verificadas. O teste visual automatizado do navegador não concluiu neste ambiente; teste as interações no aparelho após publicar.


## Redesign v10 — substituição de exercícios
- As alternativas abrem em um painel inferior, sem ocupar espaço permanente dentro do cartão do exercício.
- Inclui busca no catálogo e filtro por categoria; sem busca, mostra primeiro as sugestões relacionadas ao movimento atual.
- Antes da troca, apresenta uma etapa de revisão com o exercício atual e o novo exercício.
- A troca altera somente o nome na ficha e preserva as séries preenchidas, cargas, repetições, RIR e marcações do treino atual.
- O painel pode ser fechado pelo botão, tocando no fundo ou pressionando Escape; respeita a preferência por movimento reduzido.
- Cache atualizado para `treino-pwa-v10`.
