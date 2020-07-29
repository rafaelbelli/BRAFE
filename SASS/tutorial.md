=== O QUE É ? ===

SASS faz com que o css "se torne" uma linguagem de programação para que fique mais fácil a sua criação, como por exemplo, a adição de variáveis, loops entre outras coisas.
O arquivo sass não é adicionado ao projeto, ele é processado e só assim adicionado ao projeto como um arquivos css comum.

<h1>=== IMPORT ====</h1>

<h3>Para importar um css dentro de outro css podemos utilizar o código:</h3>

	@import "arquivo.css";

<h3>Ex:</h3>

	@import "arquivo.css";

	body {
		margin: 0;
		padding: 0;
	}</p>


<h3>para importar um arquivo .scss dentro de outro scss escrevemos</h3>

	@import "arquivo" /*para um arquivo .scss, não é necessário colocar a extensão*/

<h3>ele irá criar um outro arquivo css de mesmo nome para que os itens sejam importados e haja uma conexão entre os arquivos

se você colocar _ antes do nome do arquivo .scss, ele não irá criar outro arquivo scss, mas irá importar o código para
dentro do css alvo.</h3>

<h3>ex:</h3> 
nome do arquivo:  _arquivo.scss"

modo de importar: 

	@import "arquivo";

<h1>=== variáveis ===</h1>

<h3>As variáveis funcionam quase igual no PHP, a diferença é que invés de "=" você utiliza ":" para criar uma você escreve no arquivo .scss:</h3>

	$variável: valor;

<h3>ex:-</h3>

	$color = #fff;

	div>a {
		color = $color;
	}

<h3>no arquivo .css irá aparecer:</h3>

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

<h3>no arquivo .css irá aparecer:</h3>

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
