# Explorando os Fundamentos do SIEM e sua Evolução na Segurança Cibernética

Recentemente, aprofundei meus conhecimentos em Segurança da Informação e Gestão de Eventos (SIEM) através de laboratórios no HackTheBox, explorando como essas soluções são cruciais para a proteção dos ativos digitais de uma organização. Aprendi que o SIEM integra o gerenciamento de informações de segurança (SIM) e o gerenciamento de eventos de segurança (SEM) para oferecer uma abordagem abrangente na detecção e resposta a ameaças.

# O que é SIEM e como ele funciona?

O SIEM permite que profissionais de TI detectem ataques cibernéticos em tempo real ou até mesmo antes de ocorrerem. O sistema coleta dados de diversas fontes – como dispositivos de rede, PCs e servidores – normalizando e agregando essas informações para facilitar a análise. Um ponto interessante é que o SIEM não apenas identifica ameaças potenciais, mas também gera alertas contextuais que ajudam a equipe de segurança a focar nos eventos mais críticos, minimizando falsos positivos.

## Evolução e Capacidades do SIEM

Foi fascinante entender a evolução do SIEM, desde suas raízes em SIM e SEM, até se tornar uma ferramenta essencial de segurança moderna. Primeiramente, as tecnologias SIM se concentravam na coleta e armazenamento de logs, enquanto SEM focava na correlação e notificação de eventos. A combinação dessas tecnologias deu origem ao SIEM, que agora é amplamente utilizado para agregar, armazenar e analisar eventos de segurança em uma abordagem mais unificada.

## Requisitos de Negócio e Casos de Uso

Um dos aspectos mais relevantes do SIEM é a agregação e normalização de logs. Isso oferece uma visão centralizada dos dados de segurança e ajuda as equipes de SOC a identificar padrões e anomalias que possam indicar ameaças potenciais. Outro ponto crucial é a capacidade de gerar alertas em tempo real, permitindo respostas rápidas e eficazes a incidentes.

## Benefícios do Uso de Soluções SIEM

Os benefícios de implementar uma solução SIEM são evidentes. Sem ela, uma organização pode perder eventos críticos de segurança e enfrentar grandes desafios para responder a incidentes. Com um SIEM devidamente calibrado, é possível detectar ataques antes que eles ocorram, reduzindo custos e danos potenciais.

Concluo que, para organizações reguladas, como aquelas em setores financeiros e de saúde, o SIEM não é apenas uma ferramenta de segurança, mas também uma exigência de conformidade. A experiência me mostrou como o SIEM desempenha um papel fundamental na proteção dos ativos digitais e na manutenção da conformidade com normas como ISO e HIPAA.



# 1. Criação de Dashboards e Visualizações no SIEM: Tentativas de Logon Falhadas

Em minha recente exploração no HackTheBox, trabalhei na criação de dashboards e visualizações no SIEM para monitorar tentativas de logon falhadas. O objetivo era entender como os dashboards no SIEM organizam e exibem dados de forma significativa, ajudando a identificar possíveis ameaças e anomalias em tempo real.

## Iniciando a Criação de um Dashboard e Visualização

Primeiro, acessei o sistema-alvo e naveguei até o endereço do SIEM (http://[Target IP]:5601). No painel de navegação, cliquei em "Dashboard" e excluí o dashboard existente chamado "SOC-Alerts". Em seguida, iniciei a criação de um novo dashboard clicando no botão "Create new dashboard".

Para criar a nossa primeira visualização, cliquei em "Create visualization". Antes de configurar a visualização, ajustei o intervalo de tempo para "last 15 years" usando o ícone do calendário e apliquei o filtro.

![image](https://github.com/user-attachments/assets/cf745311-0366-488d-a637-7f18f9710dd4)


## Configurando a Visualização: Filtrando Tentativas de Logon Falhadas

Ao configurar a visualização, notei alguns elementos importantes:

Opções de Filtro: Utilizei o filtro para focar nos eventos específicos de falha de logon, por exemplo, especificando o ID de evento 4625, que indica tentativas de logon falhadas em sistemas Windows.

Data Set (Index): Especificamos "windows*" no padrão de índice para garantir que estamos trabalhando com os dados corretos, provenientes de fontes Windows da infraestrutura.

Barra de Pesquisa: Usei a barra de pesquisa para confirmar a presença de campos específicos, como user.name.keyword, garantindo que estávamos acessando os dados certos para nossa análise.

Tipo de Visualização: Optei pela visualização de "Tabela", que melhor se adequava à exibição das tentativas de logon falhadas por usuário.

Depois de configurar as "Rows" e selecionar "Count" como métrica, a tabela começou a exibir os dados. Adicionei uma configuração adicional para mostrar a máquina onde ocorreram as tentativas de logon falhadas, usando o campo host.hostname.keyword.

![image](https://github.com/user-attachments/assets/0da1bf56-a44e-4daf-ae19-35c1935e5cef)


## Aprimorando a Visualização 

Supondo que recebi algumas sugestões de refinamento de um SOC Manager para melhorar a clareza e a precisão da visualização:

.Nomes de Colunas Claros: Renomeei as colunas para torná-las mais descritivas.

.Inclusão do Tipo de Logon: Adicionei o campo winlog.logon.type.keyword para identificar o tipo de logon tentado.

.Ordenação dos Resultados: Configurei a visualização para ordenar os resultados.

.Exclusão de Usuários Específicos e Contas de Computador: Utilizei filtros adicionais para excluir usuários específicos, como "DESKTOP-DPOESND" e "WIN-OK9BH1BCKSD", além de excluir contas de computador usando uma consulta KQL específica.

![image](https://github.com/user-attachments/assets/1dc2a174-fede-4f09-a7c9-c24fc7c20cdd)


.Finalmente, após todas as modificações, salvei a visualização com um título apropriado e a adicionei ao dashboard. Essa prática me ajudou a entender melhor como personalizar visualizações no SIEM para atender às necessidades específicas de segurança da organização.

![image](https://github.com/user-attachments/assets/1461d16e-f0bc-445b-91c1-42b605d53cdc)


Conclusão

A experiência de criar dashboards e visualizações do zero no SIEM me mostrou o quão poderoso é ter ferramentas de monitoramento em tempo real para detectar e responder a ameaças. Com as melhorias baseadas no feedback do SOC Manager, aprendi a refinar a exibição dos dados e garantir que os resultados sejam precisos e úteis para o time de segurança. Essa prática é essencial para manter a segurança e a conformidade em ambientes corporativos.

# 2.Configuração de Visualização no SIEM: Tentativas de Logon Falhadas (Usuários Desativados)

Neste segundo exemplo de visualização no SIEM, meu objetivo foi criar uma visualização para monitorar tentativas de login falhadas contra usuários desativados.

Usei o termo "falhadas" porque não é possível realizar login com um usuário desativado, então nunca haverá sucesso, mesmo que as credenciais estejam corretas. Em casos onde as credenciais corretas são usadas, os logs do Windows conterão um valor de SubStatus adicional, 0xC0000072, que indica a razão da falha.

Para começar, naveguei até o final da seção e cliquei em "Clique aqui para iniciar o sistema alvo!". Em seguida, fui até o endereço http://[IP do Alvo]:5601, cliquei no menu de navegação lateral e selecionei "Dashboard".

Um dashboard pré-configurado estava visível. Cliquei no ícone de "lápis" para editar.

## Iniciando a Criação da Visualização

Para iniciar a criação da primeira visualização, cliquei em "Create visualization". Ao fazer isso, uma nova janela apareceu com várias opções e configurações.

Nesta janela, quatro elementos principais chamaram minha atenção:

Filtro de dados: Usei essa opção para filtrar os dados antes de criar o gráfico. No meu caso, queria exibir apenas tentativas de logon falhadas contra usuários desativados. Assim, filtrei pelos IDs de evento 4625 – Tentativa de logon falhada em um sistema Windows, como no exemplo anterior. Além disso, considerei o SubStatus (campo winlog.event_data.SubStatus) configurado para 0xC0000072, indicando falha devido a logon com usuário desativado.

![image](https://github.com/user-attachments/assets/cd9d4e61-6d72-4d21-a917-5e2b34c8cf89)

Conjunto de dados (índice): Especifiquei o padrão de índice "windows*" para focar em dados relevantes. Muitas vezes, os dados de diferentes fontes da infraestrutura (como rede, Windows, Linux, etc.) são separados em índices diferentes.

Barra de busca: Usei esta barra para verificar rapidamente se o campo user.name.keyword estava presente no conjunto de dados selecionado, garantindo que estava trabalhando com os dados corretos.

Menu de visualização: Escolhi o tipo de visualização "Table" para esta análise. Depois, cliquei em "Rows" para escolher os elementos específicos a serem incluídos na visualização em tabela.

Configurando a Visualização em Tabela

Configurei as "Rows" para incluir o nome do usuário desativado, o host que gerou o evento de logon falhado, e a contagem de vezes que o evento ocorreu.

![image](https://github.com/user-attachments/assets/67bdefd3-b568-4815-a5c1-18d6ad2d4ab5)

No final, cliquei em "Save and return" para adicionar a nova visualização ao dashboard. Isso me permitiu visualizar as tentativas de logon falhadas contra usuários desativados de forma clara e organizada, ajudando a monitorar eventos potencialmente suspeitos na rede.

# 3.Criação de Dashboards e Visualizações no SIEM: Logons RDP Bem-Sucedidos Relacionados a Contas de Serviço

Neste exemplo, o foco é monitorar logons RDP bem-sucedidos, especificamente relacionados a contas de serviço. Normalmente, contas de serviço não são usadas para logons RDP em ambientes corporativos, então, qualquer evento desse tipo requer atenção especial. Fui informado pelo time de Operações de TI que todas as contas de serviço no ambiente começam com o prefixo "svc-". Como essas contas geralmente possuem altos privilégios, precisamos monitorar rigorosamente como são utilizadas.

Para criar esta visualização, baseei-me no evento de log do Windows 4624, que indica quando uma conta foi logada com sucesso. Acesse o sistema alvo, vá para http://[IP do Alvo]:5601, clique no botão de navegação lateral e, em seguida, clique em "Dashboard". Ao editar o dashboard pré-configurado, clicamos no botão "Create visualization" para iniciar a criação de nossa nova visualização.

Na nova janela, há cinco elementos principais que precisamos observar:

Filtro de Dados: Vamos filtrar apenas os eventos de logon RDP bem-sucedidos (ID de evento 4624). O logon deve ser do tipo RemoteInteractive (campo winlog.logon.type). Este filtro nos ajuda a focar somente nos logons de RDP relacionados a contas de serviço.

![image](https://github.com/user-attachments/assets/b256fba3-0cd7-42ba-a2ae-0d0e90c83330)

![image](https://github.com/user-attachments/assets/ab8e2851-a51f-4205-bfb3-d4701a6d34ba)


Seleção do Conjunto de Dados (Index): Utilizamos o padrão de índice windows*, para garantir que estamos utilizando apenas dados pertinentes ao ambiente Windows.

Barra de Pesquisa: Usamos a barra de pesquisa para confirmar a existência do campo user.name.keyword dentro do conjunto de dados selecionado, garantindo que estamos trabalhando com os dados corretos.

Tipo de Visualização: Para esta visualização, selecionei o tipo "Table", que é mais apropriado para exibir dados detalhados como logons de contas de serviço.

Configuração dos "Rows" e "Metrics": Configurei o campo de "Rows" para incluir informações como a conta de serviço (user.name.keyword), a máquina onde ocorreu o logon (host.hostname.keyword), e o IP da máquina que iniciou o logon (related.ip.keyword). Em "Metrics", selecionei "count" como métrica, para contar o número de ocorrências.

Por fim, incluí um filtro adicional para garantir que apenas logons relacionados a contas de serviço fossem exibidos, utilizando a query KQL: user.name: svc-*. Dessa forma, conseguimos visualizar quatro colunas na tabela: a conta de serviço, a máquina onde o logon ocorreu, o IP da máquina que iniciou o logon, e o número de vezes que o evento ocorreu. Ao salvar a visualização, ela é adicionada ao dashboard, permitindo monitorar de perto qualquer atividade suspeita envolvendo contas de serviço.

![image](https://github.com/user-attachments/assets/c1297c73-6d3e-42ab-9194-ce611ff157b6)

# 4.Exemplo de Visualização no SIEM: Usuários Adicionados ou Removidos de um Grupo Local (Dentro de um Período Específico)

No quarto exemplo de visualização no SIEM, meu objetivo foi criar uma visualização para monitorar adições ou remoções de usuários do grupo local "Administradores" entre 5 de março de 2023 e a data atual.

Para essa visualização, utilizei os seguintes logs de eventos do Windows:

4732: Um membro foi adicionado a um grupo local com habilitação de segurança
4733: Um membro foi removido de um grupo local com habilitação de segurança

Primeiro, acessei o sistema alvo clicando em "Click here to spawn the target system!" e naveguei para http://[IP do Alvo]:5601. Lá, cliquei no menu de navegação lateral e selecionei "Dashboard".

No dashboard pré-configurado, cliquei no ícone de "lápis"/edição.

Agora, para iniciar a criação da minha primeira visualização, cliquei no botão "Create visualization". Uma nova janela surgiu com várias opções e configurações.

Havia cinco pontos importantes a observar nesta janela:

Opção de Filtro: Configurei um filtro para exibir apenas as adições ou remoções de usuários do grupo local "Administradores". Usei um filtro para considerar apenas os IDs de eventos 4732 e 4733. Também configurei o filtro para considerar apenas eventos onde o grupo local é o "Administradores".

![image](https://github.com/user-attachments/assets/b3fbc643-4bb4-4239-b34a-217236d9784c)


Campo de Índice: Especifiquei o índice windows* no campo "Index pattern", pois os dados eram separados por índices, como rede, Windows, Linux, etc.

Barra de Pesquisa: Utilizei a barra de pesquisa para verificar a existência do campo user.name.keyword no conjunto de dados. Isso ajudou a confirmar que eu estava acessando o campo correto e trabalhando com dados precisos.

Menu Suspenso de Tipo de Visualização: Selecionei a opção "Table" para a visualização. Após escolher "Table", cliquei em "Rows" para configurar os elementos de dados específicos a serem incluídos na visualização.

Configuração das Métricas: No menu "Metrics", selecionei "count" como a métrica desejada.

Adicionei configurações adicionais para a tabela:

.Usuário Adicionado ou Removido: Utilizei o campo winlog.event_data.MemberSid.keyword para identificar qual usuário foi adicionado ou removido do grupo.

.Grupo: Verifiquei que a ação foi realizada no grupo "Administradores" usando o campo group.name.keyword.

.Ação Realizada: Determinei se o usuário foi adicionado ou removido usando o campo event.action.keyword.

.Máquina: Adicionei a coluna host.name.keyword para mostrar em qual máquina a ação ocorreu.

.Após configurar essas opções, cliquei em "Save and return". A nova visualização foi adicionada ao dashboard.

![image](https://github.com/user-attachments/assets/d8704f65-892f-4894-85c7-5d20b6271f12)

Finalmente, ajuste o escopo da visualização para monitorar as adições ou remoções de usuários no grupo local "Administradores" no período específico de 5 de março de 2023 até a data atual.

![image](https://github.com/user-attachments/assets/9e47e592-af2b-4772-9bfd-a66aa8abff31)

Cliquei no botão "Save" para garantir que todas as minhas edições fossem salvas e persistissem no dashboard.

# Exemplo de Avaliação de Habilidades: Revisão de Dashboard e Exercício de Pensamento Crítico

Simulando uma integração como analista SOC Tier 1 na Eagle, comecei a revisar as visualizações do dashboard para entender melhor o ambiente e identificar possíveis problemas de segurança. A seguir, compartilho como analisei as visualizações e os insights obtidos:

## Visualização 1: Tentativas de Logon Falhadas (Todos os Usuários)

Minha primeira tarefa foi revisar a visualização de tentativas de logon falhadas para todos os usuários. Essa visualização pode revelar potenciais ataques de força bruta, especialmente se houver um padrão de várias tentativas falhadas de um mesmo usuário ou múltiplos usuários tentando se conectar de um único dispositivo. Embora o cenário não apresente um padrão claro de ataques de força bruta, notei uma anomalia relacionada à conta "sql-svc1". Isso chamou minha atenção, e decidi investigar mais a fundo para garantir que não haja atividades suspeitas associadas a essa conta.

![image](https://github.com/user-attachments/assets/a2b25afd-5218-48db-bf99-4dbd5b7c2f6b)

## Visualização 2: Tentativas de Logon Falhadas (Usuário Desativado)

Em seguida, analisei as tentativas de logon falhadas para usuários desativados. Aqui, identifiquei um incidente onde o usuário "Anni" tentou autenticar-se mesmo com a conta desativada. Isso é preocupante e pode indicar uma tentativa de acesso não autorizada. Com base nessa informação, decidi que era necessário investigar a origem dessa tentativa de logon e verificar se há alguma brecha de segurança.

![image](https://github.com/user-attachments/assets/25b78174-8a18-44d6-82f9-beda90ab5b7d)

## Visualização 3: Tentativas de Logon Falhadas (Somente Usuários Administradores)

A terceira visualização focou em tentativas de logon falhadas apenas para usuários administradores. O objetivo era verificar se todas as falhas de logon ocorreram exclusivamente em estações de trabalho privilegiadas (PAWs) ou Controladores de Domínio. Identificar qualquer evento fora desses ambientes pode indicar uma possível violação das políticas de acesso. Revi os eventos e confirmei que todos ocorreram em PAWs e Controladores de Domínio, conforme esperado.

![image](https://github.com/user-attachments/assets/2221b65d-61d2-4f0d-9646-8cd192df2755)

## Visualização 4: Logon RDP para Conta de Serviço

A visualização seguinte revelou logons RDP para contas de serviço. Dado que as contas de serviço desempenham funções específicas e especializadas, qualquer atividade suspeita pode indicar um problema de segurança. Analisei as atividades relacionadas a essas contas e, felizmente, não encontrei irregularidades que exigissem uma ação imediata.

![image](https://github.com/user-attachments/assets/2724ef7e-f2cf-4df7-a536-419fadd20f22)

## Visualização 5: Usuário Adicionado ou Removido de um Grupo Local

Revisei a visualização de adições ou remoções de usuários em grupos locais. Notei que um administrador havia incorporado um indivíduo, identificado apenas pelo SID, ao grupo "Administradores". Isso é algo que deve ser investigado. Decidi que era apropriado escalar essa situação para um analista Tier 2/3 para uma análise mais detalhada ou consultar o departamento de Operações de TI, considerando a potencial gravidade de adicionar um SID desconhecido ao grupo de administradores.

![image](https://github.com/user-attachments/assets/a1230b77-7d05-4375-b448-ddd28aaa8a06)

## Visualização 6: Logon de Administrador Não a partir de PAW

Para a visualização de logons de administradores fora de PAWs, verifiquei se algum logon de administrador foi realizado fora das estações de trabalho privilegiadas. Identificar tais eventos pode sinalizar uma violação das políticas de acesso. Se encontrasse qualquer logon de administrador fora de PAWs, a decisão seria escalar isso para um analista Tier 2/3 ou consultar o departamento de Operações de TI.

![image](https://github.com/user-attachments/assets/2f78d756-c394-4274-9a41-c6c5ce804525)

## Visualização 7: Logins SSH

Finalmente, analisei os logins SSH. Lembrei que a conta root não deve ser utilizada, então procurei por qualquer login SSH realizado pela conta root. Caso encontrasse atividades dessa conta, isso indicaria uma violação das políticas e eu teria que investigar mais a fundo para assegurar a integridade do ambiente.

![image](https://github.com/user-attachments/assets/39b84b01-7eec-45f8-bf34-30bcdb222bf8)
