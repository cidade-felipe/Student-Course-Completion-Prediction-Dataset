# Student Course Completion Prediction Dataset

## Visão Geral

Este projeto foca na análise e predição de taxas de conclusão de cursos por estudantes em ambientes de aprendizagem online. O dataset contém informações abrangentes sobre dados demográficos de estudantes, padrões de engajamento, desempenho acadêmico e resultados de conclusão de cursos.

## Objetivos

- **Análise Exploratória de Dados**: Compreender padrões e fatores que influenciam a conclusão de cursos
- **Modelagem Preditiva**: Desenvolver modelos para prever a conclusão de cursos por estudantes
- **Geração de Insights**: Extrair insights acionáveis para instituições educacionais

## Estrutura do Projeto

```css
Student-Course-Completion-Prediction-Dataset/
├── article/
├── data/
│   └── preprocessed/
├── figure/
├── mapeamentos/
├── notebooks/
│   ├── preprocessed.ipynb
│   └── student_insights.ipynb
│   └── train.ipynb
│── pickles/
├── reports/
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

## Características do Dataset

O dataset contém **35 features** em **100.000 registros de estudantes**:

### Dados Demográficos dos Estudantes
- **Gênero**: Masculino/Feminino
- **Idade**: 17-52 anos (média: 25.7)
- **Nível de Educação**: Diploma, Bacharelado, Mestrado
- **Status de Emprego**: Estudante, Empregado, Autônomo
- **Cidade**: 15 principais cidades indianas

### Tecnologia e Acesso
- **Tipo de Dispositivo**: Laptop, Mobile, Tablet
- **Qualidade da Conexão com a Internet**: Baixa, Média, Alta
- **Percentual de Uso do Aplicativo**: 0-100%

### Informações do Curso
- **Nome do Curso**: Diversos cursos de programação e design
- **Categoria**: Programação, Design, etc.
- **Nível do Curso**: Iniciante, Intermediário, Avançado
- **Duração do Curso**: 25-90 dias
- **Avaliação do Instrutor**: 4.1-4.7

### Métricas de Engajamento
- **Frequência de Login**: 0-15 vezes
- **Duração Média da Sessão**: 5-81 minutos
- **Taxa de Conclusão de Vídeos**: 5-99.9%
- **Participação em Discussões**: 0-12 interações
- **Tempo Dedicado em Horas**: 0.5-25.6 horas
- **Dias desde o Último Login**: 0-99 dias
- **Notificações Verificadas**: 0-18
- **Pontuação de Interação com Pares**: 0-10
- **Contagem de Reprises**: 0-15 vezes

### Desempenho Acadêmico
- **Atividades Submetidas**: 0-10
- **Atividades Perdidas**: 0-10
- **Tentativas de Quiz**: 0-16
- **Média de Notas em Quizzes**: 19.6-100%
- **Nota do Projeto**: 0-100%

### Informações Financeiras
- **Modalidade de Pagamento**: Cartão de Crédito, Cartão de Débito, UPI, NetBanking, Bolsa
- **Taxa Paga**: Sim/Não
- **Desconto Utilizado**: Sim/Não
- **Valor do Pagamento**: ₹0-₹7.149

### Suporte e Comunicação
- **E-mails de Lembrete Clicados**: 0-13
- **Tickets de Suporte Abertos**: 0-8
- **Avaliação de Satisfação**: 1.0-5.0

### Variável Alvo
- **Concluído**: Concluído/Não Concluído

## Preprocessamento de Dados

O pipeline de preprocessamento inclui:

1. **Carregamento de Dados**: Importação do dataset Kaggle
2. **Verificação de Qualidade**: Análise de valores ausentes (nenhum encontrado)
3. **Engenharia de Features**: Criação de features derivadas
4. **Limpeza de Dados**: Remoção de colunas irrelevantes:
   - Student_ID (identificador)
   - Name (informação pessoal)
   - Course_ID (redundante com Course_Name)
   - Progress_Percentage (altamente correlacionado com alvo)
   - Satisfaction_Rating (potencial vazamento de dados)

5. **Exportação de Dados**: Salvar dataset processado para análise

## Insights Principais

### Distribuição da Taxa de Conclusão
- **Taxa geral de conclusão**: Aproximadamente 50% dos estudantes concluem seus cursos
- **Indicadores fortes de conclusão**:
  - Maior número de horas dedicadas
  - Melhores taxas de conclusão de vídeos
  - Logins mais frequentes
  - Menor taxa de atividades perdidas

### Padrões de Engajamento
- **Estudantes bem-sucedidos** tipicamente:
  - Dedicação média de 3.9+ horas
  - Conclusão de 62%+ do conteúdo em vídeo
  - Login 5+ vezes por período
  - Atividade recente (≤4 dias desde último login)

### Correlações de Desempenho
- **Fortes correlações positivas**:
  - Tempo dedicado vs notas em quizzes (r ≈ 0.65)
  - Conclusão de vídeos vs entrega de atividades (r ≈ 0.72)
  - Frequência de login vs conclusão do curso (r ≈ 0.58)

## Tecnologias Utilizadas

- **Python 3.x**: Linguagem de programação principal
- **Pandas**: Manipulação e análise de dados
- **Plotly**: Visualizações interativas
- **Jupyter Notebooks**: Ambiente de desenvolvimento e análise
- **KaggleHub**: Acesso ao dataset

## Como Começar

### Pré-requisitos
- Python 3.7+
- Ambiente virtual (recomendado)

### Instalação

1. Clone o repositório:
```bash
git clone https://github.com/cidade-felipe/Student-Course-Completion-Prediction-Dataset.git
cd Student-Course-Completion-Prediction-Dataset
```

2. Crie e ative o ambiente virtual:
```bash
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

### Utilização

1. **Preprocessamento de Dados**:
```bash
jupyter notebook notebooks/preprocessed.ipynb
```

2. **Análise Exploratória**:
```bash
jupyter notebook notebooks/sutdent_insights.ipynb
```

3. **Carregar Dados Processados**:
```python
import pandas as pd
df = pd.read_csv('data/preprocessed/student_completion_data.csv')
```

## Resultados da Análise

### Principais Descobertas

1. **Padrão de Atividades Perdidas**: Alunos que concluíram o curso apresentam mediana menor de atividades perdidas com distribuição mais concentrada. Alunos que não concluem mostram maior dispersão e valores máximos mais altos, indicando que perder atividades é um comportamento recorrente associado à evasão, não um evento isolado.
![Boxplot de Atividades Perdidas](figure/Boxplot_atividades_perdidas.png)

2. **Recência de Acesso**: Estudantes que concluíram tendem a ter poucos dias desde o último login, com valores concentrados próximos de zero. Alunos que não concluem apresentam caudas longas com longos períodos sem acesso, demonstrando que quanto maior o tempo sem acessar a plataforma, menor a chance de conclusão.
![Boxplot de Dias desde Último Login](figure/Boxplot_dias_desde_ultimo_login.png)

3. **Consistência vs Esforço Esporádico**: Alunos que concluem apresentam mediana de horas dedicadas claramente maior com distribuição deslocada para valores mais altos. Alunos que não concluem concentram-se em poucas horas de dedicação com outliers indicando tentativas pontuais sem consistência. Dedicar mais tempo não garante conclusão, mas dedicar pouco praticamente garante o oposto.
![Boxplot de Horas Dedicadas](figure/Boxplot_tempo_gasto_vs_conclusão.png)

4. **Consumo de Conteúdo como Proxy de Engajamento**: A distribuição dos alunos que concluem está visivelmente deslocada para taxas mais altas de consumo de vídeo, enquanto os que não concluem concentram-se em valores médios e baixos. Assistir ao conteúdo até o fim é um bom proxy de engajamento real, indicando que não é só entrar na plataforma, mas consumir o material de forma consistente.
![Boxplot de Taxa de Conclusão de Vídeos](figure/Histograma_taxa_de_conclusão_de_vídeos.png)

5. **Relação Esforço-Desempenho**: Existe tendência geral de mais horas dedicadas associadas a melhores médias nos quizzes, mas o mais importante é a separação visual dos grupos. Alunos que concluem aparecem com mais frequência na região de maior esforço e melhor desempenho, enquanto os que não concluem se espalham mais nos níveis baixos e intermediários.
![Boxplot de Relação Esforço-Desempenho](figure/Scatter_esforço_vs_desempenho.png)

6. **Natureza Multivariada da Conclusão**: As correlações com a variável Completed são moderadas, não exageradas, como esperado em dados comportamentais reais. Destacam-se correlação positiva com Video_Completion_Rate e Assignments_Submitted, e correlação negativa com Assignments_Missed. Nenhuma variável isolada explica completamente a conclusão.
![Boxplot de Natureza Multivariada da Conclusão](figure/Heatmap_de_correlação_(variáveis_numéricas).png)

### Resumo Estatístico

| Métrica | Concluíram | Não Concluíram | Diferença |
|---------|------------|----------------|-----------|
| Tempo Médio Dedicado (hrs) | 3.9 | 2.1 | +85% |
| Conclusão de Vídeos (%) | 62 | 45 | +38% |
| Frequência de Login | 5.2 | 3.1 | +68% |
| Nota Média em Quizzes (%) | 73 | 68 | +7% |

## Trabalhos Futuros

- **Modelos de Machine Learning**: Implementar algoritmos preditivos (Random Forest, XGBoost, CatBoost, Redes Neurais)
- **Engenharia de Features**: Criar métricas adicionais de engajamento
- **Análise de Séries Temporais**: Analisar padrões de progressão ao longo do tempo
- **Framework de A/B Testing**: Projetar experimentos para estratégias de intervenção
- **Dashboard em Tempo Real**: Construir sistema de monitoramento para progresso de estudantes

## Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## Autor

**Felipe Cidade Soares**
- GitHub: [@cidade-felipe](https://github.com/cidade-felipe)
- LinkedIn: [LinkedIn](https://www.linkedin.com/in/cidadefelipe/)
- Ano: 2026

## Agradecimentos

- Fonte do dataset: [Kaggle - Student Course Completion Prediction Dataset](https://www.kaggle.com/datasets/nisargpatel344/student-course-completion-prediction-dataset)
- Comunidade de mineração de dados educacionais
- Contribuidores de código aberto

## Contato

Para dúvidas, sugestões ou colaborações:
- Crie uma issue neste repositório
- Conecte-se via GitHub
- Conecte-se via LinkedIn

---

**Nota**: Este dataset contém dados sintéticos/anonimizados para fins educacionais e de pesquisa. Todas as informações pessoais foram anonimizadas para proteger a privacidade.