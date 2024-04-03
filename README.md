# module4search
Indexar os documentos
Depois de ter os documentos em armazenamento, você pode usar o Azure AI Search para extrair insights dos documentos. O portal do Azure fornece um assistente de Importação de dados. Com esse assistente, você pode criar automaticamente um índice e um indexador para fontes de dados com suporte. Você usará o assistente para criar um índice e importar seus documentos de pesquisa do armazenamento para o índice de Pesquisa de IA do Azure.
1. No portal do Azure, navegue até seu recurso de Pesquisa de IA do Azure. Na página Visão geral, selecione Importar dados.
2. Na página Conectar aos seus dados, na lista Fonte de Dados, selecione Armazenamento de Blobs do Azure. Conclua os detalhes do armazenamento de dados com os seguintes valores:
Fonte de dados: Armazenamento de Blobs do Azure
Nome da fonte de dados: coffee-customer-data
Dados a serem extraídos: conteúdo e metadados
Modo de análise: Padrão
Cadeia de conexão: *Selecione Escolher uma conexão existente. Selecione sua conta de armazenamento, selecione o contêiner de revisões de café e clique em Selecionar.
Autenticação de identidade gerenciada: Nenhuma
Nome do contêiner: essa configuração é preenchida automaticamente depois que você escolhe uma conexão existente.
Pasta Blob: deixe isso em branco.
Descrição: Comentários a Fourth Coffee shops.
3. Selecione Avançar: Adicionar habilidades cognitivas (Opcional).
4. Na seção Anexar Serviços Cognitivos, selecione seu recurso de serviços de IA do Azure.
5. Na seção Adicionar enriquecimentos:
Altere o nome do Skillset para coffee-skillset.
Marque a caixa de seleção Habilitar OCR e mesclar todo merged_content texto em campo.
Nota É importante selecionar Habilitar OCR para ver todas as opções de campo enriquecidas.

Verifique se o campo Dados de origem está definido como merged_content.
Altere o nível de granularidade de enriquecimento para Páginas (blocos de 5000 caracteres).
Não selecione Habilitar enriquecimento incremental
Selecione os seguintes campos enriquecidos:

Habilidade Cognitiva	Parâmetro	Nome do campo
Extrair nomes de locais	 	Locais
Extrair frases-chave	 	Frases-chave
Detectar sentimento	 	sentimento
Gerar tags a partir de imagens	 	imageTags
Gerar legendas a partir de imagens	 	imageCaption
6. Em Salvar enriquecimentos em um repositório de conhecimento, selecione:
Projeções de imagens
Documentos
Páginas
Frases-chave
Entidades
Detalhes da imagem
Referências de imagens
7. Selecione Projeções de blob do Azure: Documento. Uma configuração para Nome do contêiner com as exibições preenchidas automaticamente pelo contêiner do repositório de conhecimento. Não altere o nome do contêiner.
8. Selecione Avançar: Personalizar índice de destino. Altere o nome do índice para coffee-index.
9. Verifique se a chave está definida como metadata_storage_path. Deixe o nome do Sugeridor em branco e o modo de Pesquisa preenchido automaticamente.
10. Revise as configurações padrão dos campos de índice. Selecione filtrável para todos os campos que já estão selecionados por padrão.
11. Selecione Avançar: Criar um indexador.
12. Altere o nome do indexador para coffee-indexer.
13. Deixe a Agenda definida como Uma vez.
14. Expanda as opções Avançadas. Verifique se a opção Base-64 Encode Keys está selecionada, pois as chaves de codificação podem tornar o índice mais eficiente.
15. Selecione Enviar para criar a fonte de dados, o conjunto de habilidades, o índice e o indexador. O indexador é executado automaticamente e executa o pipeline de indexação, que:
Extrai os campos de metadados do documento e o conteúdo da fonte de dados.
Executa o conjunto de habilidades cognitivas para gerar campos mais enriquecidos.
Mapeia os campos extraídos para o índice.
16. Retorne à página de recursos da Pesquisa de IA do Azure. No painel esquerdo, em Gerenciamento de Pesquisa, selecione Indexadores. Selecione o indexador de café recém-criado. Aguarde um minuto e selecione &orarr; Atualize até que o Status indique êxito.
17. Selecione o nome do indexador para ver mais detalhes. 

Consultar o índice
Use o Gerenciador de pesquisa para escrever e testar consultas. O explorador de pesquisa é uma ferramenta incorporada no portal do Azure que oferece uma maneira fácil de validar a qualidade do seu índice de pesquisa. Você pode usar o Gerenciador de Pesquisa para escrever consultas e revisar resultados em JSON.

1. Na página Visão geral do serviço de Pesquisa, selecione Gerenciador de pesquisa na parte superior da tela.
2. Observe como o índice selecionado é o índice de café que você criou. Abaixo do índice selecionado, altere a exibição para JSON view.
3. 
