# DIO Lab | Trabalhando com Machine Learning na Prática no Azure ML
Esse projeto visa a prática de fundamentos de Machine Learning e de análise de dados dentro do Microsoft Azure. Todas as ações e diretrizes foram fornecidas pela Microsoft conforme está no link do desafio abaixo.

Links importantes:

[Explore Azure AI Services](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/02-content-safety.html)

Desafio [Explore Automated Machine Learning in Azure Machine Learning](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html)

## Passo 1: Criando recurso do Azure Machine Learning

Primeiro precisei criar um recurso de Machine Learning. Para isso, cliquei em "Criar recurso" e depois pesquisei por Azure Machine Learning no marketplace. Após encontrar o recurso, crie ele.

![img1](https://github.com/matheusantunes-silva/DIO-Lab-Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML/assets/156004284/050691c0-e67b-4f37-b4bd-a4bba5472ff8)


## Passo 2: Configurando o recurso do Azure Machine Learning

Na aba de Noções Básicas informei a assinatura para cobrança no campo Assinatura e depois informei o Grupo de recursos que vai englobar o recurso que será criado.

Em seguida, em Detalhes da área de trabalho, informei os detalhes do workspace que será criado. Como foi um laboratório, as configurações foram mínimas. Por fim, criei o recurso clicando em Consultar + criar. Após a validação ser aprovada, cliquei em "Criar".


Após o recurso ser criado, cliquei no botão "Ir para o recurso" para acessar a página do recurso.

Nessa página, existe o botão "Iniciar o estúdio" que redirecionará para o estúdio do Azure Machine Learning.


## Passo 3 - Criando o modelo
No estúdio, na página do workspace criado anteriormente, acessei a opção do menu ML automatizado e na página aberto, cliquei em "Novo trabalho de ML automatizado".

![img5](https://github.com/matheusantunes-silva/DIO-Lab-Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML/assets/156004284/85bc4381-7627-4f76-9402-023383a8eca6)


Em "Configurações básicas", preenchi os campos "Nome do trabalho", "Novo nome do experimento" e "Descrição". Após cliquei em "Avançar".

No passo "Tipo de tarefa e dados", selecionei o tipo de tarefa como Regressão e em seguida, em "Selecionar dados", cliquei em "Criar". No modal aberto, em "Tipos de dados", preenchi os campos "Nome", "Descrição" e escolhi "Tipo" como Tabular. Cliquei em "Avançar" e no passo "Fonte de dados", escolhi "De arquivos da Web" e cliquei em avançar novamente.

No passo "URL da Web", informei a URL https://aka.ms/bike-rentals do conjunto de dados. 


Em "Configurações de tarefas", escolhi o conjunto de dados importado. Após, em "Coluna de destino" escolhi a coluna rentals como target.

Nos campos de "Limite", preenchi com os valores abaixo e marquei "Habilitar encerramento antecipado".


Em "Validar e testar", em "Tipo de validação" escolhi "Divisão de validação de treinamento".

Ao avançar, em Computação, mantive os valores mostrados na imagem abaixo.


Após avançar e examinar as configurações do trabalho, cliquei em "Enviar trabalho de treinamento".

Após finalizar o trabalho de treinamento, precisei criar o modelo. Para isso, acessei a página do trabalho realizado e cliquei em "Modelo de registro". Deixei as opções padrões para "Selecionar saída". Em "Configurações do modelo", somente preenchi o nome e a versão. Após isso, cliquei em criar o modelo.


Po fim, o modelo fica acessível na opção de menu "Modelo".


## Passo 4: Métricas do modelo
Para acessar as métricas do modelo treinado, na página do modelo, acesso o link informado em "Criado por trabalho". Também é possível acessar o trabalho informado na opção do menu "Tarefas (jobs)".

Na página da tarefa, acessei a aba métricas.

![img9](https://github.com/matheusantunes-silva/DIO-Lab-Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML/assets/156004284/3969eee7-8afc-4ede-913d-98e38d2d181d)


## Passo 5: Teste do modelo
Na página do modelo, acessei a aba "Pontos de extremidade" e em seguida cliquei em "Implantar". Porém, por algum motivo o botão não funcionou. Então, para criar o ponto de extremidade para esse modelo, acessei "Pontos de extremidade" no menu lateral, e cliquei em "Criar". Em seguida marquei o modelo e deixei todos os campos seguintes como os valores padrões, exceto "Contagem de instâncias" que deixei como 1. Então cliquei em "Implantar".

![img10](https://github.com/matheusantunes-silva/DIO-Lab-Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML/assets/156004284/f05a0548-a447-40ab-b289-6e95e5b01022)


Logo após a implantação, que demora bastante, acessei a aba "Testar" do ponto de extremidade criado para o meu modelo.

Para o teste, utilizei o json abaixo:


![img11](https://github.com/matheusantunes-silva/DIO-Lab-Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML/assets/156004284/05c0f12c-b053-4766-8bc3-e49a1e6c1e5f)

