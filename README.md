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
No portal do Azure, no workspace recém-criado, naveguei até a opção de ML automatizado e cliquei em "Novo trabalho de ML automatizado".

Em "Configurações básicas", preenchi os campos necessários, como o nome do trabalho, o novo nome do experimento e uma descrição, antes de avançar.

No passo "Tipo de tarefa e dados", selecionei Regressão e, em seguida, escolhi a opção "Criar" para selecionar os dados. No modal aberto, preenchi os detalhes necessários, como o tipo de dados (Tabular), e avancei para configurar a fonte de dados como "De arquivos da Web".

Na etapa seguinte, informei a URL do conjunto de dados (https://aka.ms/bike-rentals).

Em "Configurações de tarefas", escolhi o conjunto de dados importado e selecionei a coluna "rentals" como target. Ajustei os limites conforme necessário e habilitei o encerramento antecipado.

Para validação e teste, selecionei "Divisão de validação de treinamento".

Ao avançar para a configuração de computação, mantive as configurações padrão.

Após revisar as configurações do trabalho, cliquei em "Enviar trabalho de treinamento".

Após a conclusão do treinamento, acessei a página do trabalho e cliquei em "Modelo de registro". Optei pelas opções padrão de "Selecionar saída" e, nas configurações do modelo, forneci apenas o nome e a versão antes de criar o modelo.

Por fim, o modelo ficou acessível na opção de menu "Modelo".


## Passo 4: Métricas do modelo

Quando meu trabalho automatizado de aprendizado de máquina é concluído, posso revisar o melhor modelo treinado.

Na guia "Visão geral" do trabalho automatizado de aprendizado de máquina, observo o melhor resumo do modelo. Aqui está uma captura de tela do melhor resumo do modelo do trabalho automatizado de aprendizado de máquina com uma caixa ao redor do nome do algoritmo.

Observação: Posso ver uma mensagem com o status "Aviso: pontuação de saída especificada pelo usuário alcançada...". Esta é uma mensagem esperada. Continuo para a próxima etapa.

Seleciono o texto em "Nome do algoritmo" do melhor modelo para visualizar seus detalhes.

Depois, seleciono a guia "Métricas" e escolho os gráficos residuais e predito_true, se eles ainda não estiverem selecionados.

Revizo os gráficos que mostram o desempenho do modelo. O gráfico de resíduos mostra os resíduos (as diferenças entre os valores previstos e reais) como um histograma. O gráfico predito_true compara os valores previstos com os valores verdadeiros.

### Implantação e Teste do Modelo

Na guia "Modelo" do melhor modelo treinado pelo trabalho automatizado de aprendizado de máquina, seleciono "Implantar" e uso a opção de serviço Web para implantar o modelo com as seguintes configurações:

- **Nome**: prever-aluguéis
- **Descrição**: Prever aluguel de bicicletas
- **Tipo de computação**: Instância de Contêiner do Azure
- **Habilitar autenticação**: selecionado

Aguardo o início da implantação – isso pode levar alguns segundos. O status de implantação do endpoint de previsão de aluguel será indicado na parte principal da página como "Running".

Aguardo até que o status da implantação mude para "Succeeded". Isso pode levar de 5 a 10 minutos.

### Teste do Serviço Implantado

Agora posso testar meu serviço implantado.

No estúdio Azure Machine Learning, no menu esquerdo, seleciono "Endpoints" e abro o ponto final em tempo real de previsão de aluguéis.

Na página do endpoint em tempo real de previsão de aluguel, visualizo a guia "Teste".

No painel "Dados de entrada para testar o endpoint", substituo o modelo JSON pelos seguintes dados de entrada:
Para acessar as métricas do modelo treinado, na página do modelo, acesso o link informado em "Criado por trabalho". Também é possível acessar o trabalho informado na opção do menu "Tarefas (jobs)".

Na página da tarefa, acessei a aba métricas.

![img9](https://github.com/matheusantunes-silva/DIO-Lab-Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML/assets/156004284/3969eee7-8afc-4ede-913d-98e38d2d181d)


## Passo 5: Teste do modelo
Na página do modelo, acessei a aba "Pontos de extremidade" e em seguida cliquei em "Implantar". Porém, por algum motivo o botão não funcionou. Então, para criar o ponto de extremidade para esse modelo, acessei "Pontos de extremidade" no menu lateral, e cliquei em "Criar". Em seguida marquei o modelo e deixei todos os campos seguintes como os valores padrões, exceto "Contagem de instâncias" que deixei como 1. Então cliquei em "Implantar".



Logo após a implantação, que demora bastante, acessei a aba "Testar" do ponto de extremidade criado para o meu modelo.

Para o teste, utilizei o json abaixo:

```
 {
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }
```

 E com isso obtive o resultado desejado. Foi uma ótima primeira experiência utilizando o Microsoft Azure e acredito que vou conseguir realizar maiores projetos nas próximas tarefas designadas.

