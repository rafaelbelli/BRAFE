#IMPORT =============================================

Para importar um css dentro de outro css podemos utilizar o c�digo:

@import "arquivo.css";

Ex:

@import "arquivo.css";

body {
	margin: 0;
	padding: 0;
}


para importar um arquivo .scss dentro de outro scss escrevemos

@import "arquivo" /*para um arquivo .scss*/

ele ir� criar um outro arquivo css para que os itens sejam importados e haja um conex�o entre os itens

se voc� colocar _ antes do nome do arquivo .scss, ele n�o ir� criar outro arquivo scss, mas ir� importar o c�digo para
dentro do css alvo.

ex: @import "_arquivo";

#vari�veis ======================================

As vari�veis funcionam quase igual no PHP, a diferen�a � que inv�s de "=" voc� utiliza ":"

para criar voc� escreve no arquivo .scss:

$vari�vel: valor;

ex:-

$color = #fff;

div>a {
	color = $color;
}

no arquivo .css ir� aparecer

div > a {
	color = #fff;
}


#NESTING ==========================================

Voc� pode identar o c�digo da seguinte forma no .scss:

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

no arquivo .css ir� aparecer:

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
