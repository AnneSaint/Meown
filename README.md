# Meown - Alimentador Automático de Pets


Projeto da 3ª avaliação da disciplina de Técnicas de Programação 2019.2

Aplicação do Meown com a framework Qt e o microcontrolador NodeMCU 12E ESP8266.

Feito por [Eduardo Freitas](https://github.com/EduFreit4s) e [Anne](https://github.com/AnneSaint)

## Sumário 
* [Sobre o Meown](https://github.com/AnneSaint/Meown/blob/master/README.md#o-que-%C3%A9-meown)
  * [Por que utilizar o Meown?](https://github.com/AnneSaint/Meown/blob/master/README.md#por-que-utilizar-o-meown)
* [Manual do Usuário](https://github.com/AnneSaint/Meown/blob/master/README.md#manual-do-usu%C3%A1rio)
  * [Como funciona o Meown](https://github.com/AnneSaint/Meown/blob/master/README.md#como-funciona-o-meown)
  * [Software do Meown](https://github.com/AnneSaint/Meown/blob/master/README.md#software-do-meown)
    * [Monitoramento da Presença Felina](https://github.com/AnneSaint/Meown/blob/master/README.md#monitoramento-da-presen%C3%A7a-felina)
    * [Monitoramento da Quantidade de Ração](https://github.com/AnneSaint/Meown/blob/master/README.md#monitoramento-da-quantidade-de-ra%C3%A7%C3%A3o)
    * [Período de Tempo Minimo para a Alimentação](https://github.com/AnneSaint/Meown/blob/master/README.md#per%C3%ADodo-de-tempo-minimo-para-a-alimenta%C3%A7%C3%A3o)
  * [Utilizando o site do Meown](https://github.com/AnneSaint/Meown/blob/master/README.md#utilizando-o-site-do-meown)
    * [Nível de Alimento](https://github.com/AnneSaint/Meown/blob/master/README.md#n%C3%ADvel-de-alimento)
    * [Tempo de Refeição](https://github.com/AnneSaint/Meown/blob/master/README.md#tempo-m%C3%A9dio-de-refei%C3%A7%C3%A3o)
    * [Número de Refeições](https://github.com/AnneSaint/Meown/blob/master/README.md#n%C3%BAmero-de-refei%C3%A7%C3%B5es)
* [Informações Técnicas](https://github.com/AnneSaint/Meown/blob/master/README.md#informa%C3%A7%C3%B5es-t%C3%A9cnicas)
  * [Materiais](https://github.com/AnneSaint/Meown/blob/master/README.md#materiais)
  * [Circuito](https://github.com/AnneSaint/Meown/blob/master/README.md#circuito)
  * [Página Web](https://github.com/AnneSaint/Meown/blob/master/README.md#p%C3%A1gina-web)


## Sobre Meown
Meown é um projeto criado por alunos do curso de Engenharia Elétrica do IFPB, Campus João Pessoa, com intuito de cronstruir uma máquina que administre automaticamente as doses e quantidade de ração por pet, como gatos ou cães, de acordo com critérios que promovam o bem estar animal e que mantenha os instintos naturais ativos no ambiente doméstico. 
### Por que utilizar o Meown?
A composição nutricional da maioria das rações para pets que circulam no comércio é do tipo seca e com uma presença excessiva de sais minerais nela. Ao longo prazo, a nutrição felina ou canina, entre outros, torna-se prejudicial, já que o consumo em excesso do alimentos ressecados acarreta, ao beber água, em um inchaço no estômago do animal pela absorção dos líquidos pela ração. Além disso, pode causar  doenças crônicas que possam ser desenvolvidas posteriomente, como diabetes, obesidade, depressão, entre outras.

Desarte, foi pensado um modo que possibilite um gerenciamento adequado das porções, as quais sejam planejadas de acordo com um intervalo de tempo já estabelecido, a presença felina e a quantidade de refeições, sendo todos esses requisitos ideais para manter o bem estar da saúde do bichano.
## Manual do Usuário
O intuito principal do projeto é que o Meown possa ter acesso a informações do tempo levado para consumir o alimento, a quantidade de ração presente no tanque interior e as vezes que o pet comeu a partir da presença do animal perto do hardware por um sensor ultrassônico. Para acompanhar essas informações, foi disponibilizado um [site](http://meown-engine.herokuapp.com/), no qual haverá acesso a esses respectivos dados para realizar o acompanhanmento direto e via web.
### Como funciona o Meown
O Meown é uma estrutura de madeira com uma tampa, para colocar a ração no tanque, que possui um sensor de presença ultrassônico do animal e, interiomente uma catraca para regular as porções de ração e uma rampa por qual a comida irá escorrer no pote de alimentação do pet.

Estas são as figuras que representam as medições do projeto em centímetros, cm:
![Figura 1. Base;](https://github.com/AnneSaint/Meown/blob/master/base.jpg)
Figura 1. Base e estrutura básica da catraca
![Figura 2. Rampa](https://github.com/AnneSaint/Meown/blob/master/rampas.jpg)
Figura 2. Rampa
![Figura 3. Paredes](https://github.com/AnneSaint/Meown/blob/master/paredes.jpg)
Figura 3. Paredes

Por dentro, o mecanismo de catraca será acionado, assim rotacionando o mecanismo em 90° e liberando pela rampa uma quantidade aproximada de 32 gramas de ração no pote. Desse modo, essa condição só será verdadeira caso o intervalo de tempo de horas, definidos anteriomente existir entre as refeições, já que esse é o período ideal para não haver complicações na saúde do animal.

![Figura 4. Catraca Interna](https://github.com/AnneSaint/Meown/blob/master/catraca%20.jpg)

### Software do Meown
O software do projeto foi montado na interface QT Creator como forma de mostrar na tela os dados coletados pelos sensores aplicados na estrutura do Meown.

![Figura 5. Interface "Home" do Meown](https://github.com/AnneSaint/Meown/blob/master/home_qt.png)

Figura 5. Interface "Home" do Meown
#### Monitoramento da Presença Felina
A presença do aminal por um sensor ultrassônico na extremidade da tampa medirá a existência de uma obstrução dos dados, uma oscilação incomum das informações coletadas, assim demonstrando e acionando como verdadeira a companhia do pet no pote de alimento.
#### Monitoramento da Quantidade de Ração
Outro sensor, do mesmo da presença felina, está localizado no outra extremidade da tampa medindo a quantidade de ração pela distância entre o topo da pilha de ração e a tampa.

![Figura 6. Interface "Conexão" do Meown](https://github.com/AnneSaint/Meown/blob/master/conexao_qt.png)

Figura 6. Interface "Conexão" do Meown
#### Período de Tempo Minimo para a Alimentação
Utilizando o primeiro sensor, será registrado o tempo que o pet fica no pote comendo pelo tempo que a oscilação os dados sairem do normal, assim coletando os minutos levados para a ração ser comida.

![Figura 7. Interface "Estatísticas" do Meown](https://github.com/AnneSaint/Meown/blob/master/estatisticas_qt.png)

Figura 7. Interface "Estatísticas" do Meown
### Utilizando o site do Meown
O [site](http://meown-engine.herokuapp.com) criado no heroukuapp.com utilizando html é uma ferramnta utilizada para o acompanhamento de dados registrados pelos sensores na estrutura física do Meown.

![Figura 8. Interface primária do site do Alimentador Inteligente para Pets](https://github.com/AnneSaint/Meown/blob/master/heroku_meonw_semconexoes.png)

Figura 8. Interface primária do site do Alimentador Inteligente para Pets
#### Nível de Alimento
O nível de alimento registrado de acordo com o sensor é registrado e colocado na tela se está cheio, pouca ração ou vazio..

![Figura 9. Interface mostrando o nível do alimento](https://github.com/AnneSaint/Meown/blob/master/heroku_meown_umaconexao.png)

Figura 9. Interface mostrando o nível do alimento
#### Tempo de Refeição
O tempo é medido pelas oscilações de dados registrados pelo sensor ultrassônico em minutos:

![Figura 10. Interface mostrando o tempo aproximado da refeição](https://github.com/AnneSaint/Meown/blob/master/heroku_meown_duasconexoes.png)

Figura 10. Interface mostrando o tempo aproximado da refeição
#### Número de Refeições
Por último, o site registra quantas vezes o animal se alimentou pelo número de aparições perto do pote em um intervalo de 24 horas:

![Figura 11. Interface mostrando todos os dados coletados](https://github.com/AnneSaint/Meown/blob/master/heroku_meown_todasconexoes.png)

Figura 11. Interface mostrando todos os dados coletados
## Informações Técnicas 
### Materiais
### Circuito
### Página Web
