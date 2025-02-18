# Algoritmo de Alocação Automática de Inspetores

## Visão Geral
Este repositório contém um algoritmo para alocação automática de inspetores em inspeções semanais, levando em consideração critérios como disponibilidade, capacitação, liderança e preferências de parceria.

## Regras de Alocação
O algoritmo segue as seguintes regras:

1. **Disponibilidade**: Apenas inspetores disponíveis na semana correspondente podem ser alocados.
2. **Capacitação**: Apenas inspetores capacitados para o tipo de empresa podem ser selecionados.
3. **Exclusividade Semanal**: Um inspetor não pode ser alocado para mais de uma inspeção na mesma semana.
4. **Limite de Escalas**: Cada inspetor pode ser escalado no máximo em 7 inspeções ao longo do período.
5. **Evitar Semanas Consecutivas**: Se um inspetor foi escalado na semana anterior, ele será evitado na seleção (exceto na região 'C').
6. **Alocação de Líderes**: Pelo menos um dos inspetores da inspeção deve ser um líder.
7. **Parceria Preferencial**: Se um inspetor tiver um parceiro preferido disponível, essa preferência será considerada.
8. **Distribuição Equilibrada**: O algoritmo prioriza inspetores com menos escalas atribuídas para manter um equilíbrio na carga de trabalho.

## Estrutura dos Arquivos
O algoritmo processa as seguintes planilhas:

- `Escala_Final.xlsx`: Contém a lista de inspeções a serem preenchidas.
- `Disponibilidade_2025.xlsx`: Lista os inspetores disponíveis por semana.
- `Inspetores_2025.xlsx`: Contém informações sobre capacitação e liderança dos inspetores.
- `Preferencia_2025.xlsx`: Define as preferências de parceria entre inspetores.

## Fluxo do Algoritmo
1. Carrega os dados das planilhas.
2. Converte as colunas de datas para o formato correto.
3. Cria um dicionário de preferências de parceria.
4. Itera sobre cada inspeção da escala:
   - Filtra inspetores disponíveis e capacitados.
   - Separa os líderes e não líderes.
   - Verifica o histórico de alocações para evitar repetições.
   - Seleciona inspetores priorizando aqueles com menos escalas.
   - Aplica a regra de parceria preferencial.
   - Garante que pelo menos um inspetor seja líder.
   - Atualiza o histórico de escalas.
5. Gera e salva a nova escala em um arquivo Excel.
6. Exibe a distribuição final das escalas por inspetor.


## Ajustes e Personalizações
- **Modificar o número máximo de escalas por inspetor**: Ajuste o parâmetro `max_escalas`.
- **Alterar o critério de escolha entre candidatos**: Defina `priorizar_menos_escala=False` para escolha aleatória.
- **Adicionar novos critérios**: O código pode ser expandido para incluir regras adicionais de alocação.
