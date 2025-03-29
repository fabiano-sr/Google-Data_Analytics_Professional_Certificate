
Passo 1: Criar Conta de Serviço no Google Cloud e compartilhar a planilha.

1. No *Google Cloud Console*, crie ou acesse um projeto.  
2. Selecione o projeto.  
3. Acesse *APIs e Serviços* no menu lateral e clique no botão *Ativar APIs e Serviços*.  
4. Pesquise *Google Drive API*, selecione a API e clique no botão *Ativar*.  
5. Pesquise *Google Sheets API*, selecione a API e clique no botão *Ativar*.  
6. No menu lateral, acesse *IAM e administrador* > *Contas de Serviço* e clique no botão *+ Criar Conta de Serviço*.  
7. Insira o nome da conta de serviço e clique em *Criar e Continuar*, depois clique em *Concluído*.  
8. Clique no e-mail da conta de serviço gerada, vá até a aba *Chaves* e clique no botão *Adicionar chave* > *Criar chave*.  
9. Selecione *JSON* e clique em *Criar*.  
      > [!WARNING]
      > O arquivo será baixado automaticamente. *Guarde-o com segurança*, pois ele contém as credenciais da conta de serviço.  
10. Salve o arquivo `.json` no *diretório do seu projeto no VS Code* ou em outro local seguro.  
11. Na *aba de detalhes*, copie o *e-mail da conta de serviço*.  
12. Acesse a planilha no *Google Drive*, clique em *Compartilhar* (*Share*).  
13. No campo de e-mail, cole o e-mail da conta de serviço e clique em *Enviar* (*Send*).  
    > [!WARNING]
    > Certifique-se de que a permissão está como Editor. Também é necessário conceder a permissão no diretório*  
 
Passo 2: Preparar o ambiente para acessar a planilha.
1. Instalar as biliotecas gspread e oauth2client no Python.
    `pip install gspread oauth2client`
2. No script python, importar as bibliotecas
    ```python
    import gspread
    from oauth2client.service_account import ServiceAccountCredentials
    ```
3. Definir o escopo de acesso que a conta vai ter.
    ```python
    scopes = ["https://spreadsheets.googl.com/feeds",
              "https://spreadsheets.googl.com/feeds",
             ]
    ```
4. Criar a credencial de acesso:
    ```python
    creds = ServiceAccountCredentials.from_json_keyfile_name(
        filename=<Credencial.json>,
        scopes=scopes
    )
5. Criar o client
    ```python
    client = gspread.authorize(creds)
    ```

Passo 3: Acessar a planilha.
1. Executar o comando indicando o nome do arquivo e o id do diretório no google drive.
    ```python
    planilha = client.ope(
        title="<nome_do_arquivo>", 
        folder_id="<folder_id>")
2. Executar o comando para indicar qual a página da planilha será carregada.
    ```python
    <planilha> = <planilha>.get_worksheet(<Indice_da_aba>)
    ```
3. Execute o comando para armazer a planilha em uma variável, indicando que todos os registros serão carregados.
        ```python
    <variável> = <planilha>.get_all_records()
    ```
