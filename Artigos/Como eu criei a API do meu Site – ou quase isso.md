Logo após que eu terminei de escrever o meu site, como podem ver nesse [artigo](), eu decidi que iria criar a API do meu site, pois um dos defeitos que a minha versão antiga tinha, era a ausência de uma API que conseguisse atualizar o conteúdo do site automaticamente. 

Diferentemente da versão anterior, eu farei uma API para o meu site, para que eu só precise mexer no site para aprimorá-lo. Sério, se você é programador e tem um site pessoal, seu site provavelmente tem uma API. Caso não tenha, você pode ter o seu site muito desatualizado, ou que terá que fazer manualmente toda vez que você aprende uma nova tecnologia, ou finaliza um projeto novo. Como eu não quero isso, eu vou criar a minha própria API.

Como uma continuação ao meu outro artigo, eu decidi que vou registrar desde o meu processo  criativo, até o desenvolvimento, seguido do Deploy.
# 1.  23 de julho de 2025
Após eu finalizar o site, eu acabei indo listar as funcionalidades que a minha API teria:
- Listar os meus Artigos;
- Listar os meus Projetos;
- Permitir com que eu pudesse gerenciar os meus Projetos;
- Listar as minhas Habilidades;
- Permitir com que eu pudesse gerenciar as minhas Habilidades;
- Internacionalizar os conteúdos;
E com isso, acabei fazendo uma modelagem básica, sobre o que o meu código teria.

Para a minha Stack, eu decidi usar o que eu mais tenho hábito: O bom e velho TypeScript com Fastify. Já tinha um tempo que eu não trabalhava com Fastify, e o último Framework que eu trabalhei foi o NestJS, mas como eu acho que o NestJS é muito robusto para o que eu estou querendo fazer – e eu teria que fazer muita coisa manual no Nest, para eu poder fazer algo que me trouxesse conforto –, eu acabei optando pelo Fastify mesmo, pela sua facilidade e performance. 

Normalmente, nos meus artigos eu não vou ter o hábito de ficar falando de tecnologia, mas como o foco do artigo é mostrar parte do meu processo, eu achei interessante falar. 

E no momento que eu comecei a desenvolver a feature de listar os artigos, meu amigo me falou de usar a API do [dev.to]() para listar os artigos. Eu comecei a testar a API, e vi que parte do meu problema já estava resolvido! Era só eu consumir a API e filtrar os artigos pelo idioma – por causa da internacionalização do site – que estava tudo certo. Com isso, acabei tendo mais alguns dos meus delírios, que me permitiu criar um novo componente para exibir esses artigos. 

![[Captura de Tela 2025-07-24 às 02.02.27.png]]

Genuinamente eu gostei do resultado, e acabei me empolgando um pouco mais e criei uma tela para exibir esse artigo, ao invés de ser um simples link.

![[Captura de Tela 2025-07-24 às 02.03.27.png]]

Beleza, e agora como a parte de Artigos está finalizada, eu decidi passar todos os meus artigos para a [dev.to](), que provavelmente vou fazer amanhã pela manhã, e com isso acabei me fazendo perguntas simples:
- Onde essas imagens estariam armazenadas?
- Onde eu faria o deploy dessa API?
- O que eu vou fazer para colocar conteúdo no meu site enquanto a API não está pronta?

Meu deus, eu preciso pagar a AWS.

Mas antes disso, decidi criar uma solução superficial que vai resolver os meus problemas, enquanto a API não dá sinais de vida: Vou criar tipagens básicas, e vou criar um JSON público que vai mostrar esse conteúdo. As imagens ficarão públicas, enquanto a API não está pronta e o site está no `preview`. Quando sair do `preview`, eu removo as imagens e o JSON público.

Nessa tipagem, acabei me interessando também em tipar as opções de SkillIcons, para melhorar no meu desenvolvimento. O processo em si foi fácil, entretanto acabei vendo que existem vários projetos meus que estão finalizados, mas que estão engavetados. Eu acredito que farei uma espécie de saga para o enriquecimento do meu portfólio. Tem vários projetos que eu quero atualizar o visual, e outros que estão finalizados, precisam apenas de um deploy para rodar. Tudo isso eu planejo fazer para poder seguir em frente.

---
# 2. 24 de julho de 2025
Percebi que tenho mais de 7 projetos que precisam estar online – e alguns precisam de ajustes críticos para poder continuar funcionando. O que farei? Provavelmente eu vou ir ajeitando esses projetos aos poucos, mas que começarei com o `poketwo`, um dos meus inúmeros projetos que faço sobre Pokémon para praticar minhas habilidades na programação. Como ele já está online, só preciso trocar o domínio e ajeitar o link.

Para a minha infelicidade, me deparei com um projeto que não usa TypeScript, e o Biome está alertando para vários erros. Depois de corrigir esses erros e colocar o Biome, eu passei por problemas na hora do Deploy na Vercel. Tanto por conta da versão usada no Vercel, como também no Corepack da Vercel, e nas versões das bibliotecas usadas. Mas depois de inúmeras tentativas, eu consegui ajeitar e troquei o domínio para [poke2.alanreis.blog](https://poke2.alanreis.blog). Um outro projeto que eu vou precisar ajeitar é o do Task.me, que eu pretendo fazer isso num momento futuro, antes de eu nerfar ele, e transformar num projeto que usa apenas `LocalStorage`.

Continuando em projetos que eu preciso colocar de Portfólio, temos o [encurtai.com](https://encurtai.com), que parando para olhar, o seu back-end é bem simples, e eu consigo colocar dentro do próprio cliente. Mas como? Graças às rotas do Next.js. Vercel, embora eu te critique bastante por conta das suas decisões, mas você facilitou a minha vida! 

Para resumir, o encurtai é um encurtador de link como qualquer outro, e serviu mais para um projeto de portfólio do que qualquer outra coisa, mas agora eu preciso pensar em como seria o seu funcionamento num contexto de não ter um back-end próprio. Qual foi o banco de dados que eu tinha escolhido na época? MongoDB. Para a minha felicidade em não ter que lidar com Prisma – nem serviços de hospedagem de banco – decidi usar o MongoDB Atlas, pois o plano gratuito vai servir para deixar o projeto rodando.

E para a minha felicidade, em menos de 2 horas eu consegui ajeitar o meu projeto para rodar inteiramente no `Next.js`. Quem for atrás desse projeto no meu GitHub não se assuste com o monstro. Esse código foi feito há 1 ano atrás e eu só implementei de modo que funcione corretamente. A configuração do Atlas foi tranquila, e a Vercel consegue lidar com CRON's e CORS, que eram 2 dos meus problemas iniciais. Isso me faz refletir sobre um contexto de escassez hipotético, que o uso dessas ferramentas se tornam meio que obrigatórias, se você quiser zero custo de manutenção, mas é aquilo, nada é exatamente de graça. Então essas alternativas não são as melhores se você quiser criar algo escalável e seguro.

Depois de virar uma madrugada ajeitando parte dos meus projetos anteriores e de ir dormir, aqui me encontro precisando urgentemente postar meus conteúdos nas outras redes, como TabNews e dev.to. Apesar de tudo isso, eu sinto que acabei tendo alguns Feedbacks sobre meu trabalho em si. Talvez não seja uma boa ideia eu colocar a Artificial Lake como interface principal de todos os meus projetos. Isso envolveria um processo gigante de refatoração, além de que os meus projetos perderiam completamente a sua autenticidade. Outro insight que eu tive foi justamente sobre alguns projetos meus que precisam de uma dedicação maior para poder estar online, e sim, eu vou fazer isso. Talvez não agora, mas a minha ideia vai ser colocar todos os meus projetos finalizados, mesmo que não sejam relevantes, e eu ir removendo conforme eu vá desenvolvendo projetos mais relevantes. Embora também seja uma boa opção manter todos esses meus projetos como histórico.

---
# 3. 25 de julho de 2025


- [ ] Task.me
- [ ] HoyPress
Esses projetos com EJS eu vou usar route handler

Puta que pariu. Dá pra usar o Next apenas como API

Cara eu to sem tankar essa stack: EJS com Next

Uma ideia que eu posso fazer é criar uma rota na minha API de portfólio para Feedbacks de outros projetos

Uma ideia para a tela de projetos é um botão de filtrar por tecnologia(s) e colocar apenas o Ano do projeto numa tag no lado direito ou esquedo superior da página

Colocar um ícone na direita falando sobre a stack