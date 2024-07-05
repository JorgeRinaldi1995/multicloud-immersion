# Passos para implementação do Projeto - Parte 1

# ‼️ Atenção: utilize o vídeo abaixo como resumo técnico para acelerar a implementação da parte 1 do projeto

[ICP_PT_MISSAO1_COMPLEMENTO.mp4](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/f253463c-d9e3-4e98-b81b-ccce5f012515/ICP_PT_MISSAO1_COMPLEMENTO.mp4)

# Passos na Amazon Web Services (AWS)

## Criando o usuário terraform-pt-1 usando o serviço IAM

- Acesse a console da AWS ([https://aws.amazon.com](https://aws.amazon.com/)) **e logue com sua nova criada**. Na barra de pesquisas, digite IAM. Na seção Services, clique em IAM.
- Clique em Users e em seguida Add users, insira o nome **terraform-pt-1** e clique em Next para criar o usuário do tipo programmatic.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a875ce20-3579-40eb-831c-66254b6a791a/Untitled.png)
    
- Após avançar, em **Set permissions**, clique no botão Attach existing policies directly.
    
    ![Screenshot 2023-02-03 at 09.27.44.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/204df068-e2dd-47fb-b822-8c192d8890b2/Screenshot_2023-02-03_at_09.27.44.png)
    
- Digite **AmazonS3FullAccess** em **Search.**
- Selecione **AmazonS3FullAccess**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6effb0e0-025f-4b74-818f-47e93de3db0b/Untitled.png)
    
- Clique em **Next**
- Revise todos os detalhes
- Clique em **Create user**

## Criando o a Access Key (Chave de Acesso) para o usuário terraform-pt-1 usando o serviço IAM

- Acesse o usuário **terraform-pt-1**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/ca055cf7-fe1a-46de-b123-f0c362ad3748/Untitled.png)

- Clique na aba **Security credentials**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/e386e961-2910-4940-88f6-1ab599a01226/Untitled.png)

- Navegue até a seção **Access keys**
- Clique em **Create access key**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/b365adb6-b76e-4e4c-b70e-ad214388d168/Untitled.png)

- Selecione Command Line Interface (CLI) e **I understand the above recommendation and want to proceed to create an access key.**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/70cc17cc-457c-4a29-bd2b-1b8589792abf/Untitled.png)

- Clique em **Next**.
- Clique em **Create access key**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/4c1fbaec-089b-457f-b284-09eac52447e2/Untitled.png)

- Clique em **Download .csv file**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/0c5a461d-c841-459e-81f1-3bb928b4fc98/Untitled.png)

- Após o download finalizar, clique em Done.
- Com o download feito, renomeie o **.csv** para **key.csv**

# Passos na Google Cloud Platform (GCP)

## Preparando o ambiente para executar o Terraform

- Acesse a Console da Google Cloud (https://console.cloud.google.com/) **e logue com sua nova criada**
- Abra o Cloud Shell
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/24accf42-6a2a-4b4b-ba8c-a049e845b78a/Untitled.png)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/3763c175-1891-405a-a61b-f12554b43c17/Untitled.png)
    
- Baixe o arquivo `mission1.zip` no Google Cloud shell usando o comando wget
    
    ```json
    wget https://tcb-public-events.s3.amazonaws.com/icp/mission1.zip
    ```
    
    **Resultado**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/23c3b83c-d74e-4430-a1e7-27ed6df94d45/Untitled.png)
    
- Faça o upload do arquivo `key.csv` para o Cloud Shell usando o browser
    
    **Passo 1**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/d7c33862-aa01-4ec9-a5a3-cf9b41a63bf1/Untitled.png)
    
    **Passo 2**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/e2d57ff5-dc58-42d2-9ebf-6129a46e50bb/Untitled.png)
    
    **Passo 3**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/7bab0fbd-ddc5-4273-aac3-04a356de452c/Untitled.png)
    
- Verifique se os arquivos `mission1.zip` e `key.csv` estão na pasta no Cloud Shell usando o comando abaixo
    
    ```json
    ls
    ```
    
    **Resultado**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/ed761b04-5a47-4a22-8b19-d29b68029b72/Untitled.png)
    
- Execute os comandos de preparação dos arquivos:
    
    ```
    unzip mission1.zip
    ```
    
    ```
    mv key.csv mission1/pt
    ```
    
    ```
    cd mission1/pt
    ```
    
    ```
    chmod +x *.sh
    ```
    
    **Resultado**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/406245b4-14b7-44ec-abf5-d87084d65100/Untitled.png)
    
- Execute os comandos abaixo para preparar o ambiente da AWS e GCP
    
    ```
    mkdir -p ~/.aws/
    ```
    
    ```
    touch ~/.aws/credentials_multiclouddeploy
    ```
    
    ```
    ./aws_set_credentials.sh key.csv
    ```
    
    ```
    GOOGLE_CLOUD_PROJECT_ID=$(gcloud config get-value project)
    ```
    
    ```
    gcloud config set project $GOOGLE_CLOUD_PROJECT_ID
    ```
    
- Clique em Autorize
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/6e43c9c0-943f-47b0-b715-591e370dd537/Untitled.png)
    
- Execute o comando abaixo para setar o projeto no Google Cloud Shell
    
    ```
    ./gcp_set_project.sh
    ```
    
- Execute os comandos para habilitar as APIs do Kubernetes, Container Registry e Cloud SQL
    
    ```
    gcloud services enable containerregistry.googleapis.com
    ```
    
    ```
    gcloud services enable container.googleapis.com
    ```
    
    ```
    gcloud services enable sqladmin.googleapis.com
    ```
    
    ```
    gcloud services enable cloudresourcemanager.googleapis.com
    ```
    
    ```
    gcloud services enable serviceusage.googleapis.com
    ```
    
    ```
    gcloud services enable compute.googleapis.com
    ```
    
    ```
    gcloud services enable servicenetworking.googleapis.com --project=$GOOGLE_CLOUD_PROJECT_ID
    ```
    

## Executando o Terraform para provisionar a infraestrutura MultiCloud na AWS e Google Cloud

- Execute os seguintes comandos para provisionar os recursos de infraestrutura

```
cd ~/mission1/pt/terraform/
```

```
terraform init
```

```
terraform plan
```

```
terraform apply
```

**Atenção**: O processo de provisionamento pode levar entre **15 a 25 minutos** para finalizar. Mantenha o **CloudShell** aberto durante o processo. Caso seja desconectado, clique em **Reconectar** quando a sessão expirar (a sessão expira após **5 minutos** de inatividade por padrão)

# Anexo I - Destruindo o ambiente e começando novamente

Caso você tenha tido algum problema/erro e queira zerar o ambiente para começar novamente, siga o passo a passo abaixo para remover todo o ambiente MultiCloud

## [Google Cloud] Deletar VPC Peering

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0d1b678b-cd91-4256-93c7-73b2e82396d5/130abec1-80d7-42d5-b94f-eef0eefaa5d8/Untitled.png)

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

# Dicas de Segurança

- Para ambientes de produção, é recomendado utilizar apenas a Rede Privada para o acesso ao banco de dados.
- Nunca fornecer acesso à rede pública (0.0.0.0/0) para os banco de dados de produção. ⚠️

**Chegando até aqui, você concluiu a implementação da primeira parte do Projeto Hands-on e fez a implementação dos recursos em um ambiente MultiCloud (AWS e Google Cloud) utilizando o Terraform!**