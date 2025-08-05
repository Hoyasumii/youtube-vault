Logo após que eu terminei de construir o meu site, como podem ver nesse [artigo](https://www.tabnews.com.br/hoyasumii/como-eu-criei-o-meu-site-pessoal-depois-de-tantas-tentativas-e-o-que-aprendi-no-processo), eu decidi criar a API do meu site, pois um dos defeitos que a minha versão antiga tinha, era a ausência de uma API que conseguisse atualizar o conteúdo do site automaticamente.

Para a minha infelicidade, eu estou desempregado e sem um centavo para poder arcar com AWS, ou outros serviços como a Railway. Com isso, criar essa API seria uma tarefa quase que impossível, pois eu não sabia onde faria o deploy da minha API, nem qual banco de dados eu usaria.

A ideia da API em si era bem simples, porque o único objetivo era listar minhas coisas. 

Eu não preciso de um Dashboard, nem tela de login. Preciso apenas criar rotas para exibir meus Artigos e meus Projetos, apenas. E aí eu me perguntei: Qual Stack eu vou escolher para publicar as minhas aplicações?

Já tem mais de um ano que eu uso Next.js em meus projetos, e embora eu tenha diversas críticas à Vercel, é um framework que eu acabo gostando muito de usar, principalmente por conta dele ter a proposta de ser um framework FullStack para React. Ele acabou implementando a renderização do lado do servidor para a geração de sites, semelhante com o PHP, graças ao fato do Next.js executar um servidor HTTP. Com isso também se torna possível criar suas próprias API's. Com isso vem o primeiro ponto que eu gostaria de falar sobre:
# 1. Escolha uma Stack Poderosa
Escolher a sua própria Stack é uma tarefa bem complicada. O que você usar no Front-End, no Back, e qual banco escolher? São muitas perguntas que acabam pesando na hora de publicar um projeto, mesmo que seja um projeto de portfólio. 

Uma boa Stack pode te poupar horas de dores de cabeça, e te prepararem para problemas que você não vai querer ter, mas quando a Stack acaba sendo fraca, você provavelmente passará pelas piores dores de cabeça, nos piores momentos possíveis, e isso pode **FAZER VOCÊ GASTAR DINHEIRO**, o que não queremos agora.

A partir de agora, eu vou falar sobre a Stack que eu venho usando para resolver um dos meus principais problemas: A Criação da minha API.

Criar a minha API não foi difícil, mas isso foi por conta de algumas coisas que eu já tinha sabia, e da API da [dev.to](https://dev.to/guilhermecheng/how-to-use-devto-api-4p65), que é um dos lugares que eu publico meus textos. A API da Dev.to consegue listar os artigos que você posta, e ele consegue diferenciar seus artigos por idioma, e como o meu site tem apenas 2 versões, a Estadunidense e a Brasileira, eu implementei um filtro do lado do servidor para exibir os artigos de acordo com o idioma escolhido, e fiz a consumação da API para exibir todo esse conteúdo. Com isso, minha tarefa acabou ficando mais leve e tranquila, restando agora a tarefa de listar os meus projetos.

Beleza, qual framework e qual banco de dados eu devo escolher?

A indecisão foi grande entre o **Fastify** e o **Nest.js**. O Fastify é um Framework que facilita muito o desenvolvimento back-end. Ele possui ferramentas nativas que dão qualidade de vida e facilitam o desenvolvimento de testes E2E, o que é incrível se eu quiser implementá-los.

Já o **Nest.js**, é um Framework de API REST com princípios e opiniões bem definidas. O que acaba sendo uma escolha bem interessante para quem quer ter um nível mínimo de decência 
no código. Entretanto, o **Nest.js** acaba sofrendo demais com o acoplamento de seus próprios mecanismos. Várias opiniões que acabam complicando o desenvolvimento à longo prazo. Para solucionar esse alto acoplamento, eu acabo sendo obrigado a criar soluções que desacopla ao máximo o meu projeto Nest.js. E vou ser sincero: Mesmo que eu não tivesse com que me preocupar com o Deploy da API, eu não escolheria o **Nest.js**. Ele é muito robusto para a minha aplicação, e eu teria que fazer muitas classes e factories pra fazer as coisas da forma que eu gosto. 

Eu acabei deixando para depois a minha escolha de Framework de API, e comecei a escolher o banco de dados. Para a minha felicidade, eu me lembrei que o **MongoDB** possui uma ferramenta chamada de *Atlas*, que é um serviço de hospedagem dos bancos **MongoDB**, e que oferece 500mb de armazenamento no seu plano gratuito, o que para armazenar poucas informações acaba sendo uma boa escolha. 

Usei o **Mongoose** como ODM e defini os modelos das **Coleções** na camada de `schemas`.  Falando em camadas, eu escolhi seguir com uma Arquitetura Limpa. Mesmo que seja um projeto simples, seguir com essa arquitetura me deixará despreocupado com o acoplamento do meu código, em contrapartida, eu terei que escrever muito mais, e foi o que eu precisei fazer.

# 2. Como organizar o seu projeto?
Quando você não tem prática com back-end, você acaba tendo que lidar com vários problemas que irão surgir no desenvolvimento da sua API, sendo comumente associado na distribuição correta de camadas, e isso acaba sendo um processo que levará semanas até que você consiga entender todo o seu funcionamento, mas confia em mim que esse processo de aprendizado acaba sendo compensado com o passar dos seus próximos projetos.

![estrutura-api.png](/estrutura-api.png)

Essa imagem é um resumo de como eu organizo o coração do meu código. 

O fluxo é bem simples: 
1. Iremos sempre criar uma camada de persistência para os nossos dados com um Repositório. 
2. Com o nosso repositório, precisaremos de uma camada para executar os métodos de um repositório somado ao processamento dos dados. Ou seja, validações, erros, tratamentos, acontecerão nessa camada. 
3. Para concluir, precisamos de uma Factory para retornar o serviço já instanciado. 

É um fluxo simples, mas para quem está começando é algo bem complicadinho de entender.

![estrutura-api-2.png](/estrutura-api-2.png)

Com a base do código feita, eu consigo mover essa base para **qualquer framework que existe**, já que todo o seu funcionamento é separado em camadas, e eu acabei me lembrando de uma ferramenta que existe e que faria toda a diferença.

# 3.  Escolhendo o Next.js para especificar as Rotas
Como eu mencionei antes, eu uso o **Next.js** há um tempo considerável, e uma das features que mais me incomodou quando surgiu foi o *Route Handlers*. Embora hoje seja a ferramenta que mais me ajudou a deixar as minhas APIs de graça para hospedar, eu nunca tinha visto um motivo real para criar uma API com **Next.js**, mas quando eu percebi que a vantagem de se fazer isso era de justamente facilitar o processo de deploy de uma aplicação inteira, eu passei a valorizar essa feature e adotei em meus projetos mais antigos, que nem sequer conseguiam ficar online, para revitalizá-los.

O **Next.js** acabou facilitando e muito o meu processo. Eu pensei que faria essa API em pelo menos 3 dias, já que a minha ideia para facilitar esses custos era usar o **AWS Lambda** e o **AWS API Gateway**, mas como eu percebi que usar o **Next.js** seria mais fácil e rápido, o processo de criação foi encurtado, eu consegui criar a API em poucas horas e consegui fazer com que o seu custo para funcionar permanecesse em US$0.00, ao hospedar na **Vercel**.

# 4. Uso da Stack para contextos peculiares
Um dos momentos mais interessantes que eu estou passando nesse meu processo de deixar todos os meus projetos concluídos online é quando eu acabo usando o **Next.js** em ocasiões que ninguém costuma pensar nisso, como é o caso de eu estar usando **EJS** com **Next.js.**

Para quem não sabe, o **EJS** é uma biblioteca para **Node.js**, que oferece uma *Template Engine* para que você consiga usar no seu projeto Node.js com o MVC clássico: Aquele projeto que só tem Model, View e Controller.

Por que eu estou usando Next.js com EJS?

Um pouquinho de contexto: Quando eu estava aprendendo Node.js, 2 anos atrás, eu acabei aprendendo o EJS para criar os meus projetos, e existem 2 projetos meus que usam EJS: Um blog, e um fórum de perguntas e respostas. Como é um projeto de 2 anos atrás, eu decidi conservar todo o seu funcionamento externo, me preocupando apenas com reescrever a base do código. Reescrevendo o back-end, e o organizando. O processo em si é bem chato, mas acaba sendo recompensador, porque imagina você conseguir colocar no ar, uma aplicação, que na época que você criou, você não sabia como colocar no ar?

Para a minha felicidade, eu não terei que fazer isso novamente, porque depois que terminar todo esse processo de ajeitar o meu portfólio, eu vou querer criar coisas maiores e mais interessantes pra mim e pra comunidade.

# 5. O Programador Pobre
O programador pobre não é aquele que tem pouco dinheiro, e que tem dificuldades em manter projetos no ar por causa do custo: É aquele que não consegue criar projetos, sem ser da forma que aprenderam inicialmente. Na nossa profissão teremos diversos desafios até que cômicos de certo modo, mas precisamos nos superar a cada dia.

Entenda o seu projeto, pois entendendo-o, você conseguirá resolver seus problemas de formas inimagináveis, e isso até te incentiva a aprender mais.

Num dos projetos que eu estou reescrevendo, eu estou trocando a base de Express para Next.js, e vou usar o EJS como Template Engine. Mas ao invés de usar o MongoDB como database, eu decidi usar o Supabase, que eu nunca usei antes, com o Prisma. Eu acabei solucionando uma das dores que eu tinha para Hospedar o meu banco de dados, e agora eu tenho 2 soluções que consigo usar para os meus projetos.

Eu estou bem satisfeito com o resultado desse meu projeto, pois eu consegui criar uma nova versão do meu site, e também pude encontrar formas não convencionais de criar as minhas aplicações.

Inclusive, finalmente terminei o projeto do meu site, e quem tiver curiosidade em acessar, basta acessar: [https://alanreis.blog](https://alanreis.blog). Foi um trabalho bem cansativo, mas que trouxe muita bagagem pra mim. Inclusive, todos os meus projetos que estão no meu site, possuem repositório público. No momento atual está faltando apenas 2 projetos, mas a intenção é que em poucos dias, os projetos estejam concluídos. 

Muito obrigado a todos que tenham lido esse artigo, e acabou me acompanhando nessa jornada do meu site pessoal!

Até mais!

