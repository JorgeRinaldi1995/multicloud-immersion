# Passos para implementação do Projeto - Parte 3

# ‼️ Atenção: utilize o vídeo abaixo como resumo técnico para acelerar a implementação da parte 3 do projeto

[ICP_PT_MISSAO3_COMPLEMENTO.mp4](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/1b5d6290-5872-4457-ba01-4e6754bda879/ICP_PT_MISSAO3_COMPLEMENTO.mp4)

# Passos na Google Cloud Platform (Migração do Banco de Dados MySQL)

- Conectar ao Google Cloud Shell
- **Download** o dump do banco de dados usando o **comando wget**
    
    ```
    cd ~
    ```
    
    ```
    **wget https://tcb-public-events.s3.amazonaws.com/icp/mission3.zip**
    ```
    
    ```
    unzip mission3.zip
    ```
    
- Conecte ao MySQL DB em execução no Cloud SQL usando o Public IP address (assim que aparecer a janela para colocar a senha, insira **welcome123456**). **Não esqueça de substituir o IP Público em vermelho**
    
    ```
    mysql --host=**<subtituir_public_ip_cloudsql>** --port=3306 -u app -p
    ```
    
- Importar o dump do banco de dados no Cloud SQL
    
    ```
    use dbcovidtesting;
    ```
    
    ```
    source ~/mission3/pt/db/db_dump.sql
    ```
    
- Checar se os dados foram importados com sucesso
    
    ```
    select * from records;
    ```
    
    ```
    exit;
    ```
    

# Passos na Amazon Web Services (Migração dos arquivos PDF)

- Conectar no AWS Cloud Shell
- Download dos arquivos PDF (Comprovante de teste negativo escaneado em PDF)
    
    ```
    wget https://tcb-public-events.s3.amazonaws.com/icp/mission3.zip
    ```
    
    ```
    unzip mission3.zip
    ```
    
- Sincronizar os arquivos PDF com o seu bucket criado no AWS S3 usado para o COVID-19 Testing Status System. **Altere o nome do bucket para o seu bucket.**
    
    ```
    cd mission3/pt/pdf_files
    ```
    
    ```
    aws s3 sync . s3://**luxxy-covid-testing-system-pdf-pt-xxxx**
    ```
    
- Testar a aplicação. Ao testar a aplicação e navegar na opção "Ver registros" você deverá ser capaz de visualizar os dados importados!
    
    ![Screen Shot 2022-02-07 at 4.39.51 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c710178-ec07-4aa5-8259-cec6e3484820/Screen_Shot_2022-02-07_at_4.39.51_PM.png)
    

### **Parabéns! Você migrou uma aplicação e seu banco de dados do "on-premises" para uma Arquitetura MultiCloud!**

# Anexo I - Destruindo o ambiente

Após concluir o projeto prático e coletar as evidências de implementação, siga o passo a passo abaixo para remover todo o ambiente MultiCloud

## [Google Cloud] Deletar recursos Kubernetes

**Passo 1**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/6d73fcef-a630-488b-bcc8-30361c5a4aee/Untitled.png)

**Passo 2**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/e424139b-dce0-4612-b685-340c53d81639/Untitled.png)

```json
kubectl delete deployment luxxy-covid-testing-system
```

```json
kubectl delete service luxxy-covid-testing-system
```

## [Google Cloud] Deletar VPC Peering

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/130abec1-80d7-42d5-b94f-eef0eefaa5d8/Untitled.png)

## [AWS] Deletar arquivos dentro do S3

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/d6030130-04b4-4f3d-bbd5-9b89c80312dd/Untitled.png)

## [Google Cloud] Deletar recursos restantes com Terraform - Cloud Shell

```json
cd ~/mission1/pt/terraform/
```

```json
terraform destroy
```

## Limpar o Cloud Shell na AWS e Google Cloud

### AWS

```json
cd ~
```

```json
rm -rf mission*
```

### Google Cloud

```json
cd ~
```

```json
rm -rf mission*
```

```json
rm -rf .ssh
```