# Desafio Docker | Desafio DevOps & Cloud

## Introdução

Problemas: Falhas constantes em produção, indisponibilidade de sistemas, ciclos de deply demorados e desgastantes, custos desnecessários com a nuvem e um aumento significativo das vulnerabilidades de segurança. Além da folha de pagamento com profissionais não qualificados e tecnicamente incapacitados.

A complexidade dos sistemas aumentou muito, e as empresas exigem cada vez mais escalabilidade, alta disponibilidade e automação.

Profissionais que entendam todo o fluxo de entrega, para garantir entregas rápidas, seguras e sem falhas.

Para continuar competitivo no mercado de TI, dominar as praticas mais modernas de como automatizar ambientes, otimizar processos e garantir a escalabilidade, disponibilidade e resiliência de sistemas.

DevOps, Cloud Computing, Automação de Processos e Monitoramento Avançado de Sistemas. Para de fato conseguir implementar as soluções que dão mais eficiẽncia, confiabilidade, estabilidade as aplicações, ou, conseguir resolver e previnir problemas com muito mais facilidade e velocidade, trazendo mais valor ao projeto e à empresa.

O desafio é sobre um E-Commerce escrito em Python utilizando um banco de dados PostgreSQL. O objetivo é pegar essa aplicação, modernizá-la em contêineres e montar toda a solução de entrega contínua, executando essa aplicação num cluster kubernetes e monitorando também essa aplicação.

Etapas do projeto:
1. Trabalhar a aplicação em docker container, migrar e obter a portabilidade;
2. Executar a aplicação em ambiente produtivo com kubernetes;
3. Colocar essa aplicação em cloud AWS;
4. Automatizar todo o processo de entrega utilizando pipeline CI/CD com GitHub Actions;
5. Monitorar essa aplicação utilizando Prometheus e exibir as informações no Grafana;

- O termo DevOps vem do DevOps Day (2009).
- Problemas no modelo cascata, cada equipe se preocupava com seus processos, métricas, recursos e prioridades.
- Com DevOps cada equipe entende dos impactos no produto e ambiente de produção.
- DevOps surgiu para acabar com essa distância entre as equipes.
- Incentiva a melhoria contínua, comunicação, colaboração e a responsabilildade compartilhada sobre processos, métricas, recursos e prioridades (metas).
- Maior velocidade para teste e entregas.
- Fluxo de produção menos burocrático. Testes, entrega, atualizações mais rápidas, sem downtime. Escalabilidade automática de acordo com as requisições.
- DevOps é baseado em cíclos contínuos e curtos. Onde cada entrega é aprimorada e refinada baseada no feedback constante.

DevOps: um conjunto de práticas e ferramentas para integrar equipes e otimizar processos. Com objetivo de melhorar a qualidade de software, acelerar o tempo de entrega e garantir a confiabilidade das aplicações em produção.

- A implementação de DevOps promove um tempo de lançamento de novos aplicativos no mercado 22% mais rápido que pelos métodos tradicionais.
- 65% das organizações notaram um melhor trabalho em equipe entre as equipes de desenvolvimento e operações após adotarem o DevOps.
- As falhas de implantação caíram 27% com DevOps, melhorando a qualidade e a estabilidade do software.
- 80% das empresas relataram uma melhor qualidade de software como um dos principais benefícios do DevOps.
- A produtividade dos funcionários aumentou 23% devido às práticas de DevOps.
- O trabalho não planejado e o retrabalho foram reduzidos em 33%, levando a um uso mais eficiente dos recursos.
- O trabalho de resolução de incidentes melhor após o DevOps, com 90% das empresas relatando soluções mais rápidas.
- A demanda por engenheiros DevOps aumentou 40%, colocando-os entre as cinco principais funções de tecnologia.
- Os custos de TI caem 25% com DevOps, impulsionados por processos simplificados.
- A satisfação do cliente melhorou em 75% das empresas após a adoção do DevOps.
- 86% das organizações consideram o DevOps essencial para suas operações.

Fonte: <https://scoop.market.us/devops-market-news>

DevOps já é o TOP 1 Framework utilizado atualmente!

5 Pilares do DevOps (CALMS):
- Cultura (Culture): mudança de pensamento e comportamento dentro das empresas e equipes, com comunicação e colaboração.
- Automação (Automation): Padronização e automatização dos processos repetitivos. Aumenta a produtividade, também evita falhas humanas e desgaste pessoal.
- Lean: Uso de gestão ágil.
- Monitoramento (Measurement): Métricas e feedback para otimização de processos e do software.
- Compartilhamento (Sharing): Compartilhamento entre equipes de conhecimento e experiências, garantindo a melhora contínua. Integrando desenvolvimento e operações.

8 Etapas do DevOps. Representadas em um símbolo do infinito:

- Planejamento > Codificação > build > teste > release > deploy > operação > monitoramento > reinicia

## Conteúdo Técnico

Os conteineres resolvem problemas e conflitos entre setups com camadas de isolamento para cada aplicação. Funcionando da mesma forma em qualquer ambiente.

Docker oferece isolamento, portabilidade, velocidade na inicialização e consistência no comportamento das aplicações em diferentes ambientes.

Container é diferente de Virtual Machine. É muito mais rápido pelo modo como carrega apenas o necessário para rodar a aplicação.

Docker permite criar, gerenciar e distribuir contêineres de forma intuitiva e eficiente.

A imagem é um blueprint de um projeto, contendo tudo o que é necessário para criar um conteiner. Com o sistema de arquivo, os pacotes, bibliotecas, dependências, tudo que for necessário para a aplicação.

3 elementos da arquitetura do Docker:

- Docker Daemon: Gerencia as imagens, contêineres, redes e volumes. Objetos;
- Docker Client: Interage com Docker Daemon via linha de comando;
- Docker Registry: Repositório de imagens (ex.: Docker Hub).

Dockerfile: Declaração com todas as instruções na ordem certa para montar a imagem.
- Python
- Código da aplicação
- Pip
- GUnicorn
- Comando de inicialização

Construir a imagem, nomeá-la, a partir do Dockerfile:`$ docker build -t conversao-distancia -f Dockerfile .`

Após a primeira construção as etapas ficam em cache. Se quiser reconstruir sem utilizar o cache, adicione o argumento `--no-cache` após Dockerfile. Também depende de alterações no Dockerfile, após uma alteração, as instruções seguintes serão exutadas sem o cache.

Rodando um container em segundo plano (detached), com portas mapeadas e com a imagem criada:`$ docker container run -d -p 8181:5000 conversao-distancia`

Colocar a imagem no repositório hub.docker.com:
1. Ver se a tag na imagem do Dockerfile está com a tag (python:3.13.0)
2. Nomear a imagem criada no formato `<namespace>/<nome da imagem>:<versão>`
3. Boa prática de também subir ela com a tag latest `$ docker tag <namespace/imagem:versão> <namespace/imagem:latest>`


