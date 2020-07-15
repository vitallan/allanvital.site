---
layout: post
title: Seu Sistema vai ser Reescrito
date: '2016-02-22 16:00:00'
permalink: seu-sistema-vai-morrer
---

*UPDATE: a minha visão sobre esse tópico é um pouco mais complexa nos dias de hoje. Um novo post deve vir para retificar*

Então, tem esse negócio sobre o seu sistema.

[Ele vai ser reescrito.](https://pt.wikipedia.org/wiki/Navio_de_Teseu)

Estou falando mais especificamente sobre os sistemas web, porque essa é minha área de especialização, mas é válida para várias áreas do desenvolvimento de software. Os sistemas são criados para serem destruídos e reescritos no longo prazo. E tudo bem.

Se você já trabalhou em algum grande projeto ou a alguns anos em uma empresa, já viu o que as pessoas chamam de "Código Legado". É mais  conhecido como código que é executado em produção por tanto tempo que as pessoas não sabem mais como ele funciona. Às vezes, esses sistemas legados mantêm os principais recursos de uma empresa, dos quais dependem todos os outros sistemas. Nesse caso, temos um cenário péssimo: minha “pedra fundamental” funciona, mas ninguém sabe exatamente como, e todo mundo tem medo de tocá-la.

Como isso acontece é simples:

1. Começamos com alguma equipe de desenvolvimento que cria o Sistema X
2. Todo mundo sabe tudo sobre o X (melhor cenário)
3. Com os novas funcionalidades entrando e os membros mudando (realocações, aposentadoria etc.), a entropia ocorre e as coisas ficam complexas
4. X cresce em complexidade e tamanho, e os membros não sabem como algumas partes funcionam
5. Os membros têm medo de tocar em algumas áreas de X, temendo os impactos gerais (geralmente os recursos mais básicos e complexos)
6. Essas "áreas escuras" aumentam em número até que haja mais "zonas de medo" do que "zonas conhecidas"
7. Todo o desenvolvimento atinge níveis realmente baixos de velocidade

Até o nível 5, alguns desenvolvedores já podem estar reivindicando que o sistema deve ser reescrito. Em 7, a velocidade geral de desenvolvimento chega a um ponto terminal, no qual o valor comercial entregue é quase nulo e mais desenvolvedores devem ser contratados. Infelizmente, essas novas pessoas geralmente pioram as coisas, por causa do ambiente já caótico.

(e por "piorar as coisas", quero dizer que eles geralmente adicionam camadas de abstração para evitar as "zonas de medo", que tornam as coisas ainda mais complexas)

Mas como você pode reescrever seu sistema principal? Tanto tempo gasto em um produto para simplesmente "recriá-lo" não parece ser um bom investimento.

(até hoje, os bancos continuam investindo mais em COBOL porque é TÃO DIFICIL e TÃO CARO tentar reescrever todos os sistemas que eles aparentemente desistiram de tentar. Não posso culpá-los)

Pensando neste problema (e como resolvê-lo), podemos ver que esse comportamento potencialmente ocorrerá em qualquer sistema. Com a aceleração da tecnologia, um novo sistema pode se tornar obsoleto em menos de um ano. Vi recentemente um ser chamado de "legado" em seis meses. E sim, às vezes é apenas a vontade dos desenvolvedores de experimentar coisas novas, mas esse cenário deve ser analisado para verificar a veracidade.

Com essas informações em mente, podemos chegar à próxima conclusão: em um projeto que está planejado para durar mais de um ano (falarei sobre estimativas em outra ocasião), há uma boa possibilidade de que ele nasça com o rótulo "legado". E quero dizer, qualquer sistema, não apenas projetos de "reescrita".

Lembro-me claramente de uma de minhas antigas experiências, em que estávamos trabalhando com um sistema antigo enorme e, após grandes discussões políticas, a equipe de desenvolvimento conseguiu a aprovação da empresa para recriar o sistema. Inteiramente, do zero!

Fiquei feliz com a decisão e parecia o caminho certo. Então eu fui falar com um dos programadores seniores sobre isso, e ele me perguntou: “Isso é bom ... mas o que está nos impedindo de não esbarrar no mesmo problema no futuro?”, E até hoje não sei o que poderia ter respondido a ele. Acredito que essa seja uma das maiores questões no desenvolvimento de software comercial.

Não acredito que haja uma maneira de resolver esse problema, mas acredito que existem maneiras de mitigá-lo. Testes unitários ajudam muito, mas eu vejo isso mais como uma maneira de ajudar na manutenção do que facilitar a reescrita. Ajudam, mas se você quiser mudar a tecnologia, provavelmente jogará fora toda a suíte.

(mas não posso esperar resolver nada em um projeto que não tenha testes de unidade. É o mínimo necessário em um projeto sério)

Acredito que a melhor estratégia é abraçar a idéia de reescrita. Manter os sistemas legados em execução é realmente caro, e contratar pessoas e treiná-los para aprender algo com um software antigo é ainda mais caro. Portanto, acho que abraçar a ideia é o melhor caminho.

“Mas continuarei reescrevendo meu sistema o tempo todo? Como posso encontrar tempo para fornecer novos recursos? ”, Posso ouvir suas alegações, leitor hipotético, e entendo você.

O meio termo seria: manter os sistemas tão pequenos que o processo de reescrita demore semanas e não anos. Para alcançar esse cenário, você precisará separar seu software em vários subsistemas, e não estou falando somente de arquitetura de componentes ou plug-ins. A idéia é ter um ecossistema de software, idealmente se comunicando via REST, para reforçar a idéia de peças soltas levemente conectadas e forçar os desenvolvedores a alcançar uma interface de serviço ideal. Para manter tudo junto, você precisará, além dos testes unitários, de testes complexos de integração, que atinjam cada um desses sistemas. Dessa forma, você pode simplesmente jogar fora um e recriá-lo sem muita dor e ter a garantia de que todo o resto funciona.

Sim, estou falando sobre arquitetura de microsserviços.

Acredito que hoje, com a tecnologia em nuvem ao nosso alcance, isso seja possível e desejável. Podemos criar e destruir VMs de maneira automatizada e manter todo o ecossistema sem downtime. Se você não pode usar a nuvem de maneira plena, docker e kubernates podem ser seus melhores amigos. Você tem ferramentas para pensar sobre essa implementação.

Entendo que os microsserviços são hoje uma palavra da moda e, se você não gostar, chame isso de arquitetura de serviços, mas o conceito existe há algum tempo, até mesmo o conceito de "quebrar grandes problemas em uma série de pequenos" é o núcleo do desenvolvimento orientado a objetos. Deveríamos pensar mais sobre isso e usar esse conhecimento com mais frequência.