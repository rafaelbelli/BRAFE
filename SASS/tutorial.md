<h1>=== O QUE É ? ===</h1>

<h3>SASS faz com que o css "se torne" uma linguagem de programação para que fique mais fácil a sua criação, como por exemplo, a adição de variáveis, loops entre outras coisas.<br>
O arquivo sass não é adicionado ao projeto, ele é processado e só assim adicionado ao projeto como um arquivos css comum.</h3>

<h1>=== IMPORT ====</h1>

<h3>Para importar um css dentro de outro css podemos utilizar o código:</h3>

	@import "arquivo.css";

<h3>Ex:</h3>

	@import "arquivo.css";

	body {
		margin: 0;
		padding: 0;
	}</p>


<h3>Para importar um arquivo .scss dentro de outro scss escrevemos</h3>

	@import "arquivo" /*para um arquivo .scss, não é necessário colocar a extensão*/

<h3>Ele irá criar um outro arquivo css de mesmo nome para que os itens sejam importados e haja uma conexão entre os arquivos.

Se você colocar _ antes do nome do arquivo .scss, ele não irá criar outro arquivo scss, mas irá importar o código para
dentro do css alvo.</h3>

<h3>Ex:</h3> 
nome do arquivo:  _arquivo.scss"

modo de importar: 

	@import "arquivo";

<h1>=== variáveis ===</h1>

<h3>As variáveis funcionam quase igual no PHP, a diferença é que invés de "=" você utiliza ":" para criar uma você escreve no arquivo .scss:</h3>

	$variável: valor;

<h3>Ex:</h3>

	$color = #fff;

	div>a {
		color = $color;
	}

<h3>No arquivo .css irá aparecer:</h3>

	div > a {
		color = #fff;
	}


<h1>=== NESTING ===</h1>

<h3>Você pode identar o código da seguinte forma no .scss:</h3>

	$color-bg: yellow;
	$color-font-a: blue;
	$color-font-hover: black;

	div {
		background: $color-bg;
		a {
			text-decoration: none;
			color: color-font-a;
			&:hover{
				color: $color-font-hover;
			}
		}	
	}

<h3>No arquivo .css irá aparecer:</h3>

	div {
		background: yellow;
	}

	div a {
		text-decoration: none;
		color: blue;
	}

	div a:hover {
		color: black;
	}	

<h3>Também é possível usar o nesting em propriedade

Ex:</h3>

	div{
		font{
			size: 1.5em;
			family: Georgia;
		}
	}
	
<h3>No .CSS irá aparecer da seguinte forma:</h3>

	div font{
		size: 1.5em;
		family: Georgia;
	}
	
<h1>=== Mixins ===</h1>

<h3>Se fossemos criar um código que iriamos repetir muitas vezes se digitado sempre, o correto seria criar um mixin para poupar de digitar muitas linhas sem necessidade.
	
Ex:</h3>

	@mixin title{
		font-size: 4em;
		font-family: monospace;
		font-weight: bold;
		color: red;
	}
	
	.classe1 h1{
	@include title;
	}
	
	.classe2 h1{
	@include title;
	}

<h3> No código .CSS gerado aparecerá assim </h3>

	.classe1 h1{
		font-size: 4em;
		font-family: monospace;
		font-weight: bold;
		color: red;
	}
	
	.classe2 h1{
		font-size: 4em;
		font-family: monospace;
		font-weight: bold;
		color: red;
	}
	
<h2> É possível utilizar argumentos no mixin.</h2>

<h3>Ex:</h3>

	@mixin title($size, $color){
		font-size: $size;
		font-family: monospace;
		font-weight: bold;
		color: $color;
	}
	
	.classe h1{
		@include title(4em, red)
	}
	
<h3> Irá aparecer dessa maneira no .CSS:</h3>

	.classe h1{
		font-size: 4em;
		font-family: monospace;
		font-weight: bold;
		color: red;
	}	

<h2>Usando @content</h2>

<h3>Podemos usar o content para enviar informações ao mixin.
Ex:</h3>

	@mixin mobile{
		@media (max-width: 600px) {
		 @content;
		}
	}
	
	@mixin tablet{
		@media (max-width: 980px) {
		 @content;
		}
	}
	
	.classe h1{
		@include mobile{
			color: blue;
			font-size: 1em;
		}
		@include tablet{
			color: red;
			font-size: 2em;
		}
	}
	
<h3>No .CSS</h3>

	@media (max-width: 600px;) {
		 .classe h1{
		 	color: blue;
			font-size: 1em;
		 }
	}
	
	@media (max-width: 980px;) {
		 .classe h1{
		 	color: red;
			font-size: 2em;
		 }
	}
<h1>=== Extend ===</h1>

	.title{
		background: blue;
		@extend title-color;
	}

	.title-color{
		color: red;
	}
<h3> No .CSS.</h3>

	.title-color, title{
		color: red;
	}
	
<h1>=== Operadores ===</h1>

<h3> Com o Sass é possível fazer contas com as propriedades
Ex:</h3>

	.classe h1{
		font-size: 10px + 20;
	}
	
<h3>No . CSS</h3>

	.classe h1{
		font-size: 30px;
	}
	
<h3>Não precisa digitar o tipo do tamanho do item que está somando, mas também não é possível somar dois tipos de tamanhos diferentes como em e px.</h3>

<h1>=== Estrutura condicional ===</h3>

	@mixin box-shadow($shadow){
		@if $boxshadow == 1 {
			shadow-box: 5px 5px 5px 0 #000
		}
		@if $boxshadow == 2 {
			shadow-box: 10px 10px 10px 0 #333
		}
		@if $boxshadow == 3 {
			shadow-box: 15px 15px 15px 0 #333
		}
	}

	.classe {
	@include box-shadow(1)
	}
	
<h3>No . CSS</h3>

	.classe{
		shadow-box: 5px 5px 5px 0 #000
	}
	
<h1>=== LOOP ===</h1>

<h3>Igual a um loop de outras linguagens, com mudanças na sintaxe

Ex:</h3>

	@for $i from 1 through 6{
		.size-{$i}{
			width: 100px * $i;
		}
	}

<h3> Usamos o @for para iniciar o LOOP, colocamos uma variável para armazenar o contador, e dizer FROM (DE) 1 THROUGH (para) 6 (até a quantidade desejada), colocamos o contador
	na criação da classe para sempre criar uma classe nova a cada passagem e não substituir, e depois usamos o contador para multiplicar o width conforme a classe for aumentando. </h3>
