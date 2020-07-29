#IMPORT =============================================

Para importar um css dentro de outro css podemos utilizar o código:

@import "arquivo.css";

Ex:

@import "arquivo.css";

body {
	margin: 0;
	padding: 0;
}


para importar um arquivo .scss dentro de outro scss escrevemos

@import "arquivo" /*para um arquivo .scss*/

ele irá criar um outro arquivo css para que os itens sejam importados e haja um conexão entre os itens

se você colocar _ antes do nome do arquivo .scss, ele não irá criar outro arquivo scss, mas irá importar o código para
dentro do css alvo.

ex: @import "_arquivo";

#variáveis ======================================

As variáveis funcionam quase igual no PHP, a diferença é que invés de "=" você utiliza ":"

para criar você escreve no arquivo .scss:

$variável: valor;

ex:-

$color = #fff;

div>a {
	color = $color;
}

no arquivo .css irá aparecer

div > a {
	color = #fff;
}


#NESTING ==========================================

Você pode identar o código da seguinte forma no .scss:

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

no arquivo .css irá aparecer:

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
