# Acelerando entrega de valor com IA: SageMaker, Bedrock e Generative BI

*Originalmente publicado no [LinkedIn](https://www.linkedin.com/pulse/acelerando-entrega-de-valor-com-ia-sagemaker-bedrock-e-n-pinto-silva-towhf/) em Dezembro de 2023*

![AWS re:Invent](./images/reinvent2024.png) <!-- Adicione uma imagem relacionada ao re:Invent -->

No AWS re:Invent 2024, o Keynote do Dr. Swami Sivasubramanian, VP de Dados e IA da AWS, foi um dos destaques! Neste texto, compartilho um resumo dos principais insights que tive ao assistir a apresentação. Ao final, apresento uma conclusão com ideias práticas para aplicar esse aprendizado e gerar impacto real.

## 🔘 Amazon Sagemaker

✨ Mesmo com o advento do GenAI, que de certa forma aproximou um público mais leigo de soluções que são implementadas por AI, a demanda do público mais especializado (cientistas de dados, por exemplo) vem sendo alterada. Agora, esse público precisa aplicar as técnicas de treinamento de modelos nos Foundation Models utilizados pelas suas empresas, para fins de fine tuning, por exemplo

🚀 **(Novidade) Sagemaker AI (New Generation)**

Depois de anos recebendo feedbacks de clientes, o objetivo da abordagem foi unificar toda a jornada de dados, analytics e necessidades voltadas para AI como um todo em uma única ferramenta.

### 🔴 Case Autodesk - 2D/3D Generative AI (Sagemaker)

Raji Arasu, CTO da Autodesk, fez uma apresentação muito inspiradora e relevante (minuto 19:31 do video), demonstrando casos de sucesso de uma estratégia e prática de AI com uma grande consistência técnica e com um impacto notável no cliente final. Tópicos que tomei nota:

- Mais de 15 anos de parceria com a AWS nas áreas de Cloud, Dados e AI
- Desafio de extrair inteligência de uma gigantesca diversidade de arquivos existentes na base, de forma que se tornassem dados granulares dentro da Cloud
- Líder na abordagem "2D/3D Generative AI" a partir de toda evolução sua evolução e maturidade de Machine Learning e AI
- Desenvolvimento do próprio Foundation Model (FM), baseados nas especificidades do setor
- 2D/3D CAD Geometry: distinção de geometria e textura
- Mais do que melhoria de produtividade, tudo isso está se convertendo em funcionalidades, dentro dos produtos, para os clientes finais
- Foco em minimizar tarefas e maximizar a criatividade 🤯

### Arquitetura de AI

- **Data Ingestion**: DynamoDB por questões de desempenho e escala
- **Data Preparation**: EMR+EKS+Glue+SageMaker
- **Data Train**: Sagemaker (para treinamento dos FMs) + Elastic Fabric Adaper (melhorou o tempo de treinamento em 50%)
- **Data Inference**: Sagemaker (real-time e batch inference)
- Melhoria de 30% na produtividade de iniciativas que envolvam AI

## 🔘 Amazon Bedrock

✨ Inferência é o processo em que modelos de IA, como os de geração de texto (GenAI), transformam dados em respostas e insights em tempo real, atendendo às novas e rápidas demandas por escalabilidade e precisão

Serviço gerenciado que viabiliza a criação de soluções seguras e escaláveis com GenAI. Com ele é possível:
- Empresas parceiras na disponibilização de FMs: Mistral AI, Meta, Stability AI, Anthropic 

🚀 **(Novidade) Poolside Assistant**: Incorporação do FM da empresa poolside para apoio aos engenheiros de software em atividades diversas 

🚀 **(Novidade)** Incorporação do Luma AI na plataforma, para geração de vídeos de alta qualidade a partir textos e imagens 

🚀 **(Novidade) Bedrock Marketplace**: descobrir, testar e usar modelos gerados e compartilhados por empresas diversas

🚀 **(Novidade) Prompt Caching**: feature importante para gerenciar o cache das interações feitas dentro dos prompts, melhorando a latência (~85%) e custos (~90%), em função dos tokens processados pelo FM

🚀 **(Novidade) Intelligent Prompt Routing**: orquestração de prompts com os modelos mais adequados, dentro das restrições de custo, latência e acurácia configuradas, a partir de um único end-point

RAG = Retrieval Augmented Generation, ou seja, o modelo utiliza um mecanismo de busca (ex.: vetor semântico ou consultas estruturadas) para recuperar informações relevantes de uma base de conhecimento externa 

🚀 **(Novidade) Amazon Kendra GenAI Index**: permite a conexão com fonte de dados de serviços corporativas (Sharepoint, Salesforce, Jira, etc) como boas opções para uso RAG, para fins de geração de assistentes ou como base de conhecimento

✨ A variabilidade dos tipos de dados existentes (estruturados, não estruturados e multimodais) torna os trabalhos aplicados à GenAI mais complexos.
Sistemas que usam RAG precisam aprender como acessar os dados estruturados, para que o seu trabalho seja feito adequadamente
O processo de convertermos linguagem natural para SQL (NL2SQL) é complexo

🚀 **(Novidade) Bedrock Knowledge Bases supports Structured Data Retrieval**: o prompt com a pergunta realizada é convertida para SQL e as queries rodam em fontes como Redshift, Sagemaker Lakehouse ou no novo S3 Tables e a resposta é fornecida em linguagem natural

✨ Alguns casos de uso requerem a utilização de uma distintas fontes de dados para se obter respostas assertivas sobre o que foi perguntado via prompt. Nesta situação, faz-se necessário montar grafos, conectando todas as fontes possíveis. Implementar isso manualmente exige uma dedicação relevante.

🚀 **(Novidade) Bedrock supports GraphRAG**: integração facilitada do AWS Neptune (Banco de Grafos) que permite conexão de várias fontes de dados distintas para aplicação que usam GenAI com RAG, através de uma API simplificada 

✨ Grande parte dos dados corporativos são não-estruturados e os seus contextos multimodais (áudio, video, fotos e até mesmo os textos), não estão prontos para o uso imediato em soluções com GenAI.

🚀 **(Novidade) Bedrock Data Automation**: feature que implementa um poderoso no-code ETL para conversão de conteúdos multimodais em dados estruturados. Além de facilitar o trabalho de engenharia, ele também implementa técnicas que garantem consistências nos dados convertidos, evitando, assim, questões de alucinações nos modelos. 

✨ Existe uma preocupação muita válida sobre as questões que envolvem questões de segurança, privacidade e ética a partir dos dados processados pelos FMs. Para mitigar riscos desta natureza, recomenda-se usar o Amazon Bedrock Guardrails.

🚀 **(Novidade) Multimodal Toxicity for Bedrock Guardrails**: essa feature estende os guardrails para análise de imagens, conseguindo identificar conteúdos inadequados (ex: violência, desvio de conduta)

✨ Os AI Agents vieram para levar as automações para outro patamar, podendo-se aplicar em diversos tipos de caso de uso. O Bedrock ofere os Bedrock Agents para implementação deste conceito, de forma que os workflows mais complexos possam ser viabilizados através da configuração de agentes especializados, apoiando a orquestração e automação

🚀 **(Novidade) Bedrock Multi-Agents Collaboration**: é a capacidade dos agentes criados interagirem entre eles

## 🔘 Amazon Q

Foco centrado em melhorar a produtividade de times técnicos ou não-técnicos
Usa o Bedrock em sua fundação

### 🔘 Amazon Q [Developer]

Assistente para desenvolvimento de softwares, atuando no ciclo de vida completo da disciplina

🚀 **(Novidade)** - top software bench (leaderboard)

✨ GenAI democratiza o desenvolvimento de modelos de ML. Você não precisa ser um cientista de dados para entregar valor por este caminho

🚀 **(Novidade) Amazon Q no Amazon SageMaker Canvas**: com linguagem natural explicamos o problema de negócio ser trabalhado e ele conduzirá os processos de construção, avaliação e deploy do model

### 🔘 Amazon Q [Business]

Ferramenta que aproxima as áreas de negócio aos dados corporativos, permitindo interações via linguagem natural para entendimento de cenários e tomadas de decisões a partir das respostas obtidas

🚀 **(Novidade) Amazon Q in QuickSight Scenarios**: o Amazon Q já estava no QuickSight, permitindo a interações com BIs através de prompts. Agora é possível sairmos de uma resposta mais simplificada em forma gráfica para irmos realmente para uma construção de cenários estruturados a partir de um problema de negócio mais complexo, a partir de toda a base de conhecimento pré-existente

## 💡 Conclusões

As três ferramentas são complementares e podem apoiar em diferentes momentos da jornada de AI, considerando os tipos de desafio de negócio e grau de maturidade técnica em que se está. Abaixo, listei possíveis caso de uso para cada uma delas. 

### 🟢 Amazon Q (Developer, Business, Apps)

#### Developer

- Assistente para geração de novos códigos
- Apoio do troubleshooting de bugs detectados
- Aceleração de modernização de código legado
- Geração automática de documentação de código
- Apoio no code review
- Leitura rápida do estado do ambiente Cloud (custos, desempenho, segurança)
- Apoio no troubleshooting do ambiente Cloud
- Interpretação rápida de logs de servidores ou aplicações
- Interação automática com ferramentas de gestão (ex: Jira)

#### Business

- Conectar bases de serviços SaaS utilizados de forma corporativa
- Ex: Jira, Confluence, Github, Teams
- Fornecer interfaces para que os usuários interajam com essas fontes através de linguagem natural, tanto para consultas cruzadas, quanto para acionar gatilhos de ações nas ferramentas (ex: criar uma issue no Jira com determinadas características) 

#### Apps

- Encapsular prompts para tarefas específicas da rotina
- Ex: template de job description de vagas, template para resposta de e-mail, template para especificação de projeto

### 🟣 Amazon Bedrock

- Prototipação de aplicações que terão algum tipo de feature ligada a GenAI, pelo baixo esforço de se testar diferentes modelos e os seus resultados relacionados a latência, custo e assertividade (requer um bom trabalho de engenharia de prompt, no caso)
- Dentro de uma arquitetura de uma aplicação com GenAI, o serviço atua como um grande orquestrador, não somente de Foundational Models, mas também abstraindo questões de caching, interação com as bases de conhecimento e outras premissas técnicas
- Usando o serviço como base das aplicações em produção, avançamos no tema "Responsible AI", por meio da feature Guardrails. Isso é fundamental, principalmente considerando a variabilidade de respostas que poderíamos ter dos modelos, uma vez que haverá interações com usuários finais
- Saímos de um tipo de solução mais simplificada (somente com engenharia de prompt) e passamos a ter soluções mais robustas, que incorporam bases externas juntamente com os prompts pré-configurados (RAG)
- Com o uso dos Agentes, é possível tratar questões de workflows mais complexos de uma forma bem diferente do convencional

### 🟠 Amazon Sagemaker

- Com o Sagemaker há um foco mais especializado em Machine Learning. Aqui há uma oportunidade de aumento de repertório para o tipo de solução de AI que daremos para os problemas de negócio, até porque, algumas demandas não requerem necessariamente o uso de GenAI
- Mesmo não tendo skills mais aprimoradas de um cientista de dados mais experiente, é possível montar soluções low-code (Sagemaker Canvas), passando pelos fluxos conhecidos de ML (desenvolvimento, treinamento, avaliação, produção), aplicando técnicas diversas (Regressão, Classificação, K-means, etc)
- Olhando para GenAI, considerando que já há uma maturidade mais forte em Machine Learning, a ferramenta deve ser usada para treinamento de FMs existentes, para fins de personalização (vide case Autodesk) 

Agora é hora de priorizar, aprofundar os estudos, praticar com consistência e, gradativamente, aproveitar as oportunidades para colocar o aprendizado em prática!

---

### Sobre o Autor

Tiago do Nascimento Pinto da Silva é CTO na AutoDoc, especialista em transformação digital para o setor de construção civil. Com mais de 20 anos de experiência, lidera iniciativas de inovação através de implementações SaaS, estratégias multicloud e soluções de IA. Certificado como AWS AI Practitioner (Early Adopter), participou de 4 edições do AWS re:Invent e tem implementado com sucesso soluções baseadas em nuvem que transformam negócios.

### Referências

- [Vídeo do Keynote no YouTube](https://www.youtube.com/watch?v=qGzYTg5FIA4)
- [Artigo original no LinkedIn](https://www.linkedin.com/pulse/acelerando-entrega-de-valor-com-ia-sagemaker-bedrock-e-n-pinto-silva-towhf/)
- [Documentação oficial do Amazon SageMaker](https://aws.amazon.com/sagemaker/)
- [Documentação oficial do Amazon Bedrock](https://aws.amazon.com/bedrock/)
- [Documentação oficial do Amazon Q](https://aws.amazon.com/q/)

---

**Tags**: #ArtificialIntelligence #MachineLearning #AWS #SageMaker #Bedrock #AmazonQ #GenerativeAI #BusinessIntelligence #DigitalTransformation #AWSReInvent