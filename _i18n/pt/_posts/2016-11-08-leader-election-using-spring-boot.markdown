---
layout: post
title: Eleição de Nó Lider em Spring Boot
date: '2016-11-08 03:53:00'
permalink: eleicao-de-no-lider-em-spring-boot
---

Spring boot tomou do mercado de assalto nos últimos anos. Só o Spring MVC [já havia crescido e virado a principal tecnologia de novos sistemas, como mostram os *trends* no StackOverflow](http://www.indeed.com/jobtrends/q-Spring-Framework-q--J2EE-q--Java-EE-q-Java.html?Relative=1), porém o Spring Boot aprofundou ainda mais essa dianteira. Com seus recursos de configuração automática e o [spring initizr](https://start.spring.io/), o setup dos projetos agora leva segundos.

Mas toda a simplicidade tem um preço: é difícil fazer algo simples e personalizado fora da estrutura padrão. Talvez dificil não seja a palavra, mas quando você se acostuma com uma configuração simples e fácil, toda complicação fica frustrante. Foi assim que começou minha pequena saga.

Eu estava testando alguns recursos para um novo projeto no trabalho e uma das muitas idéias era: dado um número de nós da aplicação, sem intervenção, definir um nó como líder para executar um trabalho em segundo plano. Simples assim. É chamado [Eleição de Liderança de Cluster](https://en.wikipedia.org/wiki/Leader_election) e é um problema comum em muitos ambientes em cluster ([Redis](http://redis.io/topics/sentinel) entre outras).

A filosofia do Spring é manter o servidor sem estado, então via de regra, não há necessidade de processo de eleição, pois os nós do seu aplicativo não são exatamente agrupados, da maneira que eles não estão cientes um do outro. É ótimo para crescimento horizontal, e acredito que é um dos "modos de vida do Spring" que o levou ao topo. Mas, no meu caso, tudo que eu queria era uma maneira simples de manter os nós conscientes, se eles são ou não o líder.

Pesquisando a documentação, encontrei pela primeira vez [Eleição da Liderança com Hazelcast em Spring Cloud Cluster](https://github.com/spring-cloud/spring-cloud-cluster/tree/master/spring-cloud-cluster-hazelcast) , mas ops, foi descontinuado em favor de [Spring-Integration](https://projects.spring.io/spring-integration/). Comecei a olhar para esse aqui, mas foi um imenso exagero para o meu caso de uso. Eu não precisava de interações complexas entre meus nós, nem precisava de grandes integrações entre muitos protocolos diferentes. Descartado.

A outra maneira que encontrei foi usar o [ZooKeeper](https://zookeeper.apache.org/). É um projeto incrível, que tem por padrão a [Eleição da Liderança](https://zookeeper.apache.org/doc/trunk/recipes.html#sc_leaderElection) que eu tanto precisava. Mas, novamente, configurar um cluster do ZooKeeper parecia um grande passo para executar algo simples. Eu não precisava da descoberta de serviços e de muitos outros recursos que ela traz para a mesa. Parecia um canhão para matar uma formiga. Fora da competição.

Além desses dois eu encontrei ... nada. Foi realmente difícil encontrar alguém com o mesmo problema e, quando descobri, eles geralmente criavam algo grande e complexo, com tabelas de banco de dados e outras coisas. Não era a ideia de rápido e simples que eu tinha em mente.

Então, [eu mesmo construí um](https://github.com/vitallan/redis-leader-by-lock).

Usando o *redis set* para criar um registro de lock, a idéia é: quem detém o lock é o líder. Isso é um pouco diferente de outra implementação em que o nó mais antigo é o líder até o desligamento, porque a liderança pode ir de nó em nó, dependendo do ping do lock e do tempo limite, mas resolveu o meu problema. É simples, com configuração fácil, confiável e expansível.

[Fique à vontade para usá-lo](https://github.com/vitallan/redis-leader-by-lock).

É bom testá-lo em, digamos, quatro terminais diferentes. Dessa forma, você pode matar e gerar o processo e verificar sua própria organização  definir o líder. Uma melhoria seria configurar aleatoriamente os atrasos fixos e verificar o comportamento. Farei este teste em um futuro próximo.

Por favor, oh, por favor, se você encontrar algum bug ou problema, [me avise](https://github.com/vitallan/redis-leader-by-lock/issues).