É fato que nós programadores fomos agraciados com o poder de construir o que quisermos, desde que tenhamos criatividade e paciência. Entretanto, a depender do tipo de aplicações que acabamos criando, seja para portfólio, ou para validar algum Micro SAAS, vamos acabar nos esbarrando em uma das únicas verdades verdadeiras do mundo: *Nada é de Graça*.

Com isso acabamos nos forçando a usar serviços pagos que nos trazem qualidade de vida para o nosso projeto. Entretanto nem todo mundo tem dinheiro para manter tantos projetos, que não trazem nenhum retorno financeiro, no ar. 

### Com isso te pergunto: 
- Você sabe como criar Aplicações Fullstack de graça? 
- Você sabe como deixar essas Aplicações Fullstack bem otimizadas, para melhorar a performance desses serviços gratuitos?

Nesse artigo vamos falar sobre:
- Hospedar a sua aplicação gratuitamente;
- Usar o Next.js como Framework principal para a construção da API do sistema:
	1. Stacks inusitadas: EJS + Next.js;
	2. Usando Frameworks intermediários para servir de Controladores para o Next.js;
- Hospedar Bancos de Dados Gratuitamente(MongoDB Atlas, Supabase e Turso):
	1. Problemas de consumir diretamente os serviços de bancos de dados com o Plano Gratuito;
- Uso de Cache para melhorar o tempo de resposta dos bancos de dados;

---
# 1. A Verdade sobre Criar Aplicativos Fullstack de Graça
A hora de desenvolver é fácil. O problema é justamente quando o seu projeto está maduro o suficiente para você poder hospedar. E assim, criar APIs usando Express.js ou Fastify é tranquilo para hospedar. Você tem pode usar plataformas como Render, Fly.io, e até mesmo provedores maiores como a Amazon e a Cloudflare, que estão disponíveis para qualquer pessoa poder usar.

Entretanto, usar um serviço pago que não te dá o controle da máquina que está rodando o seu produto acaba te limitando. Você acaba precisando usar outros serviços para poder complementar a sua Stack. Ou seja, se você está hospedando uma API escrita em Elysia com Bun na Railway, e precisa de um banco de dados que seja rápido e esteja disponível 24h por dia, você acaba tendo 2 caminhos: 
- Usar o serviço de Database da Railway e passará a pagar pelo custo computacional;
- Procurar um serviço de Database que vai fornecer esses dados para a sua API;
E para a minha infelicidade, nenhuma das duas escolhas são sensatas.

A ideia de criar aplicações sem ter que pagar nada é uma forma excelente de validar ideias, porém é quase que utópico. Todas os serviços gratuitos possuem um problema de performance. As máquinas usadas são extremamente fracas, e elas servem justamente para nos dar o gostinho de usar uma versão profissional.

Como um bom programador Programador Pobre(PP), eu comecei a repensar justamente em como criar uma aplicação que aproveite ao máximo desses serviços gratuitos, mas que de algum modo seja possível reduzir parte dessa má performance. Como?

---
# 2. Explicando a Stack
Inicialmente a ideia era de usar o Next.js como Framework Fullstack, juntamente com o MongoDB Atlas – serviço esse que oferece plano gratuito para hospedar o banco de dados MongoDB – mas acabou que o retorno para as chamadas se torna extremamente lento, tendo tempo de resposta de até 1.5 segundos para requisições simples.

O Next.js em si é um bom Framework. Ele possui features que te permitem renderizar páginas ou componentes React do lado do servidor. Além do mais, ele possui uma feature chamada de Route Handlers.

O Route Handler do Next.js permite que consigamos criar uma API para o seu projeto em Next.js num só lugar. Cliente e servidor, tudo em um só lugar. Divertido, não?

Errado. Além de ser um processo bem chato – pois qualquer rota que você criar, você precisa criar uma pasta, e nela colocar o arquivo `route.ts` –  ela acaba oferecendo um método porco para criar essas rotas.

Quem já criou alguma API na vida, e tenha conseguido escapar do MVC clássico, sabe que não é interessante você criar as regras de negócio de um produto dentro dessa rota. E aí o projeto começa a crescer.

Diversos diretórios que vão representar camadas diferentes da aplicação vão se somar aos diretórios já existentes do site. Ou seja, a pasta de `services`, `repositories`, `factories`, ficará na mesma raiz que `components`, `stores`. É uma salada de frutas, e é uma das coisas que eu mais tento evitar, mesmo falhando miseravelmente algumas vezes.

Apesar de tudo isso, usar o Next.js como um Framework para criar API acaba sendo até que engraçado, porque você acaba criando combinações inusitadas: Next.js com EJS. Se as pessoas já reclamam do Next.js parecer em certos aspectos com o PHP, o EJS no Next.js escancara ainda mais essa semelhança. 

Contextualizando, o EJS é uma biblioteca para JavaScript que oferece uma linguagem de template. Ou seja, o EJS será um arquivo, que para gerarmos iremos precisar dos argumentos desse template, e aí o conteúdo será gerado. Pegando esse conteúdo e colocando na Response do Next.js nós temos algo bem próximo ao PHP, o que é bem divertido, mas não façam isso em casa. Usar o Next.js sem o React, e usar uma outra forma para carregar o conteúdo do site acabam tendo diversas limitações. E é um processo bem complicado. Já adianto logo que, se você quiser fazer um redirecionamento nessa rota e tentar enviar algum cookie para ser redirecionado, você passará por algumas dores de cabeça, mas que provavelmente você vai pensar em alguma gambiarra legal e vai fazer.

Eu peço que vocês não se horrorizem com essa ideia. Eu só estou usando essa Stack de Next.js com EJS por conta de 2 projetos que eu fiz em 2023 e queria deixar funcionando na Web. E é bem complicado de fazer isso, porque o projeto foi feito em JavaScript, Express, Sequelize e EJS, mas agora eu preciso migrar todo o coração do código para algo que faça sentido pra mim: Usar os padrões que eu acabei aprendendo ao longo do tempo é um deles. Mesmo que eu só esteja querendo deixar online, eu não vou deixar de qualquer jeito. A ideia é manter apenas o site idêntico mesmo, e é o que eu estou fazendo desde o início.

---
# 3. Conhecendo um pouco do Next.js
Apesar de eu ter mencionado que o Next.js seja um Framework Fullstack, capaz de processar dados no lado do servidor, o Next.js nesse contexto – com API Routes e hospedado na Vercel – usará Serverless como padrão para funcionar.

Para quem não entende o conceito de Serverless, imagine que ao invés de você manter um servido rodando a todo o momento – como acontece em servidores tradicionais com Fastify ou Express – você só executa partes específicas da sua API quando elas são realmente chamadas.

Mas por que isso é interessante?

Redução de Custos. 
> Ao hospedar uma API no modelo Serverless, você tira a necessidade de manter um servidor funcionando o tempo todo. Sua API responde imediatamente, e sem a necessidade de `cold start`, que é algo comum em servidores que não usam Serverless. 

Mas qual seria o custo de se criar aplicações Serverless, em comparação à criação de aplicações convencionais?

O Ambiente.
> Quando se desenvolve aplicações Serverless, é comum que algumas features relacionadas à runtime, não existam. E nesse contexto de estar reescrevendo APIs em Express para Next.js foi o que mais me causou problemas.

O Next.js não te dá muito controle sobre a passgem desses dados, a não ser que eu os salve em Cookies. Dito isso, usar Cookies é a única forma de registrar dados de sessão, e isso acaba fazendo com que eu tenha que criar algumas gambiarras no código, para que ele funcione da mesma maneira que a versão antiga.

Apesar disso, uma das coisas que o uso do Route Handler nos beneficia, é que podemos utilizar Frameworks auxiliares para a criação de controladores, o que melhora significativamente na organização do código. Frameworks como Elysia e Hono podem ser oferecidos como `handlers` para as rotas da nossa aplicação. 

Aqui está um exemplo do que pode se fazer agora com o sistema de diretórios da nossa aplicação quando usamos o Elysia juntamente com o Next.js:

```
| src
	| app
		| api
			...
		...
	| components
	| controllers
	| repositories
	| services
```

Futuramente eu pretendo falar mais sobre o Next.js e suas particularidades, mas acredito que pelo tópico do artigo(e pelo tempo de leitura que ficaria se eu decidisse falar sobre as particularidades do Next.js), eu vou preferir por falar numa outra hora.

---
# 4. Como reduzi o tempo de 1.5s do MongoDB Atlas para 232ms?
Usar o MongoDB da forma que eu estava habituado a usar está bem complicado. Além de demorar muito para responder, existe a chance de rotas caírem simplesmente por conta de alguma conexão que foi interrompida ou encerrada. Uma das soluções que eu acabei encontrando foi o uso do cache.

Usar cache em API é uma tarefa comum e que acaba reduzindo às consultas repetitivas aos mesmos campos salvos. Ao invés de fazermos uma busca total no banco por valores previsíveis, vamos fazer apenas uma consulta e armazenar a resposta. Quando for necessário consumir esse valor cacheado, e ele estiver válido, ele irá retornar. Caso não esteja mais válido, uma nova consulta será feita. E para a minha surpresa, a diferença da consulta direta no banco para com a consulta no cache foi esmagadora: Consegui sair de 1.5s para 232ms, um resultado surpreendente para uma troca de metodologia.

O serviço que eu estou usando para hospedar o Redis é o Upstash, e ele possui diversas features interessantes para o seu projeto, e pretendo falar mais sobre a Upstash futuramente em algum outro momento. E sim, eu estou usando o plano gratuito.

---
# 5. Além do MongoDB 
Com o re-desenvolvimento desses meus projetos antigos, teve algumas situações que eu não consegui simplesmente usar o MongoDB em toda ocasião. Principalmente quando se tinha muita regra de negócio no banco de dados, e quando a sua base estava em Sequelize. E como a ideia é manter a essência desses projetos, eu acabei optando por usar o Supabase com o Prisma, o que foi uma escolha bem tranquila para a minha experiência de desenvolvimento.

Eu tenho os meus problemas com o Prisma, mas desde que ele passou a exportar a tipagem automaticamente, eu sinto que eu não tenho muito o que reclamar dele, então só aceitei a sua existência e uso quando eu preciso fazer algo simples.

Além do Supabase, tem o Turso, que eu de fato queria parar para ver sobre, e talvez em algum futuro projeto, eu o use, mas por enquanto vou ficar em paz com o Supabase + Prisma + Redis. Para quem não conhece o Turso, ele é um serviço de banco de dados em SQLite, só que voltado especificamente em servidor.

---
# 6. Conclusão
Eu acredito que ao longo desses meus 3 últimos artigos, eu consegui encontrar parte de uma Stack que desde o início eu não tinha grandes expectativas, mas é interessante pensar que tudo isso surgiu de uma ideia de poder hospedar a API do meu site sem gastar nada.

Começamos falando do site; Depois fomos falar da API; e por fim, amadurecemos parte desse back-end. E por mais que parte dessa ideia de Programação Orientada à Pobreza seja uma piada, eu sinto que consegui não só abrir mais a minha cabeça sobre estar preparado para o pior cenário possível, como também, incentivar você leitor, de conhecer coisas novas.

E como um bom Programador Pobre, eu estou até valorizando esses meus projetos zero custo, porque essa ideia de escassez acaba fazendo com que você busque alternativas incomuns para otimizar ao máximo o custo, o que é bom até para casos reais.

Essa stack ainda é problemática em alguns sentidos, mas eu pretendo ir aperfeiçoando ela com o passar do tempo, e dos textos que eu vou desenvolvendo. 

Eu pretendo falar mais sobre o Next.js em algum momento, ou em alguma série no meu canal do Youtube, para mostrar um pouco mais sobre as features dele, sem falar de React. O foco é falar sobre o seu funcionamento, e sobre como você pode usar alguns de seus defeitos a seu favor. 

Programação é mais sobre você entender o fluxo dos dados do que qualquer outra coisa. Entendendo o fluxo, você consegue criar soluções inteligentes para problemas, fugindo daquela ideia de gambiarras, ou POGs.

Além disso, eu pretendo abordar futuramente sobre pub/sub em ambientes Serverless, e sobre a documentação de APIs com OpenAPI e Scalar, mas é tanta coisa nova para descobrir e aprimorar, que daria pra fazer um livro só sobre isso.

No fim, foi um artigo bem interessante. Ele me fez repensar muito sobre a forma que eu venho desenvolvendo minhas aplicações e vocês estão acompanhando esse processo. Gostaria de agradecer a todos vocês que estão me acompanhando.

Inclusive, você tem algo a incrementar? Algo a sugerir? Opiniões e sugestões são sempre bem-vindas!

Até mais!
