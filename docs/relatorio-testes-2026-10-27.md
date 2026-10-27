# Relatório da bateria abrangente de testes

**Data:** 27/10/2026  
**Projeto:** Jogo de Palavras

## Resultado geral

| Verificação | Comando/ambiente | Resultado |
|---|---|---|
| Testes automatizados | `npm test` | Aprovado — 3 arquivos e 19 testes |
| Tipagem TypeScript | `npm run check` | Aprovado |
| Build de produção | `npm run build` | Aprovado |
| Fluxos da aplicação | Navegador integrado com Vite | 37 verificações aprovadas |
| Erros em execução | Console JavaScript e requisições da página | 0 erros e 0 requisições falhas |

## Cobertura automatizada por módulo

### Catálogo de palavras — `src/content.test.ts`

- Confirma o tamanho de respostas e palpites aceitos nos níveis leve, normal e desafiador.
- Confirma que a seleção diária é determinística para a mesma data e configuração.

### Regras do jogo — `src/game-core.test.ts`

- Normalização de acentos e espaços.
- Avaliação das marcas correta, presente e ausente, inclusive para letras repetidas.
- Rejeição de tamanhos incompatíveis, comprimento incorreto e palavras fora do dicionário.
- Preservação da melhor marca de cada letra no teclado.
- Criação de grade compartilhável sem inserir o palpite ou a resposta.

### Progresso local — `src/progress.test.ts`

- Separação de estatísticas diárias e de prática, empates e partidas incompletas.
- Restauração e validação de dados salvos, incluindo rodada corrompida, modalidade, data, nível e marcas.
- Rejeição de vitória sem palpite vencedor.
- Preservação das palavras reveladas na coleção.

## Cobertura exercitada no navegador

Foram realizadas 37 verificações de interação na aplicação em execução, cobrindo:

- Inicialização, título, tabuleiro e quantidade de tentativas/tamanho da palavra por nível.
- Alternância entre desafio diário e prática, entre os níveis e entre as mecânicas de letras e definição.
- Rejeição de palpite curto e de palavra fora do dicionário sem consumir tentativa.
- Envio por teclado físico e teclado virtual, incluindo apagar letra.
- Vitória em rodadas diária e de prática; derrota após esgotar as tentativas.
- Bloqueio de entradas após a conclusão, exibição da resposta e geração de resultado compartilhável sem spoiler.
- Ação de copiar resultado, com verificação da mensagem de sucesso ou da alternativa para cópia manual.
- Abertura e fechamento dos modais de coleção e estatísticas; atualização da coleção e dos indicadores.
- Separação das estatísticas diárias e da prática, incluindo taxa de vitória, sequência e partidas concluídas.
- Persistência e retomada de partidas após recarregar e ao alternar nível/mecânica.
- Layout sem rolagem horizontal nas larguras de 320, 375, 768 e 1280 pixels.

## Arquivos e superfícies exercitados

Os testes unitários exercitam diretamente os módulos de catálogo, regras e progresso. A navegação pelo navegador exercita a entrada HTML, a inicialização React, a interface, os estilos, os controles, as interações e o armazenamento local. A checagem de tipos e o build também validam os arquivos TypeScript e a configuração de empacotamento usados por esses comandos.

## Alterações realizadas

- Nenhuma alteração foi necessária na lógica do jogo, nos testes existentes ou nas dependências; as verificações passaram.
- Este relatório foi atualizado para registrar a bateria ampliada e os resultados observados.
- O build gerou arquivos em `dist/`, diretório ignorado pelo Git.

## Limites da verificação

Os resultados demonstram o funcionamento nos cenários executados, mas não garantem todos os ambientes ou combinações possíveis. Não foram feitos testes em todos os navegadores e dispositivos físicos, com tecnologias assistivas, nem uma varredura de todas as datas/fusos e combinações de estado. Portanto, a bateria é abrangente para os fluxos principais, mas não equivale a uma prova exaustiva.
