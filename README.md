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
      
