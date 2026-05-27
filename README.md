# Meus Estudos de AWS: Entendendo o Amazon EC2 

Este repositório foi criado para organizar minhas anotações e os principais aprendizados que tive nas aulas teóricas da DIO sobre o **Amazon EC2 (Elastic Compute Cloud)**. 

Como as aulas focaram bastante na arquitetura, no funcionamento da ferramenta e em como gerenciar custos, montei este resumo para servir de material de apoio e consulta rápida.

---

##  O que é o Amazon EC2? (Visão Geral)

Basicamente, o EC2 é o serviço da AWS que nos permite "alugar" servidores virtuais na nuvem (que eles chamam de **instâncias**). Em vez de gastar uma fortuna comprando hardware físico, a gente consegue subir uma máquina em minutos.

Os conceitos que achei mais importantes entender sobre a estrutura dele:
* **AMI (Amazon Machine Image):** É como se fosse o "instalador" ou a imagem do Sistema Operacional (Ubuntu, Amazon Linux, Windows) já pré-configurada.
* **Tipos de Instância:** As máquinas são divididas por famílias. Tem máquina focada em uso geral, outras otimizadas para processamento pesado, outras para muita memória RAM, etc. 
* **Security Groups:** Funcionam como o firewall da nossa máquina. Por padrão, vem tudo bloqueado, e a gente precisa liberar explicitamente as portas que vai usar (tipo a porta 22 para SSH ou a 80 para HTTP).
* **EBS (Elastic Block Store):** É o HD virtual que a gente acopla na instância para salvar os arquivos.

---

##  O que aprendi sobre Custos (A parte mais crítica!)

Um dos pontos mais batidos nas aulas foi que, na nuvem, se você não tomar cuidado, a conta vem alta. A AWS tem três modelos principais para cobrar pelo uso das instâncias:

* **On-Demand (Sob Demanda):** Você liga a máquina, usa e paga pelo tempo que ela ficou rodando. É o modelo mais caro por hora, mas te dá total liberdade de ligar e desligar quando quiser. Bom para testes.
* **Instâncias Reservadas / Savings Plans:** Se você já sabe que vai precisar daquela máquina rodando por 1 ou 3 anos direto, você assina um compromisso com a AWS e eles te dão um desconto gigante (chega a mais de 70%).
* **Instâncias Spot:** É você usar o "resto" de capacidade que está sobrando nos servidores da AWS por um preço ridiculamente barato (até 90% de desconto). O único problema é que se a AWS precisar daquela máquina de volta, ela te avisa com 2 minutos de antecedência e desliga. Excelente para processamento em lote que pode ser interrompido.

### Detalhe importante que muita gente erra:
Se você der um **Stop** na sua instância, você para de pagar pelo uso da CPU e da memória RAM. **Mas você continua pagando pelo espaço do HD (EBS)** que ficou lá guardado esperando você ligar a máquina de novo. Para parar de pagar tudo, tem que dar **Terminate** (o que apaga a máquina de vez).

---

##  Meus Insights / O que levei das aulas

1. **Economia em primeiro lugar:** Não adianta só saber subir uma máquina, o bom profissional de nuvem precisa saber arquitetar pensando no bolso da empresa. Escolher o modelo de pagamento certo faz toda a diferença.
2. **Segurança por padrão:** Aquela ideia de fechar todas as portas no Security Group e só abrir o que for estritamente necessário é uma regra de ouro para não deixar o servidor exposto na internet.
3. **Elasticidade real:** O poder da nuvem não é só ter uma máquina forte, mas sim usar ferramentas (como o Auto Scaling) para fazer a infraestrutura crescer quando tem muito acesso e encolher na madrugada, evitando desperdício de dinheiro.

---

##  O que usei para estudar
* Aulas teóricas na plataforma da **DIO**.
* Documentação oficial da AWS para aprofundar em alguns conceitos.
* Git e GitHub para criar este portfólio.
