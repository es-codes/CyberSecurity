# Explorando o Básico dos Logs de Eventos do Windows

No laboratório "Windows Event Logs", aprofundei meu conhecimento sobre o sistema de logging do Windows. Os Logs de Eventos do Windows são fundamentais para o sistema operacional, armazenando registros de componentes variados, como o próprio sistema, aplicações, serviços e provedores ETW (Event Tracing for Windows). Como profissionais de cibersegurança, utilizamos esses logs de forma intensiva para análise e detecção de intrusões.

## Estrutura e Acesso aos Logs de Eventos

Os logs são categorizados em grupos como "Application", "System" e "Security", para organizar eventos de acordo com sua origem ou finalidade. Utilizei o Visualizador de Eventos do Windows, uma ferramenta nativa que permite explorar esses logs, ou APIs específicas, como a Windows Event Log API, para acessá-los programaticamente.

Dentro do Visualizador de Eventos, observei os cinco logs padrão do Windows: "Application", "Security", "Setup", "System" e "Forwarded Events". Cada um tem uma função específica — como monitorar erros de aplicações, eventos de segurança e informações do sistema. A seção "Forwarded Events" é única, exibindo dados de logs encaminhados de outras máquinas, o que é útil para administradores que buscam uma visão centralizada.

![image](https://github.com/user-attachments/assets/46f48afa-56ec-4e6b-bb6b-51539e1f1375)

## Componentes de um Log de Evento

Cada entrada em um Log de Eventos do Windows possui componentes essenciais, como o "Log Name" (nome do log), "Source" (origem do evento), "Event ID" (identificador único do evento), "Level" (severidade do evento), "Keywords" (categorias amplas para classificação), "User" (usuário conectado quando o evento ocorreu), e dados em formato XML, que oferecem uma descrição estruturada e detalhada do evento.

Foquei na análise de eventos de segurança, como o Event ID 4624, que indica um logon bem-sucedido. Esse log contém detalhes importantes como "Logon ID", permitindo correlacionar este logon com outros eventos que compartilham o mesmo ID, e o "Logon Type", que indica o tipo de logon (por exemplo, um logon de serviço iniciado pelo sistema).

![image](https://github.com/user-attachments/assets/0d8b93e9-ffc0-4b66-be9a-125c75339221)

## Criando Consultas Personalizadas com XML

Para otimizar a análise, explorei a criação de consultas XML personalizadas no Visualizador de Eventos. Utilizando o campo "Logon ID", filtrei eventos correlacionados e aprofundei minha investigação, focando em eventos específicos como o Event ID 4907, que indica mudanças na política de auditoria de um objeto.

Essas consultas são cruciais para refinar a análise e focar nos eventos mais relevantes, ajudando a desvendar atividades suspeitas ou anômalas. Por exemplo, utilizando uma query XML personalizada, consegui identificar mudanças de permissões de arquivos e correlacionar essas alterações com processos suspeitos.

## Logs de Eventos Úteis do Windows

Além disso, fiz um levantamento de eventos críticos que merecem atenção constante. Aqui estão alguns dos eventos de maior relevância:

.Event ID 1074: Indica quando e por que o sistema foi desligado ou reiniciado, útil para detectar atividades suspeitas de desligamento.

.Event ID 4625: Registra tentativas de logon falhas, o que pode indicar tentativas de ataque por força bruta.

.Event ID 7045: Registra a instalação de novos serviços, muitas vezes usada por malwares para persistência.

## Conclusão e Aplicação

Compreender a estrutura e a utilização dos Windows Event Logs é essencial para a detecção de intrusões e análise de incidentes. A habilidade de criar consultas personalizadas e interpretar logs de eventos específicos aprimora a capacidade de resposta a ameaças, permitindo ações proativas na defesa do ambiente. Este laboratório reforçou minha confiança na análise detalhada de eventos e em técnicas de correlação de dados, elementos críticos para uma postura de segurança eficaz.

# Analise de Atividades Maliciosas com Sysmon e Logs de Eventos

Neste laboratório de "Sysmon e Event Logs", aprofundei meu conhecimento na detecção e análise de atividades maliciosas através do monitoramento detalhado do sistema com o Sysmon, uma ferramenta essencial da Sysinternals Suite. Sysmon é projetado para capturar eventos críticos de segurança que não são cobertos pelos logs padrão do Windows, permitindo uma visibilidade mais profunda sobre atividades suspeitas no sistema.

## Implementação e Configuração do Sysmon

Comecei instalando e configurando o Sysmon em um ambiente controlado. Utilizei um arquivo de configuração XML personalizado para ajustar os eventos que desejava monitorar, como a criação de processos, conexões de rede, carregamento de módulos, entre outros. Este arquivo de configuração é fundamental, pois permite um nível de granularidade alto, filtrando eventos irrelevantes e focando apenas em atividades potencialmente maliciosas.

A configuração adequada do Sysmon melhora significativamente a detecção de anomalias. Por exemplo, monitorar eventos como "Event ID 1" (criação de processo) e "Event ID 10" (criação de threads remotas) fornece insights valiosos sobre comportamentos que podem indicar a presença de um malware, como um processo tentando injetar código em outro.

## Análise de Logs com o Visualizador de Eventos

Com o Sysmon configurado, passei a analisar os logs gerados diretamente no Visualizador de Eventos do Windows. Observei eventos específicos que geralmente indicam atividades maliciosas. Foquei, por exemplo, no "Event ID 3" (conexões de rede), que pode ser crucial para identificar conexões de saída suspeitas, um sinal comum de comunicação com servidores de comando e controle (C2).

Além disso, observei o "Event ID 13" (modificação de chaves do Registro), essencial para identificar tentativas de persistência, e o "Event ID 21" (criação de novos drivers ou serviços), muitas vezes usados por atacantes para garantir que o malware sobreviva a reinicializações.

## Correlacionando Eventos e Construindo Histórias de Ataque

Através da correlação de eventos diferentes, pude construir histórias detalhadas de possíveis ataques. Por exemplo, ao correlacionar um "Event ID 1" (criação de processo) com um "Event ID 7" (carregamento de imagem), foi possível identificar quando um executável malicioso iniciou e quais bibliotecas ele carregou, ajudando a compreender melhor seu comportamento.

![image](https://github.com/user-attachments/assets/c8bc5b66-4c10-4707-89fb-1e8c8be55a01)

Para tornar esta análise ainda mais eficaz, utilizei queries personalizadas em XML no Visualizador de Eventos. Por meio dessas queries, refinei a busca de eventos específicos, filtrando eventos como "Event ID 10" para identificar injeções de thread remotas, que frequentemente indicam técnicas de pós-exploração usadas por atacantes para mover lateralmente dentro de uma rede.

## Aplicação de Técnicas de Caça às Ameaças

Uma parte importante do laboratório foi aplicar técnicas de Threat Hunting utilizando os logs gerados pelo Sysmon. Identifiquei padrões comuns a ataques conhecidos, como a execução de scripts de PowerShell com argumentos codificados, ou tentativas de esvaziamento da memória LSASS, uma técnica usada por malwares para roubar credenciais.

Ao aplicar filtros avançados e correlacionar eventos, como o "Event ID 1" (criação de processo) e "Event ID 22" (modificação de arquivos executáveis), pude detectar atividades que geralmente são ignoradas em uma análise superficial. Este nível de detalhe é essencial para encontrar ameaças que possam passar despercebidas pelos controles de segurança tradicionais.

## Conclusão e Melhoria Contínua

Este laboratório reforçou a importância de ferramentas como o Sysmon para a detecção proativa de ameaças e a análise detalhada de atividades maliciosas. A configuração correta e o uso estratégico de queries para filtrar e correlacionar eventos me permitiram identificar potenciais ataques com mais precisão. Esse aprendizado é fundamental para melhorar a postura de segurança em ambientes corporativos, permitindo respostas mais rápidas e eficazes a incidentes.

Durante o meu trabalho com ferramentas de monitoramento e análise de segurança, descobri que o Event Tracing for Windows (ETW) é um recurso frequentemente subestimado, mas extremamente poderoso. A habilidade de extrair e analisar informações detalhadas sobre o funcionamento interno do Windows pode fazer uma grande diferença na detecção e resposta a incidentes de segurança.

# O Que é o ETW?

ETW é uma ferramenta de rastreamento de alto desempenho integrada ao Windows, projetada para capturar e analisar uma vasta gama de eventos que ocorrem no sistema. Ele utiliza um mecanismo de buffer e log no núcleo do sistema operacional, permitindo a coleta de dados em tempo real de aplicativos e drivers, tanto no modo de usuário quanto no modo de núcleo.

Ao explorar o ETW, fiquei impressionado com a profundidade das informações que ele pode fornecer. Em vez de depender apenas dos logs tradicionais, que têm um escopo mais limitado, o ETW oferece um panorama detalhado das atividades do sistema, incluindo chamadas de sistema, criação e término de processos, atividades de rede, e modificações em arquivos e registros.

## Arquitetura e Componentes do ETW

![image](https://github.com/user-attachments/assets/ce355f2b-b297-4d0f-b8b0-f14dc72dd371)

A arquitetura do ETW é baseada em um modelo de publicação e assinatura, e envolve os seguintes componentes principais:

Controladores: Gerenciam as operações do ETW, como iniciar e parar sessões de rastreamento e ativar ou desativar provedores. Ferramentas como o logman são usadas para gerenciar essas sessões.

Provedores: São responsáveis por gerar eventos e podem ser de vários tipos, como provedores baseados em MOF, WPP, manifestos ou TraceLogging. Cada tipo oferece uma abordagem diferente para a geração de eventos.

Consumidores: Assinam eventos de interesse e processam ou analisam esses eventos. Normalmente, os eventos são gravados em arquivos ETL, que servem como armazenamento durável para análise posterior.

Canais: Contêineres lógicos que organizam e filtram eventos, permitindo que os consumidores se concentrem apenas nos eventos relevantes para suas necessidades.

## Utilizando o ETW para Monitoramento de Segurança

Na prática, utilizar o ETW para monitoramento de segurança revelou-se extremamente útil. Ferramentas como logman permitem criar e gerenciar sessões de rastreamento, o que me permitiu configurar a captura de eventos de interesse específicos, como atividades de rede ou execução de processos. Provedores como Microsoft-Windows-Kernel-Process e Microsoft-Windows-Kernel-Network foram especialmente valiosos para detectar comportamentos suspeitos e atividades de rede não autorizadas.

Além disso, descobri que há provedores restritos, como o Microsoft-Windows-Threat-Intelligence, que fornecem dados altamente granulares sobre ameaças de segurança, mas que só podem ser acessados por processos com permissões especiais. Essa restrição ajuda a proteger informações sensíveis, mas também destaca a importância de ter as permissões adequadas para acessar esses dados cruciais.

## Conclusão

Explorar o ETW me mostrou o quão poderoso e abrangente ele pode ser para a detecção e resposta a incidentes de segurança. Ao integrar o ETW em nossas estratégias de monitoramento, podemos obter uma visão mais detalhada e contextualizada das atividades do sistema, melhorando significativamente nossa capacidade de identificar e responder a ameaças.

# Skill Assessment of Windows Event Log & Finding Evil

## Tarefa 1: Identificando o Processo de DLL Hijacking

Ao examinar os logs no diretório "C:\Logs\DLLHijack", precisei determinar qual processo foi responsável por executar um ataque de DLL hijacking.

Passo a Passo:

Modifiquei o arquivo de configuração do Sysmon para incluir Imageload Onmatch = exclusive.
Atualizei a configuração com o comando sysmon.exe -c ....
No Visualizador de Eventos, abri os logs salvos e naveguei até a pasta correspondente. A análise focou no Event ID 7, que está relacionado ao carregamento de imagens, incluindo detalhes como o caminho da imagem, o hash e os metadados. Utilizando a opção de busca, consegui identificar o processo responsável.

## Tarefa 2: Identificando o Processo que Executou Código PowerShell Não Gerenciado
Em seguida, precisava encontrar o processo que executou código PowerShell não gerenciado, analisando os logs no diretório "C:\Logs\PowershellExec".

Passo a Passo:

Com o Visualizador de Eventos aberto, carreguei os logs salvos do diretório especificado.
Como essa tarefa também envolvia imagens carregadas, filtrei os eventos para o Event ID 7. Usando a dica relacionada ao .Net, consegui identificar o processo que executou o código PowerShell.

## Tarefa 3: Identificando o Processo que Injetou Código PowerShell

A terceira tarefa estava interligada à anterior. Eu precisava identificar o processo que injetou no processo que executou o código PowerShell não gerenciado.

Passo a Passo:

Utilizei o Event ID relacionado ao Source Process ID e ao nome (CreateRemoteThread).
Analisei o evento correto que lidava com o ID do processo pai para encontrar o processo responsável pela injeção de código.

## Tarefa 4: Identificando o Processo que Realizou um Dump do LSASS
A quarta tarefa exigia a identificação do processo que executou um dump de LSASS, analisando os logs em "C:\Logs\Dump".

Passo a Passo:

Esta tarefa era um verdadeiro teste de paciência, especialmente se estivesse tentando resolvê-la em 60 minutos devido a possíveis problemas de rede ou RDP.
Reconfigurei o arquivo de configuração do Sysmon, desta vez alterando o ProccessAcess onmatch para Exclude.
Abri os logs salvos e utilizei a dica "lsass.exe" para filtrar pelo Event ID 10. Embora esse método pudesse ser demorado, também considerei usar a ferramenta Chainsaw em linha de comando, mas optei pelo Visualizador de Eventos.

## Tarefa 5: Identificando um Processo com Relação Estranha de Pai-Filho

A última tarefa envolvia encontrar um processo que foi usado para executar temporariamente código com uma relação incomum de processo pai-filho, analisando os logs em "C:\Logs\StrangePPID".

Passo a Passo:

Carreguei o arquivo .evtx da pasta especificada.
Embora a ferramenta Chainsaw fosse uma alternativa, achei que usar o Visualizador de Eventos foi mais fácil para esta tarefa, apesar de ter demorado algumas horas.
Analisei o evento relacionado à criação de threads (CreateThread Detected) para identificar o processo relevante.
