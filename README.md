# Dicionário Tech

Descomplicando as siglas e termos de tecnologia.

**Deploy**: Deploy é o processo de colocar um software em um ambiente específico, como de teste ou produção.

**PO (Product Owner)**: Um Product Owner (PO) é uma figura que transformar as necessidades do cliente em objetivos claros para as equipes técnicas do projeto.

**POO**: É a sigla para Programação Orientada a Objetos, um paradigma de programação que se baseia na criação de objetos. A POO é uma forma de organizar e escrever software, aproximando o mundo virtual do mundo real.

**API**: É a sigla em inglês para Application Programming Interface, que significa Interface de Programação de Aplicações. É um conjunto de regras e padrões que permitem que diferentes aplicativos se comuniquem e compartilhem dados.

**SOLID**: SOLID é um acrônimo mnemônico que relaciona um tópico de boas práticas de programação a cada letra. A aplicação desses princípios tem por objetivo deixar o projeto mais coeso, reaproveitável e torna a sua manutenção mais simples.

**TDD (Test Driven Development)**: Desenvolvimento baseado em testes.

**SSR (Server Side Rendering)**: Ao acessar sua aplicação, todo o javascript que é processado no navegador é processada no servidor e o navegador recebe todo o resultado já renderizado.

**CSR (Client Side Rendering)**: Renderização no navegador do cliente.

**Deploy Blue/Green**: Ao fazer deploy de uma nova versão, o trafego só é redirecionado a nova versão quando o healthcheck sinaliza ok, caso o healthcheck não dê o ok o tráfego é mantido na versão anterior.

## Arquitetura

**Arquitetura Limpa (Clean Architecture)**: Prega a ideia da arquitetura hexagonal, não tendo acesso as regras de negócio, mas tendo camadas que tenham responsabilidades definidas para acessar as regras de negócio.

**Arquitetura Hexagonal**: Isolar o conceito da sua aplicação, isolar regra de negócio, isolar domínio, onde de um lado adaptadores fazem requisições e de outro lado adaptadores fazem consultas em banco/api externa.

**Microsserviço Autônomo**: microsservice independente, continua rodando mesmo que outros serviços caem (normalmente utilizado com mensageria e com cópia em banco de dados próprio pra não consultar outro serviço pra buscar dados - comum a replicação de dados "dados duplicados" mas só com os dados que o microsserviço precisa).

**Service Mesh**: Uma solução que você pode instalar para monitorar a comunicação de dados que ocorre em toda a rede e interceptar e alterar o comportamento da rede.
Exemplo: microsservico 1 manda mensagem para microsservico 2 que está offline, com o service mesh você pode pegar uma requisição que falhou e re-tentar enviar X vezes. (side car proxy - proxy acoplado ao serviço onde o proxy que faz o retry da requisição para o serviço 2).

**Service Mesh -> Circuit Breaker (Recurso do Service Mesh)**: Serviço 1 enviando muitas requisições para Serviço 2. Serviço 2 está com enorme fila devido a quantidade de requisição elevada, o circuit breaker pode ser configurado para retornar erro 500 para as próximas requisições do serviço 1 até o serviço 2 efetuar o self healing e conseguir processar toda a fila.

**CQRS (Command Query Responsibility Segregation)**: Separação da leitura da escrita - utilizado para trabalhar com banco de dados de leitura separado do banco de dados de escrita.

**Event Sourcing**: Se eu tenho um cliente Renan e altero para Renan Augusto eu não vou consegui ver que antes era Renan, então com event sourcing eu posso ter um histórico de tudo que ocorreu (log) para saber que antes o cliente se chamava renan.

**DDD (Domain-Driven Design)**: É uma abordagem de desenvolvimento de software que coloca o foco no entendimento profundo de negócios. Em vez de começar pelo código ou pela tecnologia, prioriza-se a compreensão de regras, processos e conceitos da empresa que a aplicação é destinada a atender.


## Mensageria

**Kafka**: Apache Kafka é uma plataforma de código aberto para processamento de dados em tempo real. É usado para criar pipelines de dados e aplicações que se adaptam a fluxos de dados. Permite que diferentes sistemas troquem informações rapidamente e de forma organizada. É usado para coletar, processar e armazenar dados de eventos de streaming. É usado para construir aplicações que consomem fluxos de dados. É usado como uma solução de broker de mensagens, que é uma plataforma que processa e media comunicação entre duas aplicações. 

**RabbitMQ**: RabbitMQ é uma solução de enfileiramento de mensagens gratuita, de código aberto e extensível. É um agente de mensagens que entende AMQP (Advanced Message Queuing Protocol), mas também pode ser usado com outras soluções de mensagens populares como o MQTT. É altamente disponível, tolerante a falhas e escalável.

**Kafka vs RabbitMQ**: O Kafka é um barramento de mensagens que processa e reprocessa dados transmitidos em disco. O RabbitMQ é um sistema de mensageria que pode lidar com trabalhos em segundo plano. 
O Kafka é adequado para: Processamento de fluxo de alto rendimento, Arquiteturas orientadas por eventos, Agregação de logs, Análise em tempo real, Streaming de alto rendimento. 
O RabbitMQ é adequado para: Agendamento de tarefas, Filas de trabalho, Mensagens de microsserviços, Solicitação-resposta, Roteamento flexível. 


## Golang

**GoRoutine**: Thread muito leve, facilitando paralelismo e concorrência. Thread em C#/Java = 2mb. GoRoutine = 2kb.

**Slice**: List.

**Sync.WaitGroup**: await em grupo do golang, aguarda todos os processos assíncronos finalizar para continuar.

**Channel**: fácil comunicação entre goroutines, aguarda o leitor após um envio.

**Channel Buffer**: channel com tamanho informado, não aguarda o leitor após um envio (efetua todos os envios para depois começar a ler).
