# Definição e Escopo do Tratamento de Incidentes

O tratamento de incidentes (IH) se tornou uma parte essencial da capacidade defensiva de qualquer organização contra crimes cibernéticos. Embora medidas protetivas sejam constantemente implementadas para prevenir ou reduzir a quantidade de incidentes de segurança, a capacidade de tratamento de incidentes é indiscutivelmente necessária para qualquer organização que não pode se dar ao luxo de comprometer a confidencialidade, integridade ou disponibilidade de seus dados. Algumas organizações optam por implementar essa capacidade internamente, enquanto outras confiam em provedores terceirizados para suporte contínuo ou conforme necessário. Antes de mergulharmos no mundo dos incidentes de segurança, vamos definir alguns termos e estabelecer um entendimento comum sobre eles.

Um evento é uma ação que ocorre em um sistema ou rede, como o envio de um e-mail por um usuário, um clique do mouse, ou um firewall permitindo uma solicitação de conexão. Um incidente é um evento com uma consequência negativa, como uma falha no sistema ou acesso não autorizado a dados sensíveis. Incidentes podem também ocorrer devido a desastres naturais, falhas de energia, entre outros.

Não há uma definição única para o que é um incidente de segurança de TI, e, portanto, varia entre as organizações. Definimos um incidente de segurança de TI como um evento com uma intenção clara de causar dano contra um sistema de computador. Exemplos de incidentes incluem roubo de dados, roubo de fundos, acesso não autorizado a dados e instalação e uso de malware e ferramentas de acesso remoto. O tratamento de incidentes é um conjunto claramente definido de procedimentos para gerenciar e responder a incidentes de segurança em um ambiente de computador ou rede.

É importante notar que o tratamento de incidentes não se limita apenas a incidentes de intrusão. Outros tipos de incidentes, como aqueles causados por insiders maliciosos, problemas de disponibilidade e perda de propriedade intelectual, também fazem parte do escopo do tratamento de incidentes. Um plano abrangente de tratamento de incidentes deve abordar vários tipos de incidentes e fornecer medidas adequadas para identificar, conter, erradicar e recuperar a partir deles, restaurando as operações normais de negócios o mais rapidamente e eficientemente possível.

# Cadeia de Ataques Cibernéticos

![image](https://github.com/user-attachments/assets/f612d868-fb47-4ea1-82da-e6d2b406cf23)


Antes de começarmos a falar sobre o tratamento de incidentes, precisamos entender o ciclo de vida dos ataques (também conhecido como cadeia de ataque cibernético). Esse ciclo descreve como os ataques se manifestam. Compreender esse ciclo nos fornece informações valiosas sobre até onde um atacante está na rede e o que eles podem ter acesso durante a fase de investigação de um incidente.

A cadeia de ataque cibernético consiste em sete estágios diferentes: Reconhecimento, Armazenamento, Entrega, Exploração, Instalação, Comando e Controle, e Ação ou Objetivo. O estágio de reconhecimento é onde o atacante escolhe seu alvo e realiza a coleta de informações sobre ele. No estágio de armazenamento, o malware é desenvolvido e incorporado a um tipo de carga útil. A entrega é o momento em que o exploit ou carga útil é entregue à vítima. Na exploração, o exploit é ativado. A instalação envolve a execução do malware no sistema comprometido, e o comando e controle estabelecem a capacidade de acesso remoto. O estágio final é onde o atacante atinge seu objetivo, que pode variar desde exfiltrar dados confidenciais até implantar ransomware.

É importante entender que os adversários não operam de maneira linear. Algumas fases anteriores podem ser repetidas várias vezes. O nosso objetivo é impedir que o atacante avance na cadeia de ataque, idealmente em um dos estágios iniciais.

# Visão Geral do Processo de Tratamento de Incidentes

![image](https://github.com/user-attachments/assets/7cdb6a54-a995-45ae-8da8-ba93385a67a9)

Agora que estamos familiarizados com a cadeia de ataque cibernético e seus estágios, podemos prever melhor os próximos passos em um ataque e sugerir medidas apropriadas contra eles. Assim como a cadeia de ataque cibernético, o processo de tratamento de incidentes também é composto por diferentes estágios, definidos como o processo de tratamento de incidentes. Este processo define a capacidade das organizações para se preparar, detectar e responder a eventos maliciosos.

De acordo com o NIST, o processo de tratamento de incidentes consiste em quatro estágios distintos: Preparação, Detecção e Análise, Resposta, e Recuperação. Os responsáveis pelo tratamento de incidentes passam a maior parte do tempo nos estágios de preparação e detecção e análise, melhorando continuamente suas habilidades e buscando novos eventos maliciosos. Quando um evento malicioso é detectado, passamos para o estágio de resposta, sempre mantendo recursos nos dois primeiros estágios para não interromper a capacidade de preparação e detecção.

A preparação inclui a criação de uma capacidade interna para o tratamento de incidentes e a implementação de medidas protetivas adequadas, como endurecimento de endpoints e servidores, gerenciamento de acesso privilegiado e autenticação multifatorial. É crucial ter uma equipe de tratamento de incidentes qualificada, uma força de trabalho treinada, políticas e documentação claras, ferramentas apropriadas e capacidade de adquirir recursos rapidamente durante um incidente.

Durante a investigação, o objetivo é descobrir a vítima inicial e criar uma linha do tempo do incidente, identificar as ferramentas e malware utilizados pelo adversário e documentar os sistemas comprometidos e as ações do adversário. Após a investigação, a recuperação envolve a criação e implementação de um plano de recuperação para restaurar as operações normais de negócios. Quando um incidente é totalmente tratado, um relatório detalhado é emitido e atividades de "lições aprendidas" são realizadas para evitar a repetição de incidentes semelhantes no futuro.

Na segunda parte do laboratório, aprofundamos nossa preparação e procedimentos para lidar com incidentes de segurança. Um aspecto fundamental dessa fase é garantir que temos as ferramentas certas para agir de forma eficiente durante um incidente. Isso inclui:

Estação de trabalho adicional: Cada membro da equipe de resposta a incidentes deve ter uma estação de trabalho dedicada para preservar imagens de disco e arquivos de log, realizar análises de dados e investigar sem restrições. Esses dispositivos devem ser manuseados com cuidado para não introduzir riscos na organização.

Ferramentas de aquisição e análise forense: Incluem ferramentas para captura e análise de imagem digital, captura de memória, resposta ao vivo e análise de logs.

Proteção de rede e hardware: Deve-se ter cabos de rede, switches, bloqueadores de escrita e drives rígidos para imagem forense, além de ferramentas para reparo e desmontagem de dispositivos, se necessário.

Documentação e comunicação: É essencial ter formulários de cadeia de custódia e um sistema de rastreamento de tíquetes independente da infraestrutura da organização. A documentação deve ser segura e o sistema de resposta a incidentes deve estar pronto para uso imediato.

Um ponto crítico é ter um "jump bag" – uma bolsa com todas as ferramentas necessárias prontamente disponíveis para uma resposta rápida. A documentação e comunicação devem ser independentes da infraestrutura da organização, assumindo que todos os sistemas podem estar comprometidos e a comunicação pode estar sendo monitorada.

# Medidas de Proteção Recomendadas:

DMARC: Implementar DMARC para proteger contra phishing, rejeitando e-mails que parecem vir de sua organização. É importante testar exaustivamente para evitar bloqueio de e-mails legítimos.

Endereços de e-mail e filtragem: Ajustar regras de filtragem para aumentar a proteção contra e-mails falsificados, especialmente de domínios não próprios.

Fortalecimento de Endpoints (EDR): Adotar práticas como desativar LLMNR/NetBIOS, implementar LAPS, restringir o uso do PowerShell e adotar regras de Redução de Superfície de Ataque (ASR). Utilizar produtos EDR que integram com AMSI pode melhorar a visibilidade.

Proteção de Rede: Segmentar a rede para evitar a propagação de uma violação e utilizar sistemas IDS/IPS com interceptação SSL/TLS para identificar tráfego malicioso. Garantir que apenas dispositivos aprovados possam se conectar à rede.

Gestão de Identidades e Acesso: Implementar gestão de identidade, MFA e boas práticas de senhas. Utilizar frases de senha e MFA para proteger acessos administrativos.

Escaneamento de Vulnerabilidades: Realizar escaneamentos contínuos e remediar vulnerabilidades críticas. Segmentar sistemas vulneráveis se a aplicação de patches não for possível.

Treinamento de Conscientização dos Usuários: Treinar usuários para reconhecer comportamentos suspeitos e realizar testes periódicos, como simulações de phishing e dispositivos USB abandonados.

Avaliação de Segurança do Active Directory: Realizar avaliações para identificar configurações incorretas e vulnerabilidades expostas, com foco na prevenção de escalonamento de privilégios.

Exercícios de Equipe Roxa (Purple Team): Realizar exercícios que combinam o time de ataque (Red Team) e defesa (Blue Team) para identificar vulnerabilidades e testar a capacidade de resposta.

# Fase de Detecção e Análise:

Na fase de detecção e análise, o foco é identificar e entender os incidentes de segurança. Isso envolve:

Fontes de Detecção: Monitorar comportamentos anômalos por funcionários, alertas de ferramentas (EDR, IDS, Firewall), atividades de caça a ameaças e notificações de terceiros.

Níveis de Detecção: Implementar detecção em múltiplos níveis – perímetro de rede, rede interna, endpoints e aplicações.

# Investigação Inicial:

Ao detectar um incidente, é crucial realizar uma investigação inicial para entender o contexto:

Informações a Coletar: Data/hora do incidente, método de detecção, descrição do incidente, sistemas impactados e ações tomadas.

Linha do Tempo do Incidente: Criar uma linha do tempo organizada para acompanhar os eventos e entender o contexto da atividade maliciosa.

# Severidade e Extensão do Incidente:

Responder a perguntas sobre o impacto e a extensão do incidente ajuda a priorizar e escalar a resposta:

.Impacto e Requisitos de Exploração

.Sistemas Críticos Afetados

.Número de Sistemas Impactados

.Presença do Exploit no Ambiente

.Capacidades de Propagação do Exploit

# Confidencialidade e Comunicação:

Manter a confidencialidade das informações sobre o incidente é crucial. A comunicação deve ser gerenciada com cuidado e feita através de canais seguros.

Para analisar um incidente, é essencial entender como e por que ele ocorreu. A investigação envolve:

Criação e Uso de IOCs: Indicadores de Compromisso documentam artefatos de um incidente. Ferramentas como OpenIOC e Yara podem ser usadas para criar e buscar IOCs.

![image](https://github.com/user-attachments/assets/3879e535-b700-4a75-a61c-2f58fe34db57)


Identificação de Novas Pistas e Sistemas Impactados: Buscar e priorizar novos sistemas e pistas com base nos IOCs encontrados.

Coleta e Análise de Dados: Coletar e analisar dados dos sistemas impactados, seja por resposta ao vivo ou análise pós-desligamento, garantindo a preservação das evidências.

Essa abordagem detalhada e sistemática ajuda a entender a ameaça, proteger a organização e melhorar a resposta a incidentes futuros.

# Contenção, Erradicação e Recuperação

Na fase de contenção, o objetivo é impedir que o incidente cause mais danos. Dividimos as ações em contenção de curto prazo e de longo prazo. A contenção de curto prazo envolve medidas rápidas para limitar o impacto imediato, como isolar sistemas, desconectar da rede ou modificar nomes de DNS. Essas ações ajudam a conter o dano e oferecem tempo para desenvolver uma estratégia de remediação mais sólida. Se necessário, fazemos imagens forenses dos sistemas para preservar evidências. A contenção de longo prazo inclui ações mais duradouras, como alteração de senhas, aplicação de regras de firewall e instalação de sistemas de detecção de intrusões. Essas medidas são importantes, mas ainda não resolvem o incidente completamente; é necessário seguir com a erradicação e recuperação.

Após a contenção, a erradicação visa remover completamente a causa raiz do incidente e qualquer remanescente do problema. Isso pode incluir a remoção de malware detectado, a reconstrução de sistemas e a restauração a partir de backups. Durante a erradicação, também aplicamos patches adicionais e realizamos atividades de fortalecimento dos sistemas para evitar futuras ameaças. É uma etapa crucial para garantir que o adversário seja completamente removido do ambiente.

Na fase de recuperação, restauramos os sistemas para operação normal. Verificamos se os sistemas estão funcionando como esperado e se contêm todos os dados necessários antes de colocá-los de volta no ambiente de produção. Os sistemas restaurados são monitorados intensamente para detectar qualquer atividade suspeita, pois sistemas comprometidos podem ser alvos novamente. É importante observar logons incomuns, processos inesperados e alterações no registro que normalmente seriam modificadas por malware. A recuperação pode levar meses, especialmente em grandes incidentes, e é abordada em fases, começando com medidas rápidas e avançando para mudanças permanentes para melhorar a segurança.



