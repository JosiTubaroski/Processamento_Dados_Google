<div> 
<p><a href="https://github.com/JosiTubaroski/Introducao_Engenharia_Dados/blob/main/README.md">Introdução a Engenharia de Dados</a></p>
</div> 

# Análise de Dados de Sensores IoT em Tempo Real com Google Cloud

### Cenário:

Uma empresa de energia renovável possui turbinas eólicas equipadas com sensores IoT que monitoram o desempenho em tempo real. Cada turbina envia dados de sensores como:

- Velocidade do vento.
- Temperatura.
- Vibração.
- Produção de energia.

O objetivo é monitorar o desempenho, detectar anomalias e prever falhas para evitar tempo de inatividade e reduzir custos operacionais.

### Objetivo:

Construir um pipeline para processar dados de IoT em grande escala utilizando ferramentas do Google Cloud. O sistema deve ser capaz de:

1. Capturar e processar dados em tempo real.
2. Detectar anomalias automaticamente.
3. Armazenar dados para análises históricas e previsões.

### Arquitetura e Ferramentas Utilizadas:

1. Cloud IoT Core: Gerencia e recebe dados dos dispositivos IoT.
2. Pub/Sub: Canal de mensagens para ingestão de dados em tempo real.
3. Dataflow: Processamento em tempo real para transformações e análises iniciais.
4. BigQuery: Armazenamento e análise de dados estruturados e históricos.
5. Vertex AI: Treinamento e aplicação de modelos de Machine Learning para detecção de anomalias.
6. Looker Studio (antigo Data Studio): Visualização e relatórios interativos.

### Passo a Passo:

1. Coleta de Dados com Cloud IoT Core
   - As turbinas enviam dados para o Cloud IoT Core via MQTT ou HTTP.
   - Cada dispositivo é autenticado usando chaves públicas/privadas.

 <img src="https://github.com/JosiTubaroski/Processamento_Dados_Google/blob/main/img/15_JSON_Cloud.png">

2. Ingestão com Pub/Sub
   - O Cloud IoT Core publica mensagens no Pub/Sub.
   - O Pub/Sub atua como um canal de mensagens para lidar com grandes volumes de dados e distribuir para consumidores downstream.

3. Processamento em Tempo Real com Dataflow
   - Um job Apache Beam no Dataflow processa os dados em tempo real:
     - Limpeza: Remove valores inválidos.
     - Transformação: Converte unidades (por exemplo, de Fahrenheit para Celsius).
     - Agregação: Calcula médias móveis, máximos e mínimos.
    
 <img src="https://github.com/JosiTubaroski/Processamento_Dados_Google/blob/main/img/16_Pip_Python.png">

 4. Armazenamento em BigQuery
    - Os dados processados são carregados no BigQuery para análises históricas.
    - Uma tabela particionada por data é usada para otimizar o desempenho e os custos.

 <img src="https://github.com/JosiTubaroski/Processamento_Dados_Google/blob/main/img/17_Consulta_BigQuery.png">

 5. Detecção de Anomalias com Vertex AI
    - Um modelo de Machine Learning treinado no Vertex AI identifica anomalias nos dados, como vibrações excessivas ou quedas súbitas na produção de energia.
    - O modelo é implantado como um endpoint para inferência em tempo real.

 6. Visualização com Looker Studio
    -  O Looker Studio é conectado ao BigQuery para criar dashboards interativos.
    -  Exemplos de visualizações:
       - Gráfico de linha mostrando a produção de energia ao longo do tempo.
       - Heatmap indicando turbinas com maiores taxas de vibração.
       - Alertas em tempo real para valores anômalos.

   ## Benefícios:

   1. Escalabilidade: O pipeline pode lidar com milhões de eventos por segundo, garantindo alta disponibilidade.
   2. Análise em Tempo Real: Com o Dataflow, as anomalias são detectadas quase instantaneamente.
   3. Armazenamento Otimizado: BigQuery permite análises rápidas e econômicas de grandes volumes de dados.
   4. Insights Acionáveis: Vertex AI identifica problemas antes que eles causem falhas graves.
   5. Visualizações Interativas: O Looker Studio fornece dashboards claros e acessíveis para a equipe.

Essa abordagem mostra como o Google Cloud pode ser utilizado para processar grandes volumes de dados de Big Data de forma eficiente e em tempo real.
      
