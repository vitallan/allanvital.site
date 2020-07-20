---
layout: post
title: Sobre Estimativas em Software
date: '2017-07-22 22:13:44'
permalink: porque-estimativas-nunca-funcionam
tags:
- project-management
- estimates
---

Todo mundo sempre fala sobre [estimativas no desenvolvimento de software](https://www.quora.com/Why-are-software-development-task-estimations-regularly-off-by-a-factor-of-2-3). Esteja você em uma grande empresa, em uma pequena agência ou em um projeto "exército de um homem só", a idéia de que você pode prever quanto tempo levará para construir um sistema é replicada por todos.

Qualquer princípio de gerenciamento ou cronograma de projeto precisa disso como o mínimo necessário para operar. Isso é útil para que você possa planejar com antecedência e organizar os projetos em uma ordem que faça sentido, evitando buracos óbvios e erros de negócios. Em um ambiente de várias equipes, o prazo é usado para coordenar os resultados de uma maneira que uma equipe não bloqueie a outra, mapeando as dependências e ajustando o trabalho adequadamente.

O único problema é que, na maioria dos casos, as estimativas de software estão *erradas*. Normalmente, de maneira colossal.

[É provavelmente um dos problemas mais analisados ​​no setor](https://www.quora.com/Why-are-software-development-task-estimations-regularly-off-by-a-factor-of-2-3), e ainda assim, um dos mais não resolvidos.

### O elefante na sala

[As estimativas de projetos de software falham gravemente desde o início do software](http://calleam.com/WTPF/?tag=examples-of-failed-it-project).

Antigamente, com metodologias como o *Waterfall*, esse problema geralmente se perdia no meio de todo o processo. Era fácil culpar os testadores pelo tempo que levava para encontrar bugs e ainda mais fácil culpar as operações pelos atrasos ocorridos durante as tentativas de implantação. A segmentação de todo o fluxo e a ideia de que o tempo do projeto consistia principalmente na "Fase de codificação" mantinha oculto o problema específico de estimativa de recursos. Criar equipes multifuncionais para resolver isso ajudou a identificar e trazer à luz o processo defeituoso, mas poderia fazer pouco em um projeto de meses (ou anos).

O crescimento do Ágil, realizado pelo [Manifesto de Desenvolvimento de Software Ágil](https://agilemanifesto.org/), reconheceu esse problema e criou várias maneiras de lidar com ele. Existem sequências de Fibonacci, histórias de usuários do tamanho de camisetas, velocidade de sprint e muitas outras, e a idéia de quebrar projetos inteiros em uma série de pequenos minimizou o problema, porque, é claro, uma estimativa com uma semana perdida é muito melhor do que uma de um mês. Outra melhoria brilhante em comparação com os métodos mais antigos é a reação a mudanças, e o conceito de priorização de tarefas feito diretamente pelo interessado final no projeto. Ser capaz de mudar de rumo durante a chamada "Fase de Construção" é, provavelmente, a lição mais valiosa que o Manifesto Ágil trouxe ao mundo do software.

(que devemos estar sempre na "Fase de construção" é uma questão para outro post)

Com a soma de equipes multifuncionais, fateamento de backlog e priorização, conseguimos trazer todos os envolvidos ao processo deixando claro os esforços de construção de software. Com isso, pudemos explicar por que a feature X está demorando tanto para ser concluída e por que a equipe Y está se saindo bem. A taxa de entregas e o valor entregue de cada fase tornou-se claro e mais palpável.

No entanto, os projetos reais e de longo prazo ainda perdem o prazo. É algo tão difundido e aceito que algumas empresas simplesmente não fazem mais estimativas e, mesmo com a transparência de todo o processo, ainda lutamos para encontrar qualquer método sensato que traga algum nível (qualquer nível) de assertividade.

### Por que devemos nos importar?

Sou um grande fã do [Manifesto do Artesão de Software](http://manifesto.softwarecraftsmanship.org/). Penso que, no estado atual do mercado, o desenvolvimento de software está mais próximo da arte do que da ciência. Pegue dez desenvolvedores e peça a cada um deles a mesma tarefa. Observe como eles chegarão a você em momentos diferentes, com perguntas diferentes sobre a tarefa e soluções completamente diferentes, cada uma com uma parte que se move de forma estranha.

(essa é a razão pela qual acho que os desenvolvedores de software, apesar do estresse, [geralmente estão felizes com sua ocupação](https://www.forbes.com/pictures/mkl45eeilm/no-6-happiest-job-software-developer/#4f7da09b6186). Talvez não feliz com a empresa, mas com o ofício)

Obviamente, isso é um problema para qualquer negócio sério. [Planejar com antecedência e, mais importante, planejar assertivamente, é a diferença entre a vida e a morte de uma empresa](http://www.nasdaq.com/article/the-importance-of-business-planning-cm59436). Essa é a maneira atual de calcular valores de orçamento, monitorar metas e definir o sucesso ou o fracasso de um projeto. Deixar de fazer isso é o que torna o "Departamento de TI" o mais complexo a ser gerido em qualquer tipo de indústria.

[Não apresentar qualquer tipo de estimativa real e assertiva é uma falha de todo o setor e prejudica todos os setores que dependem de software](https://en.wikipedia.org/wiki/List_of_failed_and_overbudget_custom_software_projects) (no mundo de hoje, isso significa, "todos os setores "). Resolvê-lo, ou apenas melhorá-lo um pouco, nos aproximaria de formas mais maduras de engenharia.

(É por isso que geralmente evito o termo "Engenheiro de software", mas esse também é um tópico para outro post)

## Abordagens atuais

Como dito acima, o Manifesto Ágil abordou esse problema e trouxe algumas maneiras de mitigá-lo. Vou listar abaixo algumas das abordagens que experimentei e minha opinião sobre elas.

* **[Pontos de Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_scale_(agile))**: A forma mais rudimentar estimativa de tempo. O Scrum que a popularizou. O principal problema com este é que uma história de tamanho 13 não é igual a duas de 5 e uma de 3 (!). É por isso que não resolve de fato o problema de medir a velocidade da equipe.
* **[Pontos de função](https://www.codeproject.com/Articles/18024/Calculating-Function-Points)**: Este é realmente complicado e ... bem, ruim. Ele calcula um número que simboliza a complexidade dos requisitos, com base nas entradas e saídas do usuário e interfaces externas (entre outras coisas). Como as entradas do usuário são diferentes umas das outras e as interfaces externas podem variar muito entre si (tente integrar-se a um serviço da web Rest e Soap e me diga quanto tempo levará cada uma), o número sempre falha.
* **Histórias do mesmo tamanho**: tentar dividir todas as suas histórias em um tamanho semelhante para poder tirar uma mediana do tempo gasto em cada uma. Dessa forma, você saberá que, se um projeto tiver X histórias, levará Y tempo por história para concluir. A parte complicada é: "Como fatiar histórias com um mesmo tamanho?"
* **[Tamanhos de camiseta](https://www.mountaingoatsoftware.com/blog/estimating-with-tee-shirt-sizes)**: Mais sensato do que os pontos de Fibonacci, porque uma história do tamanho *M* não é a mesmo tamanho que dois *P*. No entanto, isso traz dois problemas: identificar a diferença entre a *M* e a *G* (e assim por diante) e calcular o tamanho apropriado do sprint. Simplificando, se sua equipe passou três meses fazendo apenas *M*, agora que você tem apenas *G*, quantas histórias eles podem encarar este mês?

## Conclusão

Não existe uma solução simples para o problema, mas a melhor maneira de atenuá-lo é quebrar o trabalho em pequenas etapas. Pessoalmente, não gosto de diminuir muito, porque toda história tem uma sobrecarga no processo (ou seja, uma história que é apenas uma mudança de caracter levará mais tempo para ser escrita e validada do que vale a pena), mas algo com "menos de uma semana" é mais que o suficiente.

Na minha experiência, vale a pena tentar fatiar as histórias para que fiquem do mesmo tamanho, ou o mais próximo disso possível. A principal ressalva é que os desenvolvedores precisarão ajudar a dividir as histórias, porque eles são os únicos capazes (já que conhecem os sistemas). Você também precisará estar confortável com fatias não ideais em prol da previsibilidade.

Além disso, tudo se resume ao gerenciamento de expectativas. Deixe claro para todos os envolvidos os planos e marcos. Quando as histórias começarem a se prolongar além do esperado, reexamine o problema e as estimativas. Transmita o passo a passo. Dessa forma, as partes interessadas podem planejar e reagir de acordo.

Com certeza não resolve o problema, mas o mitiga e transforma o processo em algo mais saudável e transparente