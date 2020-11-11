# LondriBajaEletronics2019

> Este repositório conta um pouco a jornada da evolução do subsistema de elétrica da equipe LondriBaja entre novembro de 2018 e março de 2020. Os detalhes de implementação de cada uma das partes do projeto citadas estão sendo adicionadas em repositórios individuais, as quais seus links são citados aqui ao longo desse texto.

(Esse README ainda está sendo escrito)

## Jornada

Em Agosto de 2018, novatos na equipe, que naquele momento estava sem membros no subsistema de elétrica, topamos o desafio de mesmo sem estar cursando graduação nas áreas afins, estudar o necessário para conseguir levar um sistema de segurança robusto para a competição, que não gerasse alto número de rechecks para a equipe. A competição Regional Sul seria em outubro. Trabalhamos duro aqueles dois meses para isso. Conseguimos finalizar alguns dias antes da competição, e observando as necessidades da equipe para aquele momento, projetamos um simples sistema para aferir níveis baixos de combustível, de fabricação manual, bem simples, mas que funcionava. Conseguimos chegar na competição e o resultado foi 0 rechecks, e conseguimos uma boa nota, para sermos os marinheiros de primeira viagem. O feedback dos juízes e experiências trocadas com as demais equipes nos mostravam que o segredo era começar com pouco, mas fazer bem feito. Isso nos deu ânimo e mostrava que estávamos no caminho certo. 

Iniciamos então uma nova fase. Definimos então algumas metas. O prazo final era a competição Nacional em março de 2020. Colheríamos mais feedbacks dos juízes nas competições Nacional de 2019, em fevereiro, e Regional Sul de 2020.
Implementar o primeiro sistema de instrumentação desenvolvido pela equipe
Otimizar a proteção contra líquidos do então atual sistema de segurança da equipe
Desenvolver um sensor de baixo custo para aferir o deslocamento da suspensão
Desenvolver um aplicativo que facilitasse o processo de fazer inspeções de segurança
Redução de massa total do sistema

### A instalação elétrica

Toda a instalação elétrica do veículo foi novamente projetada em busca de reduzir a massa total do sistema, torná-la mais robusta e mais resistente a líquidos, e mais modular em busca de acelerar o processo de manutenção. O chicote foi fabricado  com tubo anti chamas, conectores IP66, prensa-cabos.Foram projetadas caixas vedadas, fabricadas com impressão 3d e borrachas para a proteção contra líquidos dos botões de emergência.

### Sensoriamento

Seguindo o princípio de fazer algo enxuto, simples porém bem feito, para essa primeira versão foi optado por aferir 3 grandezas: RPM do motor, velocidade do veículo e nível de combustível. Os métodos escolhido para RPM foi extrair os pulsos gerados na bobina da vela, para a velocidade foi o posicionamento de um sensor indutivo no eixo da roda para contagem de pulsos, e para o combustível posicionar sensores capacitivos digitais externos ao tanque (visto que a competição proíbe utilizar sensores dentro do tanque). Mais detalhes podem ser vistos nos repositórios individuais (a serem criados).

### Projeto Elétrico e Eletrônico

O diagrama abaixo mostra como ficou organizado o sistema de segurança junto ao sistema eletrônico. 

O sistema eletrônico foi dividido em duas PCB’s, uma ECU, principal, que cuida do do controle das tensões, conecta o microcontrolador, que trabalha os dados, as entradas dos sensores, e expõe os dados para a Serial e outra PCB, que é um display com leds e displays de 7 segmentos que é utilizada como painel. 
O controle das tensões é feito por dois reguladores buck por apresentarem eficiências mais altas. O microcontrolador, um ATMega328p, foi escolhido para garantir o andamento do projeto no futuro da equipe. Como em nossa universidade não temos alunos cursando a área de eletrônica e afins, essa escolha facilita para que o projeto não fique estagnado até que futuros novos membros possam aprender a programar microcontroladores de baixo nível, pelo fato desse microcontrolador poder ser programado com a biblioteca Arduino, que tem uma grande comunidade e é de fácil aprendizagem. E mesmo assim, se adequa aos requisitos do projeto, atendendo as necessidades do projeto. Os esquemáticos e detalhes da implementação podem ser extraídos nos repositório X.

Foram projetadas caixas vedadas, como as do sistema de segurança, para o sistema de instrumentação. Foram desenvolvidas duas versões das caixas de proteção nesse tempo. A primeira foi projetada em forma de gaveta, em busca de fácil manutenção caso necessário, e guardava ambas as duas PCBs. É a implementada no veículo ao fim deste projeto. A segunda versão separa as PCB’s em duas caixas, em busca de maior modularidade, e substitui os conectores que são utilizadas na primeira versão, por sensores automotivos que se conectam diretamente a PCB, para tornar a solução mais automotiva, e retirar os prensa-cabos. Essa versão será fabricada em 2020, mas o projeto já está pronto ao fim deste ciclo. 

<p align="center"><img src="https://github.com/ViniciusGambi/LondriBajaEletronics2019/blob/master/.github/eletric-eletronic.jpg?raw=true"></p>

### User Interface e Registro de dados

Para exibir os dados aferidos pelo sistema de instrumentação, foi desenhada uma interface para a exibição dos dados. Para o registro de dados para análises, foi desenvolvido um aplicativo Android que faz registro (como um data logger) dos dados expostos na Serial. (link aqui)

### Validação

Todas as grandezas aferidas foram validadas e ajustadas com equipamentos com valores de referência confiáveis. A validação de RPM do motor foi feita por meio de um tacômetro óptico em bancada. Os valores de combustível foram validados em laboratório. Para a velocidade, pela falta de acesso a um equipamento calibrado de referência, desenvolvemos uma aplicação que extrai os dados de velocidade do aplicativo Waze (por ser a fonte mais segura acessível a equipe) por processamento de imagem, e os guarda registrados em função do tempo em uma planilha para a análise e comparação posterior.

### Extra

A partir de uma necessidade do subsistema de suspensão, que precisava de dados de deslocamento da suspensão, verificamos a possibilidade da compra de um sensor para isso. Como o valor escapava ao orçamento, buscamos uma forma de aferir essa grandeza com um sensor de baixo custo. Inicialmente realizamos alguns testes com um acelerômetro MPU6050, entretanto em virtude da baixa precisão do sensor, o acúmulo de erros ao longo do tempo tornava inviável a integral da aceleração para retirar o deslocamento. Desenvolvemos então uma solução melhor, barata, mais robusta, e com grande precisão com impressão 3D, duas barras lineares e um encoder óptico aproveitados de uma impressora velha. Esse projeto pode ser visualizado nesse outro repositório (a ser upado). 

Outro projeto desenvolvido no ano foi um aplicativo para tornar fácil e rápido o processo da inspeção de segurança, possibilitando que a equipe os faça com mais frequência, com o objetivo de ajudar na redução dos rechecks da equipe. O link do repositório desse projeto será adicionado aqui.
