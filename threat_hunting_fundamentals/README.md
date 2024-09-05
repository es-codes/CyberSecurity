# Fundamentos de Threat Hunting: Uma Abordagem Proativa

Recentemente, aprofundei meus conhecimentos sobre threat hunting, um processo essencial para reduzir o "dwell time" – o tempo médio entre uma violação e sua detecção, que pode chegar a semanas ou até meses. Essa abordagem destaca a ineficácia crescente de estratégias de segurança cibernética tradicionais, que costumam ser reativas e baseadas apenas em defesa. É aqui que o threat hunting se destaca, adotando uma postura ofensiva e proativa.

## Definição e Objetivo do Threat Hunting
 
O threat hunting é uma prática liderada por humanos, muitas vezes baseada em hipóteses, que examina sistematicamente os dados de rede para identificar ameaças avançadas e furtivas que escapam das soluções de segurança existentes. O objetivo principal é reduzir significativamente o dwell time, detectando ameaças o mais cedo possível no ciclo de vida do ataque. Essa postura proativa ajuda a prevenir a consolidação de ameaças dentro da infraestrutura e permite neutralizá-las rapidamente.

## Como o Threat Hunting se Relaciona com o Incident Handling?

Durante o curso, ficou claro como o threat hunting e o incident handling se complementam. No estágio de Preparação, o time de threat hunting define regras claras de engajamento e procedimentos operacionais, o que pode ser integrado às políticas existentes de incident handling. Durante a fase de Detecção e Análise, os hunters podem aumentar a eficácia da investigação, ajudando a identificar indicadores de compromisso (IoCs) que poderiam passar despercebidos. No estágio de Contenção, Erradicação e Recuperação, a participação dos hunters pode variar de acordo com as práticas de cada organização. No entanto, sua expertise pode ser valiosa em qualquer fase, incluindo o pós-incidente, oferecendo recomendações para fortalecer a postura de segurança da organização.

## Estrutura Ideal de uma Equipe de Threat Hunting

Aprendi também sobre a composição ideal de uma equipe de threat hunting, que deve ser cuidadosamente planejada para incluir uma variedade de habilidades e perspectivas:

.Threat Hunter: Profissionais com conhecimento profundo do cenário de ameaças e das TTPs dos ciberadversários.

.Analista de Inteligência de Ameaças: Responsáveis por coletar e analisar dados de diversas fontes para prever tendências futuras e fornecer insights valiosos.

.Respondentes a Incidentes: Gerenciam situações de incidentes identificadas pelos hunters, incluindo contenção, erradicação e recuperação.

.Especialistas em Forense Digital: Envolvidos na análise técnica detalhada dos incidentes, como análise de malware e engenharia reversa.

.Cientistas e Analistas de Dados: Examinam grandes volumes de dados para identificar padrões e tendências.

.Engenheiros de Segurança: Projetam a infraestrutura de segurança da organização e trabalham com hunters para implementar ferramentas e técnicas.

.Analistas de Segurança de Rede: Especialistas em identificar anomalias no tráfego de rede.

.Gerente de SOC: Supervisiona as operações do time de threat hunting, garantindo a coordenação eficiente.

## Quando Realizar Threat Hunting?

O curso destacou que o threat hunting deve ser uma atividade contínua e proativa, mas também pode ser intensificado em casos específicos, como:

.Surgimento de novas informações sobre um adversário ou vulnerabilidade.

.Associação de novos indicadores a um adversário conhecido.

.Detecção de múltiplas anomalias de rede.

.Atividades de resposta a incidentes.

.Ações periódicas proativas para detectar ameaças latentes.

.Relação entre Avaliação de Riscos e Threat Hunting

.A avaliação de riscos é uma ferramenta essencial para guiar as atividades de threat hunting, permitindo priorizar os esforços em ativos críticos, compreender melhor o cenário de ameaças e identificar vulnerabilidades. Utilizar ferramentas avançadas, como sistemas SIEM, é fundamental para obter uma visão holística do status de segurança da organização e apoiar a caça às ameaças.

Concluí que a integração entre a avaliação de riscos e o threat hunting fortalece a postura de segurança cibernética, reduzindo o dwell time, mitigando danos potenciais e aprimorando a defesa da organização.

# Exemplo de Threat Hunting: Processos e Descobertas Recentes

Nos últimos meses, a abordagem ao Threat Hunting foi refinada para melhorar a eficácia na identificação de ameaças que poderiam passar despercebidas pelas defesas tradicionais. A seguir, estão algumas das investigações recentes conduzidas e os insights obtidos durante o processo.

## Hipótese de Caça 1: Exploração de Vulnerabilidade no Servidor Web

A primeira hipótese formulada focou na possibilidade de um ator de ameaça ter explorado uma vulnerabilidade conhecida em um dos servidores web da organização. Com base em relatórios recentes de inteligência de ameaças e atualizações sobre novas CVEs, identificou-se um risco potencial relacionado a uma falha de execução remota de código (RCE) em um servidor web específico.

Para testar essa hipótese, foram coletados logs de acesso do servidor web e realizada uma análise detalhada de padrões de requisições suspeitas, como tentativas de injeção de comandos ou acessos a diretórios não autorizados. Foram utilizadas consultas específicas no SIEM para buscar anomalias nesses logs. Durante a análise, várias tentativas de acesso a um diretório sensível logo após uma série de requisições de teste foram encontradas, indicando um possível reconhecimento inicial. A descoberta foi escalada para a equipe de resposta a incidentes para uma investigação mais aprofundada e uma possível correção da vulnerabilidade.

## Hipótese de Caça 2: Comunicação C2 Via DNS

A segunda hipótese envolveu a suspeita de que um atacante poderia estar usando um canal de comando e controle (C2) através de consultas DNS. Esse método é conhecido por ser uma técnica furtiva para exfiltrar dados ou controlar máquinas comprometidas sem chamar muita atenção. Para investigar essa possibilidade, foram configurados alertas no SIEM para capturar e analisar consultas DNS que apresentassem características anômalas, como um número excessivo de requisições para domínios raros ou recentemente registrados.

Durante a análise, foi notado um volume incomum de consultas para um domínio recém-registrado. As consultas ocorreram em intervalos regulares, algo típico de um beacon C2. A origem dessas consultas foi investigada e descobriu-se que estavam relacionadas a um único endpoint. O caso foi escalado para isolamento do endpoint e uma análise de malware para determinar se havia uma infecção em andamento.

## Hipótese de Caça 3: Acesso Não Autorizado em Contas de Serviço

A terceira hipótese estava relacionada a possíveis acessos não autorizados usando contas de serviço. Contas de serviço são frequentemente alvos de ataque devido aos privilégios elevados e à sua presença constante em ambientes corporativos. O SIEM foi utilizado para monitorar logons de contas de serviço em horários não convencionais ou fora dos padrões normais de uso.

Foram identificados logons suspeitos de uma conta de serviço "svc-backup" ocorrendo fora do horário comercial e de um local de IP incomum. Esses eventos foram correlacionados com mudanças em algumas configurações críticas de backup, levantando uma bandeira vermelha. A investigação revelou que o IP de origem estava associado a uma VPN pública, potencialmente comprometida. A conta foi temporariamente bloqueada, e uma investigação completa foi iniciada para entender a extensão do comprometimento.

## Hipótese de Caça 4: Escalonamento de Privilégio Através de Scripts Maliciosos

A última hipótese focou em um possível escalonamento de privilégio usando scripts maliciosos. O uso de scripts maliciosos é uma técnica comum para que invasores obtenham privilégios administrativos em sistemas vulneráveis. Foram configurados alertas para detectar execuções de scripts Powershell que utilizassem parâmetros frequentemente associados a ataques, como bypass de política de execução e uso de ofuscação.

Durante a análise, foram encontrados vários scripts Powershell executados com parâmetros suspeitos em uma máquina de desenvolvimento. A revisão detalhada indicou que o script estava tentando adicionar um usuário administrativo ao grupo local de administradores. Esse comportamento sugeriu uma tentativa de escalonamento de privilégio. A máquina foi isolada imediatamente, e o usuário responsável foi contatado para explicações. Confirmou-se que se tratava de uma tentativa de ataque, e medidas corretivas foram implementadas para evitar futuros incidentes.

Conclusão

Essas hipóteses e investigações destacam a importância de um processo proativo de Threat Hunting em um ambiente de segurança cibernética. Com cada caça, foi possível não apenas identificar e mitigar ameaças, mas também refinar continuamente as técnicas e melhorar a postura de segurança da organização. Além disso, documentar cada descoberta e compartilhar os insights com a equipe ajuda a fortalecer as defesas contra futuros ataques.

Aprendizado no Laboratório: Fundamentos de Inteligência de Ameaças

No laboratório sobre Fundamentos de Inteligência de Ameaças, explorei como a Cyber Threat Intelligence (CTI) fortalece a defesa contra ciberataques. A CTI transforma uma abordagem reativa em uma proativa, fornecendo insights críticos para o Centro de Operações de Segurança (SOC).


# Aprendizado no Laboratório: Fundamentos de Inteligência de Ameaças

Durante o laboratório sobre Fundamentos de Inteligência de Ameaças, pude aprofundar minha compreensão sobre o papel crucial da Cyber Threat Intelligence (CTI) na proteção contra ciberataques. O objetivo principal da nossa equipe de CTI é evoluir de uma postura defensiva reativa para uma abordagem proativa e antecipatória, fornecendo insights essenciais para o Centro de Operações de Segurança (SOC).

## Princípios Fundamentais da CTI

A CTI se torna uma parte vital da nossa estratégia de cibersegurança através de quatro princípios fundamentais:

Relevância: Em meio a uma infinidade de fontes de informação, desde postagens em redes sociais até relatórios de fornecedores de segurança, a verdadeira importância dos dados está na sua relevância para a nossa organização. Por exemplo, uma vulnerabilidade reportada em um software que não utilizamos ou que não é usado por nossos parceiros de confiança diminui a urgência para medidas defensivas.

Temporalidade: A comunicação rápida da inteligência para nossa equipe de defesa é essencial para a implementação de medidas mitigadoras eficazes. A informação tem um valor que diminui com o tempo - dados descobertos recentemente são mais valiosos, enquanto indicadores "envelhecidos" podem já não ser utilizados pelo adversário ou ter sido resolvidos pela organização afetada.

Ação: A inteligência deve gerar insights acionáveis para a equipe de defesa. Se a inteligência não oferece diretrizes claras para ação, seu valor diminui. Deve ser analisada até que forneça insights relevantes, oportunos e acionáveis para nossa defesa. Inteligência não acionável pode levar a um ciclo não produtivo de análise, muitas vezes chamado de "ciclo de sorvete auto-lambedor".

Precisão: Antes de disseminar qualquer inteligência, ela deve ser verificada quanto à precisão. Indicadores incorretos, atribuições erradas ou Táticas, Técnicas e Procedimentos (TTPs) falhos podem resultar em perda de tempo e recursos valiosos. Se a precisão de qualquer informação for incerta, deve ser rotulada com um indicador de confiança, garantindo que nossa equipe de defesa esteja ciente das possíveis imprecisões.

Combinando esses quatro fatores, a inteligência obtida nos permite:

.Obter insights sobre possíveis operações e campanhas adversárias que podem estar mirando nossa organização.
.Enriquecer nosso banco de dados através da análise feita por analistas de CTI e outros defensores da rede.
.Descobrir TTPs adversários, possibilitando o desenvolvimento de medidas mitigadoras eficazes e aprimorando nossa compreensão do comportamento adversário.
.Fornecer aos tomadores de decisão dentro da organização informações pertinentes para uma tomada de decisão impactante relacionada às operações comerciais.
.Monitoramento Contínuo: Acompanhar e ajustar conforme necessário.

## Categorias da Inteligência de Ameaça

À medida que essas informações são compiladas, elas se transformam em inteligência, que pode ser classificada em três categorias diferentes, cada uma com graus variados de relevância para diferentes equipes dentro da nossa organização. Essas categorias são:

Inteligência Estratégica: Consumida por executivos, VPs e outros líderes da empresa, visa alinhar a inteligência diretamente com os riscos da empresa para informar decisões. Fornece uma visão geral das operações do adversário ao longo do tempo, mapeando TTPs e o modus operandi do adversário.

Inteligência Operacional: Inclui também TTPs de um adversário, fornecendo informações sobre campanhas adversárias com mais detalhes do que a inteligência estratégica. É produzida para pessoal de gerenciamento intermediário e trabalha para responder o "Como?" e "Onde?".

Inteligência Tática: Fornece informações imediatas e acionáveis para defensores de rede agirem rapidamente, incluindo detalhes técnicos sobre ataques que ocorreram ou podem ocorrer em breve.

É essencial entender que há um grau de sobreposição entre essas três tipos de inteligência, o que justifica a representação em um diagrama de Venn. A inteligência tática contribui para formar uma visão operacional e estratégica, e vice-versa.

## Avaliação de Habilidades: Caça ao Stuxbot

Neste laboratório, explorei as táticas evolutivas do malware Stuxbot, especialmente sua versão mais recente. O foco foi entender como o Stuxbot utiliza diferentes técnicas para manter a persistência e se mover lateralmente dentro de uma rede. Aqui está um resumo dos principais aprendizados:

## Principais Descobertas

Implantação via C:\Users\Public: As versões mais recentes do Stuxbot utilizam o diretório C:\Users\Public para implantar ferramentas adicionais. Essa tática ajuda na disseminação do malware por diferentes partes do sistema.

Chaves de Registro para Persistência: O Stuxbot usa chaves de registro para garantir que persista mesmo após reinicializações do sistema. Esse método de persistência é uma técnica comum utilizada por malwares para manter sua presença.

PowerShell Remoting para Movimento Lateral: Para movimento lateral, o Stuxbot utiliza PowerShell Remoting. Isso permite que o malware navegue pela rede e acesse componentes críticos, como controladores de domínio.

## Dados Disponíveis

O laboratório utilizou a pilha Elastic como nossa solução SIEM. Através do recurso “Discover”, acessei logs de várias fontes, incluindo:

.Logs de Auditoria do Windows: Encontrados sob o padrão de índice windows*.

.Logs do System Monitor (Sysmon): Também categorizados sob windows*.

.Logs do PowerShell: Indexados sob windows*.

.Logs do Zeek: Classificados sob o padrão de índice zeek*.

## Tarefas e Consultas

Transferência Lateral de Ferramentas: Criei uma consulta KQL para buscar transferências de ferramentas para C:\Users\Public. O documento relevante destacou um campo user.name associado à ferramenta transferida que começa com "r".

Chaves de Registro de Inicialização: Desenvolvi uma consulta KQL para identificar execuções de inicialização ou logon através de chaves de registro. Os resultados da consulta forneceram o conteúdo do campo registry.value relacionado à primeira ação de persistência baseada em registro.

PowerShell Remoting: Outra consulta KQL foi criada para detectar o uso de PowerShell Remoting para movimento lateral. Essa consulta ajudou a identificar o campo winlog.user.name associado às ações de remoting em direção ao DC1.

## Conclusão

Este laboratório ofereceu insights práticos sobre como detectar e analisar táticas avançadas de malware. Ao aplicar consultas KQL na pilha Elastic, aperfeiçoei minhas habilidades em identificar indicadores-chave das atividades do Stuxbot, como movimento lateral e técnicas de persistência. Essas habilidades são cruciais para monitorar e defender efetivamente contra ameaças cibernéticas sofisticadas.
