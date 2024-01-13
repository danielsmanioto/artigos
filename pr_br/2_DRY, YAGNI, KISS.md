Título: 
DRY, YAGNI, KISS ? Princípios de Design de Software que todo desenvolvedor deveria seguir.

Vamos falar sobre três Software Design Principles ou Princípios de Design de Software. 

Desenvolvedores têm desafios todos os dias e, é sabido que independente da solução e linguagem utilizada,  é possível ter o mesmo resultado de muitas formas diferentes. 

É comprovado que juntar vários programadores diferentes e pedir para que eles escrevam algo esperando um resultado, certamente todos ou a grande maioria será diferente.  

Indiferente dos requisitos necessários para a solução o importante para nós desenvolvedores manter nosso código escalável, é escrever ele de forma que outros desenvolvedores consigam entender o código com facilidade e evolui-lo se necessário. 

Passamos boa parte do tempo lendo código e, é importante escrevê-lo de forma com que qualquer outro desenvolvedor consiga entendê-lo de forma rápida.

Com o propósito de ter sistemas mais escaláveis e de fácil manutenção,  aos passar dos anos programadores experientes tentaram definir alguns padrões e boas práticas para dar uma direção à outros desenvolvedores.  

Existem vários destes padrões e alguns foram catalogados como é o caso dos tão falados Design Patterns e SOLID, mas isto é assunto para outro artigo. 

Estou aqui hoje para falar de três princípios básicos de design de software que muitas pessoas inclusive já utilizam sem saber ao certo que isso é usado como princípio para qualquer linguagem de programação que você utilize.

Caso vocẽ não conheça, comece a pensar com carinho na utilização deles. 

DRY: Don’t Repeat Yourself 
Na tradução para o português: Não se repita.

Este princípio surgiu no livro The Pragmatic Programmer escrito por David Thomas e Andrew Hunt.

Você já deve ter se deparado com códigos idênticos espalhados pelo mesmo sistema. 

Se o código é responsável por resolver o mesmo problema, o DRY orienta a arrumar uma forma de manter o comportamento único em um local. 

O objetivo principal aqui é de ajudar na manutenção e evolução do sistema.

É claro que é preciso tomar muito cuidado com coisas genéricas. Mas sempre é possível achar uma forma de manter este comportamento único em um mesmo local. 

Os primeiros passos são :
Procurar por todo código fonte do seu sistema se a solução que você está tentando implementar já não existe. 
Se precisou duplicar/copiar alguma coisa.  Pense, porque não tornar este trecho de código único, e simplesmente chamar nos lugares desejados.
Não esqueça de criar testes unitários, para garantir que os próximos desenvolvedores não quebrem o seu trecho de código tão bem implementado.
E para completar as grandes vantagens do DRY.

Economia de tempo e esforço
Facilidade de manutenção do código
Redução de possíveis erros.

KISS -“Keep It Simple, Stupid” 
Na tradução para o português: Mantenha simples, idiota.

O código não deve ser complexo, estamos escrevendo para humanos entenderem e para isto com certeza usa o conceito de mais é menos. é essencial . 

Quanto mais simples é seu código, mais simples será para dar manutenção nele depois. 

Acho a frase escrita por Martin Fowler no classico livro Refactoring - Improving the Design of Existing Code muito pertinente para isto:

“Qualquer tolo consegue escrever código que um computador entenda. Bons programadores escrevem código que humanos possam entender”

Um código simples de se entender tem como as principais vantagens evolução do sistema e até economia de tempo, tanto para quem está lendo quando para quem precisa evoluir o código.  

YAGNI:  You Aren’t Gonna Need It

Na tradução para o português:  Você não vai precisar disto. 

Quem nunca quis criar um recurso só por achar que um dia ele pode ser usado, alguns até acham bacana ser proativo e criar este algo a mais.
Porém quando estamos falando de escrever um bom sistema isto deve ser evitado.

Ou seja , se não for usar nem faça simples assim.  
Código desnecessário faz com que o seu sistema encha de coisas desnecessárias e muitas vezes de difícil manutenção.  

Considerações Finais 

Os princípios foram criados para dar uma direção para nós desenvolvedores, com objetivo te sempre melhorar o código e o sistema que estamos trabalhando.   

Pense com carinho nesses princípios, antes de sair escrevendo código por ai.

Abraços e até a próxima

