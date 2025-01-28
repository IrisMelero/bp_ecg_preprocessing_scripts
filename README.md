# Documentação

## 1.0. Visão Geral:

Os scripts desse repositório têm como função principal tratar e organizar os exames presentes na base de dados da Benefiência Portuguesa.

Sua execução é fundamental para a anonimização de cada exame, e extrair informações julgadas relevantes para as próximas etapas do projeto de pesquisa.

Esse arquivo detalha a estrutura do repositório, pré-requisitos e instruções de execução dos scripts.

## 2.0. Estrutura do Repositório:

### 2.1. Estrutura de arquivos e pastas:

📁 requirements.txt  
📁 utils.py  
📁 complete_processing.py  
📁 anonymization.py  

 
### 2.1. Descrição de funcionalidade de cada arquivo:

📁 requirements.txt  
Esse arquivo contém as bibliotecas com métodos e funções utilizados nos scripts, são elas, e suas funções:
- pillow : Manipulação de imagens
- pymupdf : Leitura e manipulação de arquivos PDF
- pandas : Manipulação de dados estruturados  

 

📁 anonymization.py  
Script responsável por anonimizar os nomes dos PDF's e gerar as seguintes saídas:
- Exams_anonymized: pasta com os arquivos renomeados
- file_mapping.csv: arquivo com mapeamento entre o nome antigo e novo de cada arquivo PDF    
  
  

📁 utils.py  
Contém funções auxiliares criadas para auxiliar no processamento dos PDF's
- process_pdf: Processa um PDF, recorta regiões especificadas (como ECG, velocidade e amplitude), e salva como imagens.
- extract_pdf_slices_sequential: Processa todos os PDF's em uma pasta, movendo arquivos com problemas para uma pasta de erros.
- resize_images_in_folder: Redimensiona imagens em uma pasta mantendo a proporção.
- extract_information: Extrai informações textuais específicas (data, hora, sexo, etc.) da primeira página de um PDF    
  
  
📁 complete_processing.py  
Script principal responsável por processar os dados, realizar recortes de imagens, e extrair informações textuais dos PDF's.
Gera as seguintes saídas:
- extract_information.csv: Arquivo .csv com todas as informações relevantes extraídas de cada exame, (["File", "Data", "Hora", "Sexo", "Data de Nascimento", "Laudo"])
- ECG_Images, Amplitude, Speed: pastas contendo informações relevantes não convertidas para texto, ou seja, as imagens recortadas do ECG, e detalhes de amplitude e velocidade de cada exame
- Problems e Errors: pastas criadas para registrar arquivos problemáticos, guardando-os separadamente para análise mais cuidadosa.  
  

## 3.0. Pré-Requisitos:

### 3.1. Instalar as dependências:
Verificar se possui o package manager uv instalado, ou acesse [aqui](https://docs.astral.sh/uv/getting-started/installation/) o guia de instalação

### 3.2. Verificações antes de iniciar o processamento:
1. Tenha um backup dos arquivos originais pois os PDFs serão deletados no final do processo

2. Certifique-se de que a pasta Exams contenha os PDFs originais e esteja no diretório principal do repositório

## 4.0. Como Executar:

### 4.1. Prepare o ambiente para executar os scritps
1. Primeiro clone esse repositório para ter acesso aos scripts
2. Em seguida instale as dependências do projeto executando o comando abaixo no diretório local
   > uv sync
4. Após executar o comando, certifique-se que o ambiente virtual esteja habilitado no terminal

### 4.2. Execute o script de anonimização:

Execute o seguinte comando para anonimizar os arquivos

> python anonymization.py

Isso criará a nova pasta Exams_anonymized e o arquivo file_mapping.csv

### 4.2. Execute o script de processamento e extração de informações:
Execute o script principal

> python complete_processing.py

Com isso você obterá os dados extraídos de cada PDF (extract_information.csv), as pastas contendo as imagens recortadas de cada exame (ECG_Images), os recortes de amplitude e velocidade do exame (Amplitude e Speed respectivamente), e os arquivos com problemas para revisão manual (Problems e Errors)





            
