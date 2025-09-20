# SantanderCodeGirls_CursoAWS
Este repositório contém anotações insights e boas práticas aprendidos durantes as aulas do curso de AWS da plataforma DIO.

## Amazon Web Services (AWS)

### Introdução à AWS e ao Universo da Computação em Nuvem

=> IaaS: Tudo que se constrói ou que migra, a nuvem te dá apenas a infra
estrutura básica - servidores, rede, armazenamento.

=> PaaS: A nuvem fornece a estrutura e a plataforma pronta para desenvolvi
mento, o usuário só precisa criar e gerenciar aplicativos, sem se preocupar
com o hardware ou o sistema operacional. (ex: AWS Lambda)

=> SaaS: A nuvem fornece software pronto pra usar, então o usuário apenas 
utiliza o software sem se preocupar com infraestrutura, sistema operacional
ou configuração. (ex: Gmail, Zoom)


### Fundamentos Essenciais da Infraestrutura AWS

A AWS possui uma extensa rede global de Data Centers, chamados de "Regions"
e "Availability Zones".

a) REGIÕES: São áreas geográficas compostas por 2 (min) ou mais zonas de 
disponibilidade.
 
=> Projetada para ser isolada de outras regiões.
	- Maior tolerância de falhas e estabilidade
	
=> Escolha da região
	- Quais critérios devem ser analisados?
		(i) Compliance: Significa, de forma geral, estar em conformidade
		com leis, normas, regulamentos internos e externos e padrões éti
		cos aplicáveis a uma organização = CONFIDENCIALIDADE 
		(ii) Disponibilidade de Serviços
		(iii) Custo
		(iv) Latência: Distância de clientes = Lentidão do timing de res
		posta ao disponibilizar serviços.
		

b) ZONAS DE DISPONIBILIDADE: São Data Centers independentes fisicamente,
mas conectados logicamente.

=> Recursos exclusivos da região escolhida = + tolerância a falhas
=> Garantia de alta disponibilidade = + alcance de clientes


### Configuração da Conta AWS e Práticas de Segurança

=> Conta principal (root) com super permissões e secundária
	- https://signin.aws.amazon.com/signup?request_type=register

ATENÇÂO! 
	- Ficar atento ao email com cobranças
	- Autenticação multifator (MFA): garantia de segurança
	- Estabelecer barreiras de proteção para permissões


### Primeiros Passos com Acesso Seguro e Controle de Custos na AWS

=> Acessar: US East (N. Virginia) = + barato
=> Como criar recursos na AWS? Via console/portal, AWS CLI (Command
Line Interface) e pela CloudShell (ambiente de linha de comando p/ cria
ção de recursos) 

a) Identity and Access Management (IAM): É o serviço que permite geren
ciar quem pode acessar os recursos da AWS e o que cada um pode fazer.
	ex: Usuários, Grupos, Funções, Políticas

=> Cadastramento do MFA (Credenciais de Segurança)
	- Criação de um dispositivo p/ controle de entrada na root
	
=> Criação de user: Definição de acesso do usuário
	- ID User e criação de nova senha
	- Identity Center: É um serviço da AWS que funciona como um ponto
	central de gerenciamento de acesso para múltiplas contas AWS e até 
	mesmo aplicações externas
	- Criação de grupo e aplicações do user
	- Registro do MFA (Google Authenticator) p/ todos

OBS! Enquanto o IAM gerencia permissões dentro de uma conta AWS específica,
o Identity Center gerencia usuários e acessos em várias contas e aplicações
ao mesmo tempo.

b) Políticas e Permissões

=> Definição de acessos do usuário
=> ETIQUETAS: Ajuda na identificação do user por critérios da conta root

========================== EXERCICIO 001 ==================================

Ler os usuários do Excel e salvar nos grupos do Console.
Comando no Git Bash: bash scriptIAM.sh usuarios.csv

ATENÇÃO !!! Um arquivo CSV (Comma-Separated Values) é um formato de arqui
vo de texto simples usado para armazenar dados em forma de tabela. O Excel
é uma das plataformas de leitura de arquivos desse tipo.

### Instâncias EC2

O que são EC2? 

 A Elastic Compute Cloud são as máquinas virtuais na AWS, podendo ser com sistema operacional Windows ou Linux.

É composta por: 
- CPU
- Memória
- Disco
- Rede
- Sistema Operacional

No modelo Cloud, é do tipo IaaS, ou seja, é uma infraestrutura como serviço. O cliente é responsável pelos aplicativos, dados e conexões feitas. 

=> A escolha da instância certa garante eficiência, escalabilidade e economia de gastos com nuvem.

a) Terminologia

=> O EC2 fornece a capacidade de computação na cloud da AWS
=> SEGURANÇA BÁSICA: É possível utilizar firewall incorporado do AWS, grupos de segurança, protocolo, porta e IPs de origem para o controle de acesso às suas instâncias EC2


b) Tipos de Instâncias EC2

=> Diferentes recursos de computação: memória, armazenamento, etc.
=> Separados em FAMÍLIAS de instâncias
  
AWS Pricing Calculator: Estimativa de custo de arquitetura e desenvolvimento do projeto 


c) Otimização de Recursos: "Poupar custos na AWS" 

=> Desligamento de instâncias não utilizadas (períodos noturnos/finais de semanas)
=> Remoção de recursos ociosos ou não utilizados 
=> Escalamento de recursos
- ESCALAR VERTICALMENTE: Acrescentar ou eduzir capacidade de um recurso em um 	mesmo nó e, geralmente, está relacionado a alterar o número de vCPUs, memória, 	storage ou rede de uma instância

- ESCALAR HORIZONTALMENTE: Quando você aumenta o número de recursos, 	adicionando instâncias para suportar alguma aplicação.



(i) Instâncias Sob Demanda

As instâncias on-demand são compradas a uma taxa fixa por hora e recomendadas para aplicativos com cargas de trabalho irregulares de curto prazo, sem interrupções.

ex: Uso durante o teste e desenvolvimento de aplicativos no EC2



(ii) Instâncias Reservadas

Costumam ser mais baratas, mas paga o ano inteiro de uso - desvantajoso para casos de baixo uso de instâncias.



(iii) Instâncias SPOT

Garante a disponibilidade de aplicações sob demanda com descontos, sendo a sua desvantagem o fato delas poderem ser encerradas a qualquer momento.


### Amazon EBS (Elastic Block Store)

É uma storage altamente confiável que pode ser anexado em qualquer instância EC2 e toda instância possui um volume de armazenamento. (ex: como anexar um HD externo)

=> Capacidade de expansão rápida = nova partição de instância
ex: Armazenamento para banco de dados ou dados p/ aplicativos de web e logs de sistema


### Amazon S3 (Simple Storage Service) = 99,99999999%

É um serviço de armazenamento de objetos em nuvem, ideal para organizar e recuperar grandes volumes de daods de forma segura, escalável e possui classes de storage que permitem a economia de custos.

=> S3 Standard = acesso MAIS frequente

O Lifecycle permite fazer a transição de objetos e migrar automaticamente para a classe Glacier (MENOS frequente) = +90 dias s/ uso = + barato


### Criação e uso de imagens AMI

O que é? (Amazon Machine Image) = cópia

=> No Amazon EC2, é uma imagem de máquina virtual pré-configurada que inclui informações necessárias p/ iniciar uma instância, como o sistema operativo, o servidor de aplicações e as próprias aplicações.


a) CRIAÇÃO: As AMIs põem ser criadas a partir de INSTÂNCIAS em execução ou paradas, capturando um instantâneo do seu ambiente configurado.

OBS! Públicas x Privadas

- A AWS fornece uma variedade de AMIs públicas que podem ser usadas ou você pode criar e usar suas próprias AMIs privadas para segurança e personalização.


b) PERSONALIZAÇÃO: É possível personalizar uma instância e criar uma AMI a partir dela = + replicação

Para executar instâncias no EC2, selecione uma AMI para o fornecimento de informações necessárias para iniciar a instância, como o volume do dispositivo raiz e as permissões de inicialização.

c) TIPOS: Existem diferentes tipos de AMIs, incluindo Amazon Linux, Windows e outros

=> Escolha da AMI baseado nos requisitos da aplicação e do sistema
=> Criação de uma base p/ ambientes consistentes e reproduzíveis na nuvem


### Snapchots EBS (IaaS)

É um serviço de backup nativo de AWS que faz backup dos volumes do EBS em um determinado ambiente (produtivo), sendo possível configurar sua frequência. Armazenam no S3, em uma matriz de armazenamento em um ambiente diferente. Os snapchots são oferecidos a diferentes custos em diferentes regiões.

=> Qual a diferença entre imagem e snapshot?

Enquanto uma máquina AMI faz o backup do servidor inteiro (incluindo todos os volumes EBS anexados), um snapchot é uma cópia pontual de um determinado volume.
