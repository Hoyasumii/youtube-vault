- Fala pessoal, beleza?
- Antes de começarmos a nossa saga de algoritmos e estrutura de dados, eu decidi começar por um tópico universal para todos os programadores.
- Algo atemporal, e que talvez você nunca tenha refletido sobre: As Linguagens de Programação.
- Será uma série curta, mas que servirá de fundamento para as próximas séries que nós iremos trabalhar.
- Então vamos começar.
- Vamos começar a entender o que é uma linguagem de programação e vamos entender o porque disso importar.
1. Como os Programas de Computador Funcionam?
	- Os programas que usamos - seja no computador, celular e outros dispositivos eletrônicos - existem para resolver problemas.
	- Entretanto, o computador precisa entender o que fazer. E o problema é: Ele só entende instruções em Linguagem de Máquina.
	- A Linguagem de Máquina é uma linguagem composta por números, geralmente em binário, como os zeros e uns, e serve para dizer ao processador exatamente o que fazer: Calcular, mover dados, acessar a memória, e por aí vai.
	- Mas criar um programa que tenha apenas zeros e uns é algo quase que impossível. Extremamente difícil, além de estar sujeito a muitos erros.
	- E foi aí que surgiu a ideia de criar uma maneira de programar, que fosse feita para humanos, mas entendida por máquinas.
2. O que são as Linguagens de Programação?
	- As linguagens de programação surgiram nas universidades e organizações militares, onde diversos programas estavam sendo criados em linguagem de máquina para resolver problemas reais.
	- Só que criar programas em linguagem de máquina é uma tarefa muito complicada. Afinal, havia uma necessidade urgente por esses programas, mas criá-los em linguagem de máquina consumia muito tempo e dinheiro.
	- E aí nasceram estudos para formalizar uma linguagem que abstraísse esses conceitos de máquina, para uma linguagem facilmente lida por seres humanos.
	- Abstração no caso, significa esconder detalhes complexos e mostrar o que importa. Nesse canal, você vai ouvir falar muito desse termo, então memorize e vamos continuar!
	- E com isso surge o Assembly, a primeira linguagem de programação moderna criada para máquinas. Mas por que moderna? Porque já existiu uma outra linguagem de programação, criada por Ada Lovelace no século 19, mas vamos falar dela num outro vídeo, pois ela merece!
3. O Nascimento do Assembly
	- O Assembly surgiu nos anos de 1940 como uma forma de substituir a programação direta em binário por comandos legíveis, e composta por uma linguagem de palavras-curtar, que representariam essas instruções de linguagem de máquina, de forma abreviada e fácil de entender.
	- Apesar do Assembly ter facilitado o desenvolvimento de software, foi criado uma camada que sucede a criação de um programa, que é a compilação.
	- O processo de Compilar é quase que o oposto de Abstrair, pois ao invés de escondermos os detalhes, iríamos associar esses comandos para a linguagem de máquina, e então seria criado um executável, preparado para rodar em qualquer máquina.
	- O surgimento do Assembly foi um marco para a Ciência da Computação como um todo, pois programas que eram feitos em anos, poderia ter o seu tempo reduzido pela metade, ou até mesmo, em meses, a partir de sua ideação.
	- Por fim, o Assembly permitiu com que novas linguagens surgissem, como o Fortran, o C, e até mesmo, linguagens mais recentes como o Java, e o Python.
4. O Por que de Tantas Linguagens de Programação?
	- Atualmente, temos diversas linguagens de programação no mundo, cada uma com suas características e públicos.
	- Mas entenda uma coisa: embora a solução de um problema possua várias formas de resolver, existem caminhos que facilitam essa solução.
	- E é aí que está o motivo por trás da existência de tantas linguagens: cada uma foi criada para resolver problemas específicos de forma mais eficiente, segura, rápida ou acessível.
	- Nos próximos vídeos, nós vamos falar sobre as características de uma linguagem de programação.
### Características de uma LP
#### Paradigma
- É como se fosse uma abordagem da linguagem para resolver os problemas propostos dela.

1. Declarativo
	1. Paradigma de Programação baseado na descrição de todos os eventos desejados, sem especificar a implementação; Normalmente é usado para linguagens de consulta, como o SQL;
```
SELECT usr.name
FROM user AS usr
INNER JOIN school_report sr 
	ON usr.id = sr.user_id
WHERE sr.student_grade < 6;
```
	
2. Lógico
	1. Paradigma de Programação baseada na lógica matemática, onde os programas são escritos como declarações de fatos e regras, e a computação consiste em provar verdades a partir dessas declarações;
```
	gosta(maria, pizza).
	gosta(maria, chocolate).
	gosta(joao, chocolate).

	amizade(X, Y) :- gosta(X, Z), gosta(Y, Z).
```
		
- Se agora perguntarmos ao sistema se: `?- amizade(maria, joao).`: Ele responderá como verdadeiro.
		
3. Funcional
	1. Paradigma de Programação baseado nos princípios da matemática funcional, em que funções puras e imutabilidade são os pilares centrais.
	2. Alguns dos pontos a se destacar é que nas linguagens funcionais:
		1. Não se usam variáveis globais;
		2. As variáveis são constantes, e caso seja alterada, será criada novas versões dela;
		3. As funções não possuem efeitos colaterais, ou seja, sem logs, mudanças em objetos externos, e por aí vai.
	3. Por fim, uma das suas principais características é a ausencia de laços de repetição, e o uso da recursão para interações.
	4. Exemplo de Linguagem Funcional é Haskell e Elixir
	
4. Imperativo
5. Procedural
6. Orientado a Objetos
7. Multiparadigma
---

1. Nível
	1. Alto Nível
		1. Linguagens Próximas à Linguagem Humana; Fáceis de serem entendidas
	2. Baixo Nível
		1. Linguagens Próximas à Linguagem da Máquina; O seu manuseio tende a ser mais manual do que uma linguagem de Alto nível;

2. Tipagem
	1. Linguagens Fortes e Fracamente Tipadas
	2. Linguagens Dinamicamente e Estaticamente Tipadas
	3. E o TypeScript?
	
3. Gerenciamento de Memória
4. Linguagens Compiladas VS Interpretadas 
5. Como escolher uma Linguagem de Programação?