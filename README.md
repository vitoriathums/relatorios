# Dashboard de Controle - Projeto CBS 2027

Dashboard dinâmico, interativo e responsivo para acompanhamento gerencial do cronograma do projeto CBS 2027 (Reforma Tributária).

## Recursos do Dashboard
- **Leitura Nativa de Excel (`.xlsx`)**: Lê automaticamente a aba `Cronograma V2`.
- **Fórmula de Avanço Parametrizável em Tempo Real**:
  1. *Peso por Duração (Regra 0/100)*: Ponderado pelos dias úteis previstos; tarefas pontuam apenas quando 100% concluídas.
  2. *Por Quantidade de Tarefas (1/N)*: Cada tarefa possui peso unitário idêntico.
  3. *Peso Manual / Ponderado*: Permite configurar peso arbitrário por entrega.
- **Filtros Dinâmicos**:
  - Filtro por Responsável (com tratamento de múltiplos responsáveis, ex.: "Pablo e Kelvin").
  - Filtro por Frente de Atuação (Fiscal, TI, Suprimentos, etc.).
  - Filtro de Risco: Exibir apenas tarefas com término vencido (em atraso).
  - Filtro de Marcos Críticos (Milestones).
- **Indicadores e Visualizações**:
  - KPIs de Avanço Físico %, Tarefas Concluídas, Términos Vencidos e Inícios Pendentes.
  - Gráfico de barras comparativo: Tarefas Concluídas vs. Atrasadas por Responsável.
  - Barra de progresso por Pacote/Frente.
  - Tabela detalhada com semáforo de status e dias de atraso calculados em tempo real.

---

## Como subir para o seu GitHub Pages

1. **Crie um repositório** no GitHub (ex.: `cbs2027-dashboard`).
2. Extraia o conteúdo deste ZIP na sua máquina.
3. No terminal, dentro da pasta extraída, inicialize o git e faça o push:
   ```bash
   git init
   git add .
   git commit -m "feat: initial commit dashboard cbs 2027"
   git branch -M main
   git remote add origin https://github.com/<SEU_USUARIO>/<SEU_REPOSITORIO>.git
   git push -u origin main
   ```
4. **Ative o GitHub Pages**:
   - No GitHub, acesse **Settings** > **Pages**.
   - Em **Build and deployment**, selecione:
     - **Source**: `Deploy from a branch`
     - **Branch**: `main` e pasta `/ (root)`.
   - Clique em **Save**.
5. Em menos de 2 minutos, o dashboard estará no ar no endereço:  
   `https://<SEU_USUARIO>.github.io/<SEU_REPOSITORIO>/`

---

## Como funciona a sincronização com o SharePoint

O projeto possui um workflow configurado em `.github/workflows/sync-cronograma.yml`.
- A cada **30 minutos em horário comercial**, o GitHub Actions acessa o link público do SharePoint com o parâmetro `?download=1`, baixa a planilha atualizada e faz commit do arquivo `cronograma.xlsx`.
- A equipe pode editar normalmente o Excel no SharePoint.
- O GitHub Pages servirá sempre os dados atualizados para quem estiver visualizando, sem risco de edição acidental na planilha oficial.
- Você também pode forçar a sincronização a qualquer momento na aba **Actions** > **Sincronizar Cronograma SharePoint** > **Run workflow**.
