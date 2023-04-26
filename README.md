# A História e Arquitetura da Netflix

# História 

![Netflix_logo svg](https://user-images.githubusercontent.com/79367218/234593132-00f2b32e-b4b9-4ee2-83bc-855d64811528.png)

## Como surgiu a Netflix?
A Netflix surgiu em 29 de agosto de 1997, criada pelos empresários Marc Randolph e Reed Hastings, que no início a empresa realizava a locação de DVDs via correios com pedidos realizados na Netflix e em seu site Netflix.com, uma inovação para a época.
A ideia de alugar filmes via correios foi de grande ajuda para aqueles que não tinham uma locadora próxima de casa. Para garantir a entrega segura e de qualidade aos seus clientes quando efetuado o serviço de locação, os fundadores Marc e Reed testaram o serviço de entrega tradicional pelos correios enviando mídias ópticas para si mesmos, uma vez que as fitas VHS eram muito frágeis e os DVDs estavam ainda entrando no mercado.

![1997-1024x683](https://user-images.githubusercontent.com/79367218/234585050-8fb23f11-e6a1-43c2-97d7-92afd7a6aafe.png)

Como não havia conhecimento se alguém havia feito isso antes, era importante testar a logística e a segurança desta nova modalidade de aluguel de DVDs com entrega e devolução via correios e ela deu super certo. A empresa foi então registrada na cidade de Scotts Valley e teve um investimento inicial de U$1,9 milhões, doados por Reed Hastings, que logo se tornou o primeiro dono da Netflix, com 70% da companhia, ao lado de Marc Randolph, que ficou com o restante, tornando-se um proprietário minoritário.
No início, ainda em fase beta, o projeto Netflix era chamado Kibble, em referência a uma antiga propaganda que dizia “não importa o quão bom é o marketing da ração canina se o cachorro não comer”. Com tudo pronto e testada a parte online, os serviços finalmente se iniciaram e, em 14 de abril de 1998, foi lançado o site www.netflix.com, o primeiro portal destinado ao aluguel e vendas de DVDs online. E os primeiros logos da marca, exibidos em seu site com as palavras Net e Flix escritos separadamente, evidenciam seu principal significado: “Net” como uma abreviação de internet e “Flix” provindo de uma variação de Flick, palavra usada informalmente no idioma americano para se referir a filmes.

No final dos anos 90, mais precisamente em 1999, a Netflix evoluiu o seu sistema e criou um serviço de assinaturas do portal, que oferecia aos seus clientes a possibilidade de alugar DVDs em quantidades ilimitadas e sem data de devolução.O serviço de assinatura oferecia também um teste gratuito, o “free trial“, que era concedido ao convidar um amigo, através de um código, para a plataforma. E ao passar dos anos, teve mais evoluções até chegar os dias atuais.

<div align="center">
<img src="https://user-images.githubusercontent.com/79367218/234588555-52eeca6d-a8ce-4b68-8e76-7026bb34fcb7.jpg" />
</div>

# Sobre o Aplicativo

Atualmente, a Netflix oferece o streaming de vídeo, o que permite o acesso instantâneo a filmes, séries, documentários, shows e animações presentes no catálogo. O serviço está disponível em 190 países e em mais de 30 idiomas. Com isso, a somatória de assinantes pelo mundo é de cerca de 200 milhões, segundo a plataforma. 
O modelo atual de negócio teve início em 2007, e de acordo com a empresa, a missão da Netflix é permitir que o acesso a filmes e outros conteúdos seja simples. Sendo assim, basta fazer o cadastro no site e escolher um dos planos disponíveis, com pagamentos mensais, para ter acesso ilimitado aos títulos.
É possível assistir em qualquer aparelho conectado à internet compatível com o aplicativo Netflix, como Smart TVs, videogames, aparelhos de streaming, decodificadores, smartphones e tablets, também pode assistir no computador pelo navegador. 

Em 5 de setembro de 2011, a Netflix era lançada no Brasil, mesmo ano em que surgiram os primeiros controles remotos com um botão direto para o serviço, ao acessá-lo pela TV, e neste ano a empresa assinaria contrato de licença com diversas produtoras, entre as quais Paramount, Sony Pictures, BBC Worldwide, MGM e Disney, para citar algumas. A Netflix no Brasil em 2015 já faturava um valor mais alto que o gerado pela TV aberta.
Muitas produções nacionais entraram no catálogo da plataforma de streaming, além de títulos originais produzidos em solo brasileiro. Mesmo com uma oferta menor de títulos em relação aos EUA, o Brasil pode ser considerado um dos países com uma maior quantidade de produções disponíveis, chegando a ultrapassar muitos países europeus.

Desde 2013, além da transmissão de filmes e séries de terceiros, a Netflix oferece produções originais, como House of Cards, Orange is the New Black, Stranger Things, Narcos e 13 Reasons Why. O primeiro filme original da marca, Beasts of No Nation, foi lançado em 2015.

Ao longo do tempo, a companhia também investiu em ferramentas para melhorar a experiência do usuário. Em 2016, o recurso de download foi adicionado e permitiu o acesso offline. No ano seguinte, foi incluída a opção de pular a abertura dos títulos. Em 2018, o bloqueio por meio de um código PIN foi oferecido como um dos recursos de controle dos pais. Já em 2020, foi lançado o TOP 10, uma lista que exibe os conteúdos mais assistidos. De forma contínua, a empresa faz melhorias no app, a fim de se destacar como a melhor plataforma de streaming.  

![43e0db2f-fea0-4308-bfb9-09f2a88f6ee4_what_is_netflix_1_en](https://user-images.githubusercontent.com/79367218/234594650-8a9afc53-00ca-428d-a1e1-f218c906db4b.png)


# Demandas e Características 

# Arquitetura

O estilo arquitetônico da Netflix é construído como uma coleção de serviços. Isso é conhecido como arquitetura de microsserviços e capacita todas as APIs necessárias para aplicativos e aplicativos da web. Quando a solicitação chega ao endpoint, ela chama os outros microsserviços para obter os dados necessários e esses microsserviços também podem solicitar os dados para microsserviços diferentes. Depois disso, uma resposta completa para a solicitação da API é enviada de volta ao terminal. 
Em uma arquitetura de microsserviço, os serviços devem ser independentes uns dos outros, por exemplo, o serviço de armazenamento de vídeo seria desacoplado do serviço responsável pela transcodificação de vídeos.

![Microservice-Architecture-of-Netflix](https://user-images.githubusercontent.com/79367218/234607756-8a93c171-e67a-4e2b-922b-dfd583188787.jpg)

## Como tornar essa arquitetura confiável?

* Use Hystrix, uma biblioteca projetada para controlar as interações entre serviços distribuídos, adicionando tolerância de latência e lógica de tolerância a falhas. Hystrix faz isso isolando pontos de acesso entre os serviços, sistema remoto e bibliotecas de terceiros. 
* Separe microsserviços críticos: Podemos separar alguns serviços críticos (ou endpoint ou APIs) e torná-los menos dependentes ou independentes de outros serviços. Pode tornar alguns serviços críticos dependentes apenas de outros serviços confiáveis. Ao escolher os microsserviços críticos, pode incluir todas as funcionalidades básicas, como pesquisar um vídeo, navegar até os vídeos, clicar e reproduzir o vídeo etc. Dessa forma, podendo tornar os endpoints altamente disponíveis e até mesmo no pior dos cenários, pelo menos um usuário será capaz de fazer as coisas básicas.
* Trate os servidores como sem estado: A ideia é projetar o serviço de forma que, se um dos endpoints estiver apresentando o erro ou não atendendo à solicitação em tempo hábil, você possa alternar para outro servidor e realizar o seu trabalho. Em vez de depender de um servidor específico e preservar o estado nesse servidor, você pode rotear a solicitação para outra instância de serviço e pode ativar automaticamente um novo nó para substituí-lo. Se um servidor parar de funcionar, ele será substituído por outro.
