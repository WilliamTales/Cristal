# Documentação dos Fluxos da Cristal

> Chatbot inteligente criado por Weni.

## Sumário

[Legenda](#_tiho6rf6i2rf)

[1 - Regras de negócio](#_q9kues6fc77t)

[2 - Evoluções](#_g5vlr88z085d)

[3 - Globals](#_dasppzh8cf4k)

[4 - Triggers](#_lr67culogd15)

[5 - Campos de contato](#_lqjqnhcy8pfg)

[1 - Mensagem](#_hgqyc3oausxf)

[2 - Atividade](#_6lra3v2k6qh2)

[3 - Atividade no chat](#_xdos3r29uerr)

[4 - Código da sala](#_2bjdx1uid1jl)

[5 - Departamento](#_s6yzlyni66f2)

[6 - Documento](#_dzsvjr480jlu)

[7 - Finalidade](#_lkvurlo20vea)

[8 - ID do cliente](#_joxionf5hjh5)

[9 - Privacidade](#_sbt3tokluuvl)

[10 - Telefone](#_6znjjd5z67j6)

[11 - Título](#_ou5dsah0uprj)

[12 - Último login](#_zd59tqs70dcm)

[6 - Fluxos e Fluidez](#_wmkt6w9x6bw)

[1 - Nova mensagem](#_fs8j614vy933)

[2 - Boas vindas](#_kjq3zokd6alu)

[3 - Cumprimentos e despedidas](#_8pt7opswl1c4)

[4 - Menu principal](#_2goz9a268cz8)

[5 - Algo mais](#_k8xldcbuc9xo)

[6 - Inatividade](#_fk7kbqzijltw)

[7 - Encerramento](#_2vyof9gmoba1)

[8 - Baixa convicção](#_g94hc6fk0gua)

[9 - Classificação](#_xv0xlm1ov2ao)

[10 - Classificador](#_gcmjhsy3arli)

[11 - Intenções](#_hy6vh7kbii7z)

[12 - Funções não suportadas](#_spkc4zlqlw4v)

[13 - Extrato por email](#_aujwf7htmjb3)

[14 - Lead](#_9qgbxrcjy6si)

[15 - Atendimento humano](#_ewx09zxt5f1k)

[16 - Obter dados](#_z9qutz88piuo)

[17 - Obter dados - Nome](#_527kd3ph1iz4)

[18 - Obter dados - Telefone](#_h8cpsx2j771t)

[19 - Obter dados - eMail](#_vcsb053x0si8)

[20 - Credenciamento](#_w9kerbclzc5y)

[21 - Status Financeiro](#_q07rovfu356s)

[22 - Verifica centros de custos](#_unnmro6299g7)

[23 - Verifica data do intervalo](#_auaeg6z027av)

[Lógica para parcelas futuras:](#_3r2wb4vh8gy)

[Lógica para parcelas atrasadas:](#_zgophj2irm9b)

[Lógica para outras parcelas:](#_gbqvksb7lrs9)

[24 - Resposta - Parcela Sienge](#_psy28kyenpzu)

[Para a categoria das parcelas recentes:](#_v3yjadtwprxt)

[Para a categoria das parcelas atrasadas:](#_tsx3ky71h1c6)

[Para a categoria das parcelas futuras:](#_c7vs7xj0sjpx)

[Para a categoria da parcela atual:](#_1aih6vy5jo3k)

[25 - Intervalo por extenso](#_4mjgp3imbhhf)

[26 - Status Financeiro - Back4app](#_2p9dsim8gkml)

[27 - Resposta - Parcela Back4app](#_fvf6uah9wd3o)

[28 - Segunda via por email](#_3a8peuxw1ak0)

[Para cenários Back4app:](#_wf7xivhve5i0)

[Para cenários Sienge:](#_q4cqq5ui4d2e)

[29 - Linha digitavel + link](#_nagx1zk6zucc)

[Para cenários Back4app:](#_6zzejgrr1xee)

[Para cenários Sienge:](#_orkmsp67wx90)

[30 - RocketChat - Criar sala](#_o5t5h2qfd4cn)

[31 - RocketChat - Enviar mensagem](#_c4b8wxrzh5oa)

[32 - RocketChat - Mídias](#_d68zaqo4ocp0)

[33 - RocketChat - Finalizar atendimento](#_10wa3c10kh44)



# Legenda
1. Em negrito → Título de função, campo de contato, parâmetro ou valor salvo.
1. Em itálico → Função, ferramenta ou parâmetro da plataforma.
1. Sublinhado → Nome de fluxo.
1. Negrito e itálico → Valor de um campo.

# 1 - Regras de negócio
Este é um template de chatbot inteligente para assistência financeira. Para isto, o único ERP utilizado é o [Sienge](https://api.sienge.com.br/docs/). Para o fornecimento de informações financeiras, como segunda via e consulta de parcelas, utiliza-se como regra de negócio o intervalo de tempo entre o *mês atual, dois meses atrás e dois meses à frente*, totalizando cinco meses. O usuário final poderá acessar somente os dados que estejam nesse intervalo de tempo.

Para iniciar qualquer consulta ou solicitar segunda via, o usuário passa por um credenciamento através de seu CPF ou CNPJ e precisa ter um número de telefone atualizado na plataforma Sienge, visto que a verificação ocorre por meio da confirmação dos 4 últimos dígitos do número cadastrado. É importante ressaltar que nenhum código é enviado por SMS ou email, visando melhorar a experiência do usuário mantendo o canal.

Para o usuário ser direcionado ao atendimento humano, pede-se o nome completo, o número de contato e o email cadastrado, sendo o email a única informação obrigatória para o direcionamento ao atendente. Desta forma, deve-se atentar ao cadastro do usuário no Sienge para evitar frustrações.

# 2 - Evoluções
`	`Atualmente alguns cenários não são tratados neste template, sendo assim deixamos algumas ideias de evoluções futuras para melhorar a usabilidade:

1. Cenários em que o usuário desejar segunda via e digitar o mês por extenso. Exemplo: Quero a fatura do mês de dezembro e janeiro;
1. Cenários em que o usuário quiser somente a última fatura atrasada (fatura do mês passado) e a próxima fatura (fatura do próximo mês). O cenário da fatura atual (fatura desse mês) já está sendo tratado no fluxo. Atualmente, quando o usuário incorre na fatura atrasada ou futura, o mesmo recebe informações relacionadas ao mês atual e dois meses atrás para **atrasadas** e o mês atual e dois meses à frente para **futuras**. A única possibilidade de o usuário receber somente 1 boleto é se o mesmo utilizar a entidade “atual”;
1. A criação de uma intenção para o usuário que desejar saber qual o dia do seu vencimento.
1. Aplicar fluxos específicos para captura de leads.

# 3 - Globals
`	`Para este projeto, observe as globals e preencha corretamente. São elas:

- 3 globals do Sienge:

![](Documentação%20Fluxos%20Cristal.001.png)

- 2 globals para o Back4app e 1 global para a inteligência:

![](Documentação%20Fluxos%20Cristal.002.png)

- ` `3 globals do Rocketchat e 2 globals da Organização:

![](Documentação%20Fluxos%20Cristal.003.png)
# 4 - Triggers
`	`São utilizadas 3 Triggers neste projeto, são elas: **iniciarchat**, **uncaught message** para Rocketchat - Enviar mensagem e **uncaught message**. 

- **iniciarchat:** inicia o fluxo Boas vindas;
- **uncaught message (**grupo **Atendimento humano)**: Qualquer mensagem captada fora de algum fluxo é direcionada para o fluxo RocketChat - Enviar mensagem. Esta trigger serve para verificar se o usuário está falando com o bot ou sendo atendido no Rocketchat;
- **uncaught message:** Qualquer mensagem captada fora de algum fluxo e que o usuário não esteja em algum grupo, é direcionada para o fluxo Nova mensagem para ser tratada.


# 5 - Campos de contato
## 1 - Mensagem
Salva a mensagem enviada pelo usuário a fim de reutilizar em filtros e chamadas externas.
## 2 - Atividade
Atualizado de acordo com a ação/estágio no qual o contato* se encontra.
## 3 - Atividade no chat
Status do contato.

- Visitante: Conversando com o bot
- Atendimento humano: Conversando com um atendente.
## 4 - Código da sala
Salva o identificador de salas no Rocketchat.
## 5 - Departamento
Classificação de atendimento para o Rocketchat.
## 6 - Documento
Salva o CPF ou CNPJ do cliente.
## 7 - Finalidade
Classificação de atendimento para o Rocketchat.
## 8 - ID do cliente
Identificador do cadastro do cliente no SIENGE.
## 9 - Privacidade
Limpa os dados do contato e salva como anônimo.
## 10 - Telefone
Salva um número de telefone do cliente como padrão para consulta e validação.
## 11 - Título
Salva o identificador do título.
## 12 - Último login
Salva um timestamp da última vez que o cliente passou pelo fluxo de credenciamento.

# 6 - Fluxos e Fluidez
## 1 - Nova mensagem
A mensagem enviada no chat é salva no *campo de contato* **Mensagem** e verificado se trata-se de um novo contato* ou retorno de um já existente (Por agrupamento dinâmico usando o *campo de contato* **Atividade no chat**).

Se o usuário for visitante a mensagem é salva direcionada para tratamento no fluxo de Classificação. Caso o usuário não seja visitante será direcionado para o fluxo de Boas vindas para mensagem de apresentação da assistente.

## 2 - Boas vindas
Fluxo inicial de apresentação/boas vindas onde:

- o usuário é setado como Visitante (a mensagem de apresentação da assistente não repetirá se o usuário for visitante);
- Direcionado para o fluxo Menu principal.

## 3 - Cumprimentos e despedidas
`	`Fluxo em que chama-se a inteligência de Cumprimentos e saudações. Para evitar erros de intenção usa-se a confidência em 90%. O repositório de **Cumprimentos e Saudações** utilizado está disponível [neste link](https://bothub.it/dashboard/ilhasoft/farewellgreetings).

`	`Se o usuário cumprimentar, será respondido de acordo com o horário do dia (bom dia, boa tarde ou boa noite). Se o usuário se despedir será direcionado ao encerramento do chat.

## 4 - Menu principal
`	`Fluxo que diz opções de solicitações ao usuário. As opções podem ser alteradas de acordo com as solicitações do cliente. A divisão por *campo de contato* **Channel** possibilita o envio das opções em canais que não possuam *quick-reply* (whatsapp e sms).

## 5 - Algo mais
Este fluxo é chamado ao final do fluxo de Classificação para verificar se o usuário tem mais alguma solicitação. 

- Primeiro verifica-se a **atividade** do usuário para evitar envio de mensagens caso o usuário final tenha demonstrado interesse em encerrar o chat. Dessa forma, se **atividade** for ***fim***, apagamos a **atividade** e qualquer outra mensagem vai para fluxo de nova mensagem.
- Se a **atividade** não for ***fim,*** é apresentado novamente as opções de solicitações ao usuário final.

## 6 - Inatividade
`	`Fluxo que encerra atendimento por inatividade no chat. Se o usuário final estiver conversando pela web, quando chegar neste passo:

- Será apagado os dados do **id do cliente** e **título**, forçando-o a refazer o login/credenciamento para outras solicitações;
- A **atividade** será atualizada como ***fim*** para evitar envio de mensagens posteriores caso o usuário final não tenha completado o fluxo.

## 7 - Encerramento
Este fluxo envia mensagem de finalização do atendimento por *divisão por chance aleatória* e seta a **atividade** como ***fim*** para evitar envio de outras mensagens ao usuário final que demonstrou interesse em encerrar o chat.

## 8 - Baixa convicção
`	`Este fluxo dá um feedback ao usuário se a mensagem estiver com baixa confidência ou for para a intenção “bias”. É enviado um email para o cliente com a mensagem não entendida para ser tratada e o usuário é direcionado ao fluxo Atendimento humano.

## 9 - Classificação
Este é o fluxo estrutural que organiza os outros fluxos que tratam a entrada do usuário, como Cumprimentos e despedidas, Menu principal, Intenções, etc. 

Neste fluxo salva-se a intenção, entidades e confidencia da mensagem do usuário com base na chamada da inteligência no fluxo Classificador. O Repositório da inteligência da Cristal está disponível [neste link](https://bothub.it/dashboard/Mardone/surpresa-v4).

`	`O fluxo também direciona a mensagem para o fluxo de Intenções (fluxo que classifica por intenção) ou baixa confidência e verifica a **atividade** do usuário no chat. Se a **atividade** for ***fim*** o fluxo encerra, se não, o usuário é direcionado para o fluxo Algo mais.

## 10 - Classificador
Este é o fluxo que faz a chamada externa à inteligência da Cristal:

- POST em <https://nlp.bothub.it/v2/parse> 
- HTTP Headers: Authorization - @globals.bothub\_susana\_auth / Content-Type - application/json
- Post corpo: @(json(object("language", "pt\_br", "text", fields.mensagem)))
- O resultado da chamada é salvo como **Classificador**.
## 11 - Intenções
`	`Este fluxo direciona a entrada do usuário para cada intenção, são elas: segunda\_via; consultar; extrato; atendimento; lead; negociar; corretoria; saldo\_devedor; contratacao; antecipar; assistencia; encerrar; negativo, afirmativo e bias.

- As intenções de “segunda\_via” e “consultar” são direcionadas para o fluxo de Status Financeiro para tratamento pela API do Sienge.
- A intenção “extrato” é direcionada para o fluxo de Extrato por email.
- A intenção de “atendimento” e “lead” são direcionadas para o fluxo Atendimento humano.
- As intenções “negociar, corretoria, saldo\_devedor, contratacao, antecipar e assistencia” são direcionadas para o fluxo Funções não suportadas, essas funções são liberadas a partir da contratação do cliente.
- As intenções “encerrar e negativo” são direcionadas para o fluxo Encerramento.
- A intenção “bias” é direcionada para o fluxo Baixa convicção.

## 12 - Funções não suportadas
`	`Este fluxo divide e direciona as intenções não contratadas pelo Cliente (organização) à uma resposta mais amigável ao usuário. Como essas funções não estão disponíveis, o usuário é direcionado para o Atendimento humano, salvando a **finalidade** (nome da intenção) e o **departamento** como **financeiro**.

## 13 - Extrato por email
`	`Este fluxo verifica se o usuário já está credenciado, se não estiver credenciado será enviado para o fluxo Credenciamento. Também é verificado se o usuário tem email cadastrado antes de chamar a API do sienge, sendo:

- POST em customer-financial-statements
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- Post corpo: {"customerId":@fields.id\_do\_cliente,

"email": "@(replace(urns.mailto,"mailto:",""))"}

- O resultado da chamada é salvo como **EnviaExtrato**

`	`Verifica-se também se a chamada deu “Sucesso” e avisa ao usuário que o extrato foi enviado ao email. Se a chamada não for sucedida, pede-se ao usuário entrar em contato com o setor financeiro.

## 14 - Lead
Este fluxo dá uma resposta mais amigável ao usuário que entra na intenção “Lead” e redireciona para o fluxo Atendimento humano, salvando o *departamento* como **Vendas** e **finalidade** como **Lead**.

## 15 - Atendimento humano
`	`Este fluxo filtra as intenções para direcionar ao Atendimento humano desta forma:

- Se a intenção for “lead”, o usuário entra no fluxo “Lead” para dar a resposta mais amigável antes de continuar o fluxo.
- Se a intenção for outra, o usuário segue o fluxo.

Para evitar envio desnecessário e sobrecarga ao Rocketchat, pergunta-se se o usuário quer ser transferido para um atendente. Se a resposta for afirmativa, o usuário entra no fluxo Obter dados. É feita consulta de **atividade** (***fim***) para finalizar o fluxo se o usuário tiver desistido do atendimento no decorrer do fluxo de Obter dados e também verificamos se existe **departamento**. Se tiver **departamento**, o usuário é direcionado para o fluxo RocketChat - Criar sala, se não tiver **departamento**, salva-se o **departamento** como **Outros assuntos** e apaga-se a **finalidade** antes de direcionar para o fluxo RocketChat - Criar sala.

Caso o usuário não queira ser direcionado para um atendente, será direcionado ao fluxo Encerramento e se não houver resposta do usuário em 15 minutos será direcionado ao fluxo Inatividade.

## 16 - Obter dados
`	`Este fluxo estrutura os outros fluxos de obter dados (nome, telefone e email). É necessário verificar se o usuário não quis informar seus dados (anônimo) e se já tem os dados cadastrados para prosseguir com os fluxos. Além disso, verificamos se a **atividade** é ***fim*** (possibilidade de desistência do atendimento) para evitar *loopings* ou continuidade do fluxo.

## 17 - Obter dados - Nome
É o fluxo que capta o nome completo do usuário. Na *categoria* “Other” o nome que o usuário digitou é salvo e consulta-se a inteligência da Cristal para saber se o usuário digitou um nome ou quis desistir do chat ou não quis responder o nome, visto que a inteligência atual possui as intenções “encerrar e negativo”. Desta forma, chama-se o fluxo Classificador, verifica se a intenção for encerrar com 90% de confidência. Se sim, encerra o chat, se não, salva o nome do usuário no *campo de contato*.

## 18 - Obter dados - Telefone
É o fluxo que capta o telefone de contato do usuário utilizando o regex. Há também consulta à inteligência no fluxo Classificador para possibilitar a desistência do usuário com a mesma lógica do fluxo de Obter dados - Nome. É importante frisar que o usuário pode escolher não informar o telefone. A única informação imprescindível é o email.

## 19 - Obter dados - eMail
É o fluxo que capta o email do usuário. É requisito obrigatório para o credenciamento ou direcionamento para atendimento humano. Utiliza-se a mesma lógica para desistência no fluxo: chama-se o fluxo Classificador, verifica se a intenção for encerrar com 90% de confidência. Se sim, encerra o chat, se não, informa que este email não é um email válido.

Nos cenários de Obter nome, telefone e email não se encerra o chat se a intenção for “negativo”, visto que o nome dos usuários frequentemente têm confidência alta para esta intenção e isso poderia causar frustrações ao usuário, que nunca iria conseguir ser direcionado para o atendimento humano, visto que seu nome ou email podem ir sempre para a intenção “negativo”.

## 20 - Credenciamento
`	`É o fluxo que capta os dados de cadastro Sienge do usuário por meio do CPF ou CNPJ, chamando webhook desta forma:

- GET em: customers
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- O resultado da chamada é salvo como **cliente.**

`	`Após chamar a api do sienge, verifica-se a existência de telefone no cadastro, salvando o resultado para utilizá-lo na verificação de acesso por meio dos 4 últimos dígitos:![](Documentação%20Fluxos%20Cristal.004.png)

Se o usuário não responder com o CPF ou CNPJ ou quando o usuário não informar os 4 últimos dígitos corretamente seguirá a mesma lógica para desistência do atendimento: chama-se o fluxo Classificador, verifica se a intenção for encerrar com 90% de confidência. Se sim, encerra o chat, se não, informa que os dados são inválidos.

`	`Após a validação pelos últimos 4 dígitos do número de telefone do cadastro, todas as informações do usuário serão salvas em *campos de contato*, são elas: **Nome**, **documento** (CPF ou CNPJ), **Endereço de email**, **Telefone**, **ID do cliente** e **Último login**.

## 21 - Status Financeiro
É o principal fluxo que chama a API do sienge e capta os dados brutos do usuário para consultar parcelas, enviar segunda via, linha digitável e link do boleto. É o fluxo estrutural que funciona para as intenções “consultar” e “segunda\_via”.

Este fluxo verifica se o usuário já está credenciado no chat para, usando o **ID do cliente** (que foi salvo no fluxo de credenciamento) chamar a API do Sienge desta forma:

- GET em: https://api.sienge.com.br/@globals.sienge\_baseurl/public/api/v1/customer-financial-statements?customerId=@fields.id\_do\_cliente
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- O resultado da chamada é salvo como **statusfinanceiro.**



`	`Após a sucedida chamada ao Sienge, verifica-se o centro de custo no fluxo Verifica centro de custos, salvando-se o **Total de títulos** e o **Indice**. É importante ressaltar o uso da Global **@globals.centro\_de\_custos**, que deve ser alterada de acordo com a contratação do Cliente (organização).

`	`Se a verificação dos centros de custos der “sucesso”, salva-se o "Índice" como resultado do fluxo e se for “Nulo”, informa-se ao usuário que não foi possível ter acesso aos dados cadastrais. Se o índice não for “nulo” o fluxo segue.

`	`Após esta verificação, verificamos se a mensagem inicial do usuário já possui alguma data de parcela ou alguma das entidades “atrasada, próxima ou atual”. Se a mensagem já possuir uma data, formatamos adicionando dia como 01 e salvamos como "Mês consultado” e “Ano consultado”, sendo estes diferentes da data de vencimento da parcela.

`	`Se a mensagem do usuário não possuir entidades, essas serão as opções de resposta:

![](Documentação%20Fluxos%20Cristal.005.png)

`	`A categoria “Other” salva a mensagem e chama o fluxo Classificação para tratar a mensagem com a Inteligência da Cristal.

Se a mensagem inicial do usuário já possuir algumas das entidades “atrasada, próxima ou atual”, entra no fluxo Verifica data do intervalo para fazer a contagem do intervalo das parcelas que serão enviadas ao usuário. A regra de negócio aplicada a isso foi a seguinte: 

- Considera-se a data da consulta e o intervalo de até três meses para parcelas atrasadas ou futuras, neste caso conta-se o mês atual (mês em que foi feita a consulta), 2 meses atrás e 2 meses à frente.
- A consulta superior a 3 meses será direcionada para o fluxo Atendimento humano.

`	`Após completar o fluxo Verifica data do intervalo salva-se o mês e ano consultado com o nome **Mês consultado** e **Ano consultado**. Após isso, inicia-se o *contador* para evitar o *looping* na contagem de parcelas que vão ser enviadas ao usuário. Para isso salva-se a “data da parcela” que retorna do Sienge, o mês atual e o ano atual como parâmetro para comparar a ***data da parcela*** com a data consultada, usando as expressões **@(results.ano\_consultado = results.ano)** e **@(results.mes\_consultado = results.mes)** nas *divisões por expressão*.![](Documentação%20Fluxos%20Cristal.006.png)

`	`Quando a data consultada ou as entidades captadas passarem pela verificação de data e pelo *contador*, será dada uma resposta ao usuário sobre sua situação financeira pelo fluxo Resposta - Parcela Sienge. Esses são os casos de usuários que têm poucas parcelas e a chamada do sienge é bem sucedida (não precisa do back4app para paginação do retorno).

`	`Após a resposta do status financeiro dada pelo fluxo Resposta - Parcela Sienge, verifica-se por meio do card “Dividir por expressão” a *categoria* de “intervalopesquisa” (que filtra a entidade na mensagem do usuário) para enviar ou não a segunda via por email, a linha digitável e link do boleto. No caso de parcelas futuras, nada é enviado ao usuário, visto que não há nada em atraso. No caso de parcelas recentes e atrasadas, somente as parcelas atrasadas serão enviadas ao usuário.

`	`Antes do usuário entrar no fluxo Segunda via por email é verificado se as parcelas estão em aberto. Depois de completar o fluxo de Segunda via por email o usuário é direcionado para o fluxo Linha digitavel + link.

`	`Após isso, verifica-se o “índice” se é sienge ou back4app. Se for sienge, pergunta-se se o usuário deseja consultar outra parcela. É importante ressaltar que o usuário retorna ao *Aguarde por resposta* e se a resposta for afirmativa, utiliza-se a **mesma chamada anterior ao sienge**, evitando chamadas desnecessárias. Se for back4app (other), o usuário é direcionado ao fluxo Status Financeiro - Back4app, fluxo esse que chama o intermediário Back4app para consultar com retornos em json que ultrapassam o limite de 640 caracteres e salva-se o resultado do fluxo como “on”.

`	`Após completar o fluxo Status Financeiro - Back4app, verifica-se a **atividade** do usuário, caso o mesmo tenha desistido do atendimento no fluxo Status Financeiro - Back4app. Neste caso, se for ***fim***, encerra-se o fluxo. Se não, é chamado o webhook do Back4app para credenciamento do usuário:

- POST em: https://parseapi.back4app.com/functions/installments?customerId=@fields.id\_do\_cliente&billReceivableId=@fields.titulo&domain=@globals.sienge\_baseurl&token=@globals.sienge\_token\_back4app&afterDate=@child.results.afterdate&beforeDate=@child.results.beforedate
- HTTP Headers: Content-Type - application/json; X-Parse-Application-Id - @globals.appid ; X-Parse-REST-API-Key - @globals.appkey ;
- O resultado da chamada também é salvo como **statusfinanceiro** (lembrando que já se trata do caso back4app).

`	`Se a chamada ao back4app for sucedida, o usuário entra no fluxo Resposta - Parcela Back4app. Após completar esse fluxo, salva-se os resultados ‘intervalopesquisa” e “count” (quantidade de parcelas). Após isso, segue-se o mesmo fluxo das parcelas que chamam o Sienge: o usuário é direcionado ao fluxo de Segunda via por email e depois para o fluxo Linha digitavel + link (lembrando que Segunda via por email e  Linha digitavel + link possuem os dois cenários centralizados no fluxo: Sienge e Back4app).

## 22 - Verifica centro de custos
`	`Este fluxo é chamado pelo fluxo Status Financeiro para verificar os centros de custo do usuário. Neste fluxo verifica-se a existência de algum título. Se o **total de títulos** for 0, o índice é salvo como **nulo**. Se for algum número maior que 0, salva-se o **Total de títulos** e o “Indice”. É importante ressaltar o uso da Global “@globals.centro\_de\_custos”, que deve ser alterada de acordo com a contratação do Cliente (organização).

`	`Para encontrar o centro de custo usa-se a expressão:

@(parent.results.statusfinanceiro.extra.results[results.total\_de\_titulos -1].billsReceivable.0.costCenterId)

Encontrado o centro de custo de acordo com a global, salva-se o **Indice** e o **Total de títulos**.

## 23 - Verifica data do intervalo
`	`Este é o fluxo que obedece a regra de negócio do intervalo de consulta às parcelas (este é o intervalo que o usuário consultou), sendo este:

- Considera-se a **data da consulta** e o **intervalo de até três meses** para parcelas atrasadas ou futuras, neste caso conta-se o mês atual (mês em que foi feita a consulta), 2 meses atrás e 2 meses à frente.
- A consulta superior a 3 meses será direcionada para o fluxo Atendimento humano.
- ### Lógica para parcelas futuras:
Devido ao formato da contagem de meses no push ser diferente do resultado da chamada externa do Sienge e Back4app, para o cenário do mês de outubro salva-se o mês atual + 2 meses como “Mes consultado” e o ano atual.

Para tratar os casos de virada de ano captamos 13 como sendo mês Janeiro usando a expressão “@(if( (format\_date(today(), "MM") +2)=13, 1,(format\_date(today(), "MM")+2) ))” e 14 como mês Fevereiro usando a expressão “@(if( (format\_date(today(), "MM") +2)=14, 2, (format\_date(today(), "MM")+2) ))”.

Desta forma, se o usuário consultar parcelas futuras em novembro ou dezembro, haverá tratamento para formatar o mês e o ano: se o mês for Janeiro (01) ou Fevereiro (02) será salvo a categoria do “Mes consultado” e o ano atual + 1 (próximo ano).

Para qualquer outro caso salva-se o mês atual + 2, adicionando o 0 à esquerda do mês, visto que o formato da contagem de meses no push é diferente do resultado da chamada externa e salva-se e o ano atual.![](Documentação%20Fluxos%20Cristal.007.png)
- ### Lógica para parcelas atrasadas:
Para tratar os casos de virada de ano captamos 0 como sendo mês Dezembro usando a expressão “@(if( (format\_date(today(), "MM") -2)=0,12, (format\_date(today(), "MM")-2) ))” e -1 como mês Novembro usando a expressão “@(if( (format\_date(today(), "MM") -2)=-1, 11, (format\_date(today(), "MM")-2) ))”.

Para qualquer outro caso, salva-se o mês atual - 2 meses como "Mês consultado” e o ano atual como “Ano consultado”.
- ### Lógica para outras parcelas:
Quando o usuário não especificar se é parcela futura ou atrasada, segue-se a lógica de salvar o mês atual como "Mês consultado” e o ano atual como “Ano consultado”.
## 24 - Resposta - Parcela Sienge
Esse fluxo é chamado no fluxo de Status Financeiro para dar resposta ao usuário sobre sua situação financeira. Como uma forma de evitar erros e frustrações, a mensagem enviada ao usuário só possui o mês e ano de vencimento, impossibilitando enviar dia e valores pelo chat.

O fluxo inicia com um *contador* para evitar *looping* na contagem de parcelas a serem enviadas ao usuário. Após isso, divide-se o tratamento por *categoria* do “intervalopesquisa” do fluxo anterior (Status Financeiro).

- ### Para a categoria das parcelas recentes:
`	`Salva-se “count’ como 4 - É a quantidade de parcelas que serão contadas, iniciando contagem pelo 0. É importante lembrar que as parcelas recentes são todas as parcelas no intervalo de 2 meses atrás, mês atual e 2 meses à frente, totalizando 5 parcelas.

`	`Salva-se também o *contador* do fluxo anterior (Status Financeiro) com nome **indice** usando a expressão **@(parent.results.contador -2)**. Após isso chama-se o fluxo Intervalo por extenso para converter a data em mês e ano por extenso e dar a resposta ao usuário usando a expressão **@child.results.mes.category** e  **@child.results.ano**.

`	`Seguindo a lógica do *contador*, se a contagem for igual ao número **count**, o fluxo dá a resposta ao usuário e encerra por ter atingido a quantidade de parcelas. Se não, é somado 1 no **@results.indice** e no **@results.contador** do fluxo atual.

- ### Para a categoria das parcelas atrasadas:
Salva-se **count** como 2 - É a quantidade de parcelas que serão contadas, iniciando *contador* pelo 0. É importante lembrar que as parcelas recentes são todas as parcelas no intervalo do mês atual e 2 meses atrás, totalizando 3 parcelas.

Salva-se também o *contador* do fluxo anterior (Status Financeiro) com nome **indice** usando a expressão **@(parent.results.contador)**. Após isso chama-se o fluxo Intervalo por extenso para converter a data em mês e ano por extenso e dar a resposta ao usuário usando a expressão **@child.results.mes.category** e  **@child.results.ano**.

`	`Seguindo a lógica do *contador*, se a contagem for igual ao número **count**, o fluxo dá a resposta ao usuário e encerra por ter atingido a quantidade de parcelas. Se não, é somado 1 no **@results.indice** e no **@results.contador** do fluxo atual.

- ### Para a categoria das parcelas futuras:
Salva-se **count** como 2 - É a quantidade de parcelas que serão contadas, iniciando contagem pelo 0. É importante lembrar que as parcelas recentes são todas as parcelas no intervalo do mês atual e 2 meses à frente, totalizando 3 parcelas.

Salva-se também o *contador* do fluxo anterior (Status Financeiro) com nome **indice** usando a expressão **@(parent.results.contador)**. Após isso chama-se o fluxo Intervalo por extenso para converter a data em mês e ano por extenso e dar a resposta ao usuário usando a expressão **@child.results.mes.category** e **@child.results.ano**.

`	`Seguindo a lógica do *contador*, se a contagem for igual ao número **count**, o fluxo dá a resposta ao usuário e encerra por ter atingido a quantidade de parcelas. Se não, subtrai 1 no **@results.indice** e soma 1 no **@results.contador** do fluxo atual.

- ### Para a categoria da parcela atual:
Salva-se **count** como 0 - Este é o caso de o usuário pedir somente 1 parcela, sendo a parcela do mês atual, desta forma inicia-se a contagem pelo 0. 

Salva-se também o *contador* do fluxo anterior (Status Financeiro) com nome **indice** usando a expressão **@(parent.results.contador)**. Após isso chama-se o fluxo Intervalo por extenso para converter a data em mês e ano por extenso e dar a resposta ao usuário usando a expressão **@child.results.mes.category** e  **@child.results.ano**.

`	`Seguindo a lógica do *contador*, se a contagem for igual ao número **count**, o fluxo dá a resposta ao usuário e encerra por ter atingido a quantidade de parcelas. Se não, subtrai 1 no **@results.indice** e soma 1 no **@results.contador** do fluxo atual.

## 25 - Intervalo por extenso
É o fluxo chamado no Status Financeiro e tem a função de converter o formato de data DD-MM-YYYY para o mês e ano por extenso, dando uma resposta mais amigável ao usuário final e evitando frustrações quanto ao dia de vencimento da parcela.

Para isso, usamos a expressão **@(format\_date(parent.results.statusfinanceiro, "MM"))** e formatamos os meses “01, 02, 03 e seguintes” em “Janeiro, Fevereiro, Março e seguintes”. Além disso, usamos a mesma expressão para categorizar o ano da mesma forma que os meses.

Desta forma, o ano não é formatado, somente é feito isso para a resposta do fluxo Resposta - Parcela sienge e Resposta - Parcela Back4app ser chamada como **@child.results.mes.category** e **@child.results.ano**, facilitando o entendimento visual nos fluxos.

## 26 - Status Financeiro - Back4app
É o fluxo que capta o intervalo da pesquisa de usuários que não se encaixam no **indice** Sienge (que fica no fluxo Status Financeiro). É importante ressaltar que as datas que retornam do Back4app vêm com formato diferente do retorno do sienge, sendo assim, salvamos as datas com expressões diferentes porém com o mesmo nome para facilitar entendimento e melhorar a fluidez na workspace.

Primeiramente verificamos se o usuário se encaixa no **indice** sienge no fluxo de Status Financeiro, tornando **on** para **rerun** e chamando o resultado de **rerun** no fluxo Status Financeiro - Back4app para saber se o usuário deseja consultar outra parcela ou se ainda não consultou parcelas.

Se for **on**, aguardamos a resposta do usuário sobre a parcela que deseja. Senão, chama-se a API do sienge para verificar quantos títulos existem, desta forma:

- GET em: https://api.sienge.com.br/@globals.sienge\_baseurl/public/api/v1/accounts-receivable/receivable-bills?customerId=@fields.id\_do\_cliente
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- O resultado da chamada é salvo como **buscatitulo**.

`	`Após a chamada, verificamos se existe mais de 1 título. Se sim, informamos ao usuário quantos títulos existem e os salvamos em um *campo de contato*. Se só houver 1 título, também salvamos em *campo de contato*. Após salvar, verificamos se a mensagem do usuário já possui alguma data de parcela ou alguma das entidades “atrasada, próxima ou atual”. 

Se a mensagem inicial do usuário já possuir uma data ou entidade “atual”, salvamos **afterDate** adicionando dia como 01, o mês e o ano usando esta expressão “@(date\_from\_parts(format\_date( today(), "YYYY" ), format\_date( today(), "MM" ), "01" ))” e o **beforeDate** adicionando dia como 31, o mês e o ano usando esta expressão “@(date\_from\_parts(format\_date( today(), "YYYY" ), format\_date( today(), "MM" ), "31" ))”. Esse é o intervalo de pesquisa para cenários back4app.

Se a mensagem inicial do usuário já possuir as entidades “recente, atrasada e proxima”, o **afterDate** será o mês atual até 2 meses atrás + o ano atual e o **beforeDate** será o mês atual e 2 meses à frente + o ano atual. Desta forma, usa-se as expressões:

**afterDate**: 

@(date\_from\_parts( format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), -2, "M"), "YYYY"), format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), -2, "M"), "MM"), 1))

**beforeDate**:

@(date\_from\_parts( format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), 2, "M"), "YYYY"), format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), 2, "M"), "MM"), 1))

Para os casos em que a mensagem inicial do usuário não possuir entidade, porém o usuário responder a mensagem de “exemplos de data para informar” com *quick-reply* ou palavras-chave, as parcelas futuras e atrasadas serão salvas de outra forma por conta do formato que a informação chega nessa etapa.

Neste caso, para parcelas ‘futuras’ salva-se o mês e ano atual como **afterDate** e 2 meses à frente e o ano atual como **beforeDate.** Desta forma, usa-se as expressões:

**afterDate**: 

@(date\_from\_parts( format\_date((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), "YYYY"), format\_date((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), "MM"), 1))

**beforeDate**:

@(date\_from\_parts( format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), 2, "M"), "YYYY"), format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), 2, "M"), "MM"), 1))

Neste caso, para parcelas ‘atrasadas’ salva-se o 2 meses para trás e ano atual como **afterDate** e o mês e ano atual como **beforeDate.** Desta forma, usa-se as expressões:

**afterDate**: 

@(date\_from\_parts( format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), -2, "M"), "YYYY"), format\_date(datetime\_add((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), -2, "M"), "MM"), 1))

**beforeDate**:

@(date\_from\_parts( format\_date((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), "YYYY"), format\_date((date\_from\_parts(format\_date(now(), "YYYY"), format\_date(now(), "M"), 1)), "MM"), 1))

A categoria “Other” salva-se a mensagem, chama-se o fluxo Classificação e trata a mensagem do usuário, possibilitando a desistência do usuário.

`	`Após finalizar o fluxo Status Financeiro - Back4app voltamos para o fluxo Status Financeiro para fazer a chamada ao Back4app, informando a data filtrada no fluxo: Status Financeiro - Back4app. Antes disso, verificamos se o usuário desistiu do atendimento fazendo um split por **Atividade**.

`	`A chamada ao Back4app (que ocorre após o fluxo Status Financeiro - Back4app completar, salvando o **afterDate** e **beforeDate** como intervalo de pesquisa) é feita com esses parâmetros na URL:

- POST em https://parseapi.back4app.com/functions/installments?customerId=@fields.id\_do\_cliente&billReceivableId=@fields.titulo&domain=@globals.sienge\_baseurl&token=@globals.sienge\_token\_back4app&afterDate=@child.results.afterdate&beforeDate=@child.results.beforedate
- HTTP Headers: Content-Type - application/json / X-Parse-Application-Id - @globals.appid / X-Parse-REST-API-Key - @globals.appkey
- O resultado da chamada é salvo como **statusfinanceiro**.

`	`Após sucesso na chamada ao Back4app, essas etapas são seguidas:

- Inicia-se o fluxo Resposta - Parcela Back4app (fluxo que imprime a situação financeira para os cenários Back4app);
- Salva-se o **intervalopesquisa** com a expressão **@child.results.intervalopesquisa.category;**
- E salva-se o **count** (número de parcelas encontradas e a serem enviadas ao usuário no fluxo de Resposta - Parcela Back4app) com a expressão **@child.results.count.**



`	`Essas são as informações necessárias para iniciar o fluxo de Segunda via por email e Linha digitavel + Link, que a partir desta etapa, segue o mesmo percurso que as parcelas do cenário sienge.

## 27 - Resposta - Parcela Back4app
`	`Este é o fluxo que envia ao usuário a mensagem sobre sua situação financeira no cenário back4app. Para isto, seguimos a mesma lógica do fluxo Resposta - Parcela sienge: inicia com um contador para interromper *looping* na contagem de parcelas a serem enviadas ao usuário.

`	`Após isso, verificamos os cenários de quantidades de parcelas: Uma parcela, Duas parcelas, Três parcelas, Quatro parcelas e Cinco parcelas.

Para uma parcela salva-se **count** como 0, para duas parcelas salva-se **count** como 1 e assim por diante. É a quantidade de parcelas que serão contadas, iniciando contagem pelo 0. 

É importante lembrar que as parcelas recentes são todas as parcelas no intervalo de 2 meses atrás, mês atual e 2 meses à frente, totalizando 5 parcelas. O cenário de parcelas atrasadas e futuras em regra são 3 parcelas (para trás ou para frente). O cenário de uma parcela, duas parcelas ou quatro parcelas são para os casos de primeiras parcelas do contrato em que ainda não existem 3 parcelas ou 5 parcelas.

Após verificar a quantidade de parcelas, chama-se o fluxo Intervalo por extenso para converter a data em mês e ano por extenso e dar a resposta ao usuário usando a expressão **@child.results.mes.category** e **@child.results.ano**.

`	`Seguindo a lógica do contador, se a contagem for igual ao número **count**, o fluxo dá a resposta ao usuário e encerra por ter atingido a quantidade de parcelas. Se não, continua somando 1 no **@results.contador**.

## 28 - Segunda via por email
`	`Este é o fluxo que chama a API do Sienge que envia por email as parcelas nos dois cenários: Back4app e Sienge. Para isto, o fluxo inicia salvando o resultado do contador do fluxo anterior com a expressão **@parent.results.contador** e salvando **count** (número de parcelas a serem enviadas ao usuário) como 0.

`	`A principal característica deste fluxo é que a chamada ao sienge é a mesma para todos os casos. O que diferencia os cenários são os contadores para cada situação. Esta é a chamada ao webhook:

- POST em: https://api.sienge.com.br/@globals.sienge\_baseurl/public/api/v1/payment-slip-notification/
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- POST corpo: {"receivableBillId": @fields.titulo,

"installmentId": @parent.results.statusfinanceiro.extra.result.0.installmentId,

"emailCustomer": "@(replace(urns.mailto,"mailto:",""))",

"emailTitle": "Boleto teste.",

"emailBody": "Esse é um boleto de teste."}

- O resultado da chamada é salvo como **enviaporemail**.

`	`Para definir o cenário back4app ou sienge, usamos a expressão **@parent.results.intervalopesquisa**, que busca o resultado de **intervalpesquisa** no fluxo anterior. Como salvamos os cenários sienge e back4pp no fluxo anterior com o mesmo nome (intervalopesquisa), o que diferencia os dois são as *regras* (para back4app) e a *categoria* (para sienge) da *Divisão por expressão* do fluxo anterior. Desta forma, se chamarmos a expressão **@parent.results.intervalopesquisa** e retornar “uma, duas, três, quatro e cinco”, este é o cenário das parcelas Back4app, se for “Other” o cenário é sienge.
- ### Para cenários Back4app:
- Se o usuário incorrer no cenário de “uma” parcela, chama-se a api do sienge que envia boleto por email e encerra o fluxo.
- Se o usuário incorrer no cenário de “duas três quatro cinco” parcelas, verificamos quais estão em aberto e inicia-se o contador para enviar as parcelas.

- ### Para cenários Sienge:
- Se o usuário incorrer no cenário de parcelas “Recentes e Atrasadas”, verificamos quais estão em aberto e inicia-se o contador para enviar as parcelas. A diferença é que se for “Atrasadas” o contador soma 1 e se for qualquer outra, diminui-se 1. Segue imagem do fluxo:


![](Documentação%20Fluxos%20Cristal.008.png)
## 29 - Linha digitavel + link
Este é o fluxo que chama a API do Sienge que gera o link dos boletos e a linha digitável das parcelas nos dois cenários: Back4app e Sienge. Para isto, o fluxo inicia salvando o resultado do contador do fluxo anterior com a expressão **@parent.results.contador** e salvando ***count*** (número de parcelas a serem enviadas ao usuário) como 0.

Para definir o cenário back4app ou sienge, usamos a expressão **@parent.results.intervalopesquisa**, que busca o resultado de **intervalpesquisa** no fluxo anterior. Como salvamos os cenários sienge e back4pp no fluxo anterior com o mesmo nome (intervalopesquisa), o que diferencia os dois são as *regras* (para back4app) e a *categoria* (para sienge) da *Divisão por expressão* do fluxo anterior. Desta forma, se chamarmos a expressão **@parent.results.intervalopesquisa** e retornar “uma, duas, três, quatro e cinco”, este é o cenário das parcelas Back4app, se for “Other” o cenário é sienge.

Devido ao retorno do Back4app ter formato diferente do retorno do sienge (retorno de dados brutos), o **InstallmentId** é salvo diferente para cada cenário: back4app e sienge.

Uma característica deste fluxo é que a chamada ao webhook é diferente para o cenário back4app e sienge e os cenários possuem contadores para cada situação. 

- ### Para cenários Back4app:
Esta é a chamada ao webhook para cenários Back4app:

- GET em: https://api.sienge.com.br/@globals.sienge\_baseurl/public/api/v1/payment-slip-notification/?billReceivableId=@fields.titulo&installmentId=@results.installmentId
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- O resultado da chamada é salvo como **linkelinha**.

1 - Salva-se o **installmentId** com a expressão:

**@(parent.results.statusfinanceiro.extra.result[results.count].installmentId)**;

2 - Se o usuário incorrer no cenário de “uma” parcela:

- Chama-se a api do sienge que gera o link do boleto e a linha digitável;
- Inicia o fluxo Intervalo por extenso para converter a data DD-MM-YYYY para mês e ano por extenso;
- Envia ao usuário a parcela e encerra o fluxo.

3 - Se o usuário incorrer no cenário de “duas, três, quatro e cinco” parcelas:

- Verifica-se quais estão em aberto;
- Chama-se a api do sienge que gera o link do boleto e a linha digitável;
- Inicia o fluxo Intervalo por extenso para converter a data DD-MM-YYYY para mês e ano por extenso;
- Envia ao usuário a parcela;
- E inicia-se o contador (soma-se 1 em **count** e 1 em **installmentId**) para enviar as demais parcelas. O contador compara o **results.count** com o **parent.results.count** (número de parcelas do fluxo anterior). Dessa forma, se os dois ficarem iguais, o *contador* encerra.

- ### Para cenários Sienge:
Esta é a chamada ao webhook para cenários Sienge:

- GET em: https://api.sienge.com.br/@globals.sienge\_baseurl/public/api/v1/payment-slip-notification/?billReceivableId=@results.billReceivableId&installmentId=@results.installmentId
- HTTP Headers: Authorization - @globals.sienge\_token / Content-Type - application/json
- O resultado da chamada é salvo como **linkelinha**.

1 - Salva-se o **billReceivableId** com a expressão:

**@(parent.results.statusfinanceiro.extra.results[parent.results.indice].billsReceivable.0.billReceivableId)**;

2 - Salva-se o **installmentId** com a expressão:

**@(parent.results.statusfinanceiro.extra.results[parent.results.indice].billsReceivable.0.installments[results.contador].installmentId)**;

3 - Se o usuário incorrer no cenário de parcelas “Recentes e Atrasadas”:

- Verificamos quais estão em aberto;
- Chama-se a api do sienge que gera o link do boleto e a linha digitável;
- Inicia o fluxo Intervalo por extenso para converter a data DD-MM-YYYY para mês e ano por extenso;
- Envia ao usuário a parcela;
- E inicia-se o *contador* para enviar as parcelas. Se for “Atrasadas” o *contador* soma + 1 e se for qualquer outra, diminui-se 1, após isso salva-se o **installmentId**. Além disso, para encerrar o contador e o envio de parcelas, dividimos o *campo de contato* **count** para quando for 2 (três parcelas contando do 0), encerrar o fluxo.

## 30 - RocketChat - Criar sala
`	`É o fluxo que cria sala para atendimento humano chamando a api do rocketchat:

- GET em: https://@globals.rocketchat\_baseurl/core/room/?orgId=@globals.rocketchat\_org\_id&department=@(url\_encode(fields.departamento))&token=@contact.uuid&name=@(url\_encode(title(contact.name)))
- HTTP Headers: Authorization - @globals.rocketchat\_token / Content-Type - application/json
- O resultado da chamada é salvo como **sala.**

Salva-se o **Código da sala**, atualiza o *campo de contato* **Atividade no chat** para ***Atendimento humano*** para não haver conflitos de envios de mensagem ao usuário que estiver sendo atendido pelo rocketchat.

`	`Se a chamada ao webhook não for sucedida, informa-se que não há agente online no momento e pede ao usuário tentar novamente mais tarde.

## 31 - RocketChat - Enviar mensagem
`	`É o fluxo que salva a mídia ou mensagem para chamar a API do Rocketchat desta forma:

- POST em: https://@globals.rocketchat\_baseurl/core/message/
- HTTP Headers: Authorization - @globals.rocketchat\_token / Content-Type - application/json
- Post corpo: 

@(json(object(

`    `"org\_id", globals.rocketchat\_org\_id,

`    `"token", contact.uuid, 

`    `"room\_id", contact.fields.codigo\_da\_sala,

`    `"msg", results.mensagem.value

)))

- O resultado da chamada é salvo como **Result.**

## 32 - RocketChat - Mídias
`	`É o fluxo que envia imagem, áudio, link ou mensagem pela expressão **@trigger.params.extra**.

## 33 - RocketChat - Finalizar atendimento
`	`É o fluxo que finaliza o atendimento pelo rocketchat. Atualiza o *campo de contato* **Atividade no chat** para ***Visitante*** e apaga-se o **Código da sala**.
![](Documentação%20Fluxos%20Cristal.009.png)
