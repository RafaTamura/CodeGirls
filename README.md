# Desafio DIO: Gerenciando Instâncias EC2 na AWS

Este repositório documenta a prática e o aprofundamento de conhecimentos em serviços essenciais da Amazon Web Services (AWS), focado no gerenciamento de **EC2 e EBS**, mas expandido para incluir **S3 e Lambda** para construir uma arquitetura funcional de ponta a ponta.

Criado como parte dos estudos do **Bootcamp Santander Code Girls | DIO**.

---

## Sobre a Solução e o Desafio

O objetivo deste projeto foi ir além do básico de provisionamento, integrando serviços para simular um ambiente de aplicação real. A arquitetura demonstra uma solução coesa, que vai desde a camada de computação (servidor web) até a automação de tarefas utilizando o paradigma *serverless*.

**Serviços AWS Integrados:**
* **EC2** (Elastic Compute Cloud)
* **EBS** (Elastic Block Store)
* **S3** (Simple Storage Service)
* **Lambda** (Função Serverless)

---

## Detalhamento da Arquitetura Implementada

A estrutura da solução foi projetada para garantir **computação resiliente**, **armazenamento persistente** e **automação reativa**.

| Componente | Função na Arquitetura |
| :--- | :--- |
| **Computação (EC2)** | Servidor web (Apache/Nginx) executado em uma instância com **Amazon Linux 2**, atuando como o *host* principal da aplicação. |
| **Armazenamento Persistente (EBS)** | Um volume de **8 GiB** foi criado, anexado e montado na instância EC2, assegurando a durabilidade dos dados da aplicação. |
| **Armazenamento de Objetos (S3)** | Utilizado para *storage* escalável de arquivos estáticos. Configurado com **Versionamento** para proteção contra exclusão acidental ou *rollback*. |
| **Automação Serverless (Lambda)** | Uma função **Python** acionada por eventos no S3 (ex: *upload* de uma nova imagem), processando o objeto e gerando logs no CloudWatch. |

---

## Funcionalidades e Configurações Chave

* **Provisionamento Seguro:** Instância EC2 configurada com **Security Groups** restritivos para acesso HTTP (porta 80) e SSH (porta 22).
* **Montagem de Volume:** Processo de formatação (`mkfs`) e montagem do volume EBS para disponibilizar o espaço em disco na instância.
* **Gatilho de Eventos:** Configuração de notificação do S3 para a função Lambda, estabelecendo um padrão de **Arquitetura Orientada a Eventos**.
* **Lógica Serverless:** Código em Lambda que demonstra processamento de *uploads* de forma eficiente, sem gerenciamento de infraestrutura.

---

## Documentação Visual e Diagrama

Para facilitar a compreensão do fluxo de dados e dos componentes, o diagrama de arquitetura foi elaborado com atenção aos detalhes:

* **Ferramenta:** Draw.io

---

## Conhecimentos Consolidados

A realização deste laboratório solidificou a capacidade de orquestrar e gerenciar serviços na nuvem. As principais competências exercitadas incluem:

* **IaaS (EC2):** Domínio completo do ciclo de vida da instância, desde o lançamento até a configuração de rede e segurança.
* **Estratégias de Armazenamento:** Compreensão prática da distinção entre **EBS (Armazenamento em Bloco)** para performance transacional e **S3 (Armazenamento de Objetos)** para escalabilidade e durabilidade de arquivos.
* **Serverless:** Implementação de uma lógica de negócios sob demanda, explorando a eficiência da arquitetura Lambda.
* **Segurança em Nuvem:** Criação e aplicação de **Security Groups** e **Políticas de Acesso (IAM/Bucket Policies)** para garantir o princípio do menor privilégio.
