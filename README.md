# LEITURA-ARQUIVO-PY
Leitura de arquivo csv para filtragem e leitura de palavras especificas, utilizando, programação concorrente, pipeline etc

Analisador de Produção Acadêmica (CAPES/UFC)
Este projeto é um pipeline em Python desenvolvido para processar e analisar dados de produções acadêmicas da CAPES, especificamente focado nos dados da UFC (2021). A aplicação utiliza modelagem orientada a objetos e processamento paralelo para extrair insights e estatísticas de grandes volumes de dados.

🛠️ Arquitetura e Implementação
1. Modelagem Orientada a Objetos
O sistema utiliza a classe Trabalho para representar cada registro do dataset. Esta classe centraliza informações essenciais como:

Programa: Nome do programa de pós-graduação.

Orientador: Nome do docente responsável.

Áreas: Mapeamento entre a Grande Área e a Área de Conhecimento específica.

Título: O nome da produção acadêmica para análise textual.

2. Processamento Concorrente (Multi-threading)
Para lidar com a análise de frequência de palavras nos títulos, o código implementa uma solução escalável com a classe WordCounterWorker:

Threading: Utiliza a biblioteca threading para dividir o processamento em múltiplos núcleos.

Distribuição: O dataset é fatiado em chunks (blocos) calculados dinamicamente com base no número de threads.

Sincronização: Cada thread realiza uma contagem local independente, que é posteriormente consolidada em um dicionário global pela thread principal através do método .join().

3. Pipeline de Processamento de Texto
O tratamento dos dados textuais envolve várias etapas de normalização funcional:

Normalização Unicode: Remoção de acentos utilizando a forma NFKD.

Limpeza de Tokens: Conversão para minúsculas e remoção de pontuações via str.maketrans.

Filtragem Personalizada: Remoção de stopwords (português/inglês) carregadas de arquivos externos e exclusão de palavras com 3 caracteres ou menos.

📊 Rankings Gerados
O script automatiza a geração de quatro visões principais:

Top 10 Programas: Ranking por volume de trabalhos.

Top 10 Orientadores: Identificação dos orientadores com mais produções.

Top 10 Áreas: Hierarquia de Grande Área para Área de Conhecimento.

Top 20 Palavras-Chave: Análise semântica dos termos mais frequentes nos títulos.

🚀 Como Executar
Pré-requisitos
Python 3.x.

Arquivos de suporte: stopwords_pt.txt e stopwords_en.txt.
