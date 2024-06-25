# Fabric Workshop -  São Paulo

Bem-vindo à página wiki do Fabric Workshop. Esta página contém todos os links de que você precisará para o conteúdo de hoje, além de quaisquer alterações ou soluções alternativas que possam ser necessárias. Esperamos que você aproveite o dia!
 
## Links
 
* Link desta página: [aka.ms/fabric-sp](https://aka.ms/fabric-sp)
* Feedback: [Feedback](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbR5UnTHndg5dHvqF4p45wkjZURFZONzBXNUtTNzZRWEpSV0VLRURXSlM3Ti4u&origin=QRCode&qrcodeorigin=presentation)
 
**Portais:**
* Azure Portal: [https://portal.azure.com](https://portal.azure.com)
* Fabric Portal: [https://app.fabric.microsoft.com](https://app.fabric.microsoft.com)
 
**Conteúdo Original:**
* Original GitHub repo with Labs: [https://aka.ms/fabricrealtimelab](https://aka.ms/fabricrealtimelab)
* Resources Zip File (notebooks): [https://aka.ms/fabricrealtimelab-resources](https://aka.ms/fabricrealtimelab-resources)
 
**Acesso ao laboratório:**
* Registering for labs: [https://cloudweeks.learnondemand.net](https://cloudweeks.learnondemand.net/)
* Key: 75ACD06FC7824114
 
**Conteúdos de Fabric para Parceiros:**
* [Microsoft Fabric Partner Community](https://aka.ms/JoinFabricPartnerCommunity)
* [Learn Fabric](https://aka.ms/learn-fabric)
* [Fabric Bootcamp](https://aka.ms/azuredepthworkshops)
* [Fabric Partner Resources](https://aka.ms/FabricPartnerResources)
* [Industry Dream Demos](https://aka.ms/dreams)
* [Analytics Campaign in a Box](https://aka.ms/AnalyticsCIAB)
* [Deliver a x-IAD - In a Day Workshop](https://aka.ms/XIADPartnerOpportunity)
* [Azure Innovate](https://aka.ms/AzurePLofferings)
* [Fabric Featured Partner](https://aka.ms/FabricFeaturedPartners)
* [How to become a Microsoft Featured Partner](https://aka.ms/HowToBecomeFFP)
 
**Alguns highlights sobre o Fabric no**[Build](https://build.microsoft.com):
* [Microsoft Fabric: What's new and what's next](https://build.microsoft.com/en-US/sessions/e2dadf62-d982-4467-9c5c-fd232d663783?source=sessions)
* [Reimagine Real-Time Intelligence with Microsoft Fabric](https://build.microsoft.com/en-US/sessions/2b5c3675-36e7-4d70-bf4e-3d98c913a018?source=sessions)
* [The mechanics of Real-Time Intelligence in Microsoft Fabric](https://build.microsoft.com/en-US/sessions/514d3926-7f9a-412b-a095-93d6e5df0bca?source=sessions)
* [Integrating Azure AI and Microsoft Fabric for Next-Gen AI Solutions](https://build.microsoft.com/en-US/sessions/91971ab3-93e4-429d-b2d7-5b60b2729b72?source=sessions)
 
## Agenda
 
Note: in today's workshop, we are skipping **Lab 03: Building a DW using Pipelines**.
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/b2dc58b3-5666-4817-9b00-b949480bedf5)
 
***
 
## Lab Notes
 
Existem algumas alterações nos laboratórios que são abordadas nas notas abaixo.
 
## LAB 01: Ingesting Data using RTA
 
### Exercise 1: Environment Setup
 
A aplicação responsável por gerar os dados que vamos utilizar nesse laboratório usa um Azure Container Instance e um Event Hub, ambos já estão implatados no Azure. Porem, se você quiser implantar isso por conta própria, poderá fazê-lo usando sua própria assinatura do Azure (cerca de US$ 1,70/dia) ou utilizar uma avaliação gratuita do Azure Pass usando o código promocional que está disponível na guia Recursos. No entanto, para ajudar a simplificar, você pode utilizar a aplicação que já está executando, você não precisará de acesso ao Azure. Os detalhes da conexão estão incluídos aqui - cada participante é atribuído a um Consumer Group.
 
Se estiver usando o Event Hub do grupo, você só precisará executar essas tarefas abaixo:

* **Tarefa 1: Faça login na conta do Power BI e inscreva-se para a avaliação gratuita do Microsoft Fabric**
* **Tarefa 2: Iniciar a avaliação do Microsoft Fabric**
* Pular a tarefa 3: resgatar o Azure Pass
* Pular a tarefa 4: atribuição de função de colaborador do Log Analytics
* Pular a tarefa 5: criar conta de armazenamento
* **Tarefa 6: Criar a workspace do Fabric**
  * Ao nomear sua workspace, você provavelmente precisará tornar o nome globalmente exclusivo. Em vez de "RealTimeWorkspace", adicione suas iniciais, seu primeiro nome ou altere o nome como achar melhor. Todos os itens do workshop de hoje irão para essa workspace.
* Pular a tarefa 7: implantar o aplicativo por meio da instância de contêiner do Azure
* **Tarefa 8: Obter dados com o Eventstream**
 
Se você quiser implantar o aplicativo gerador de ações por conta própria, siga estas etapas:
 
* **Tarefa 1: Entre na conta do Power BI e inscreva-se para a avaliação gratuita do Microsoft Fabric**
* Tarefa 2: Iniciar a avaliação do Microsoft Fabric
* Tarefa 3: Resgatar o Azure Pass
* Pular a tarefa 4: Atribuição de função de colaborador do Log Analytics
* Pular a tarefa 5: criar conta de armazenamento
* Tarefa 6: Criar a workspace do Fabric
  * Ao nomear sua workspace, você provavelmente precisará tornar o nome globalmente exclusivo. Em vez de "RealTimeWorkspace", adicione suas iniciais, seu primeiro nome ou altere o nome como achar melhor. Todos os itens do workshop de hoje irão para essa workspace.
* **Tarefa 7: Implantar o aplicativo por meio da Instância de Contêiner do Azure**
* Tarefa 8: Obter dados com o Eventstream


 
Na **Tarefa 6**, dê um nome exclusivo para a workspace, como "Workshop-initials" ou algo semelhante:
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/467d5e14-36aa-4862-ab45-5ab3d5e214c6)
 
Na **Tarefa 8**, certifique-se de fazer o seguinte:
* Use os seguintes detalhes de conexão do Event Hub:
 
| Setting | Value|
| -------- | ------- |
| Event Hub namespace| **ehns-spbrazil-fabricworkshop** | 
| Event Hub| **stockeventhub** |
| SAS Name| **stockeventhub_sas** |
| SAS Key| **E7wLz2Qi2qyiZl8WFLMP/vQro+/PppxFf+AEhIq2MYU=** |
| Consumer Group | Atribuído individualmente |
 
* Exclua o nome de conexão padrão e forneça um nome exclusivo na caixa de texto, como *EventHub-Connection-{initials}* ou similar::
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/4e093598-c03b-4b1b-b07e-a3916c7542a1)
 
### Exercise 2: KQL Database Configuration and Ingestion
 
#### Task 1: Create KQL Database
 
Como parte dos novos recursos de Real-Time Intelligence, todos os bancos de dados KQL fazem parte de um EventHouse. Algumas capturas de tela podem não ter sido atualizadas.
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/6860198d-ef85-4f41-a933-cfe45e611977)
 
***
 
## LAB 02: Using KQL and building reports
 
No additional notes at this time.
 
***
 
## Lab 03: Building a DW using Pipelines
 
Este é um laboratório opcional. É claro que você pode trabalhar nele se o tempo permitir ou fora do laboratório!)
 
***
 
## Lab 04: Building a Data Lakehouse
 
Ao trabalhar com o notebook **Lakehouse 2: Build Aggregation Tables**, muitas etapas se concentram no uso do Data Activator para ajudar a formatar e agregar os dados. O Data Wrangler é uma ferramenta visual que gera código Python em uma nova célula do notebook. Se você quiser economizar tempo, cada uma das três etapas do Data Wrangler foi concluída e está comentada, e deve se parecer com a imagem abaixo:
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/60655d53-d012-478e-9229-4e5abdf348ff)
 
Se você preferir evitar passar pelas etapas do Data Wrangler ou enfrentar qualquer desafio, poderá usar o código na célula comentada. Destaque todo o código na célula (**CTRL-A**) e, em seguida, descomente todo o código (**CTRL-/**). Isso pode ser feito para qualquer uma ou todas as etapas do Data Wrangler.
 
***
 
## Lab 05: Getting Started with Building a ML Model in Fabric
 
Existem 3 notebooks usados neste laboratório:
 
| Notebook | Purpose |
| -------- | ------- |
| DS 1 - Build Model | Builds an ML model using Prophet, examines data, and stores model in MLflow |
| DS 2 - Predict Stock Prices | Consume MLflow from a notebook |
| DS 3 - Forecast All | Build predictions for all stock symbols and store in a Delta table |
 
O DS 1 e o DS 2 são, em grande parte, exemplos/teoria de como trabalhar com dados, avaliar os resultados e armazenar o modelo no MLflow. O DS 3 é o notebook principal que gera previsões para todas as ações e armazena os resultados na tabela **stocks_prediction**.
 
Para economizar tempo: se você estiver interessado principalmente na análise de dados, na configuração de experimentos e na comparação de execuções no MLflow, concentre-se no DS 1 e no DS 2. Se estiver mais interessado em obter as previsões e criar um modelo semântico e um relatório, considere pular diretamente para o DS 3 (que é o **Exercício 3: Solução na prática** no laboratório).
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/f40d2b5a-43b0-4f9f-91fc-49f223360d85)
