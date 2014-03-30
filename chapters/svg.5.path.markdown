#5. Caminhos
 •Caminhos representam o contorno de uma figura
 •São definidos por seqüências de comandos (representados por letras) e coordenadas (pares X,Y). Ex: M 50,50 L 120,120 z
 •Cada comando representa o movimento de um ponto a outro.
 •Letras maiúsculas representam coordenadas absolutas
 •Letras minúsculas são coordenadas relativas
 •Os movimentos podem ser de quatro tipos:
 •moveto: define um ponto inicial (ponto corrente) ou move até outro ponto sem desenhar (M, m)
 •lineto: desenha uma linha reta até outro ponto (L, l, H, h, V, v)
 •curveto: desenha uma curva a um novo ponto, que pode ser
 •Bézier cúbica com dois pontos tangenciais (C, c, S, s)
 •Bézier quadrática com um ponto tangencial (Q, q, T, t)
 •Arco elíptico ou circular (A, a)
 •closepath: fecha a figura (Z, z)

 Por que usar caminhos
 •Caminhos (paths) são a forma ideal para gerar SVG através de software
 •São compactos e eficientes (herança do VML)
 •São mais difíceis de validar (não são XML) e de codificar manualmente
 •Podem desenhar todas as figuras (círculos, elipses, retângulos, etc.)
 •O ideal é gerar caminhos, e não escrevê-los
 •Ao codificar SVG à mão, use as figuras básicas, se possível
 •Como criar caminhos?
 <path d="descrição do caminho" atributos-do-caminho />
 •Exemplo:
 	<path d="M 100,100 L 300,100 L 200,300 z"
       stroke="red" fill="blue" strike-width="2" />

 Exemplo de um caminho
 <?xml version="1.0" standalone="no"?>

 <!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
   "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

 <svg width="4cm" height="4cm" viewBox="0 0 400 400"
     xmlns="http://www.w3.org/2000/svg" version="1.1">
     <title>Example triangle01- simple example of a 'path'</title>
     <desc>A path that draws a triangle</desc>
     <rect x="1" y="1" width="398" height="398"
         fill="none" stroke="blue" />
     <path d="M 100 100 L 300 100 L 200 300 z"
         fill="red" stroke="blue" stroke-width="3" />
 </svg>


 Deslocamento moveto

 •Comandos M ou m estabelecem novo ponto corrente
 •Move a caneta sem desenhar
 •Se for o primeiro ponto do caminho, M (absoluto) será igual a m (relativo ao ponto 0,0)
 •Cada moveto representa o início de um subcaminho
 •Exemplo (trechos de caminhos)
 •M 100,100 m 50,-20
 •Move de 0,0 para 100,100 e depois para 150,80
 •M100 100m50 -20
 •Mesma coisa (vírgulas e espaços irrelevantes são opcionais)
 •M100 100 150 80
 •Mesma coisa (comandos não precisam ser repetidos se movimento for do mesmo tipo)

 Comando closepath
 •Comandos Z ou z fecham um subcaminho
 •Causam o desenho de uma linha reta do ponto corrente até o ponto inicial do subcaminho
 •Se o comando seguinte for um moveto, um novo subcaminho será iniciado
 •Se o comando seguinte for qualquer outro, o ponto inicial será o mesmo do subcaminho corrente
 •Valor do atributo stroke-linejoin é usado para fechar a curva
 •Exemplos
 •M200 200L250 250Z M100 100L150 150z L200 300z
 •O caminho acima tem três subcaminhos
 •O terceiro caminho começa em 100,100
 •Tanto faz usar Z como z já que eles não têm parâmetros

 Deslocamento lineto
 •Comandos L, H, V e l, h e v desenham linhas retas
 •H ou h recebe uma ou mais coordenadas x e desenha linhas retas horizontais
 •V ou v recebe uma ou mais coordenadas y e desenha linhas retas verticais
 •L ou l recebe um ou mais pares de coordenadas x,y e desenha linhas retas em qualquer direção
 •Exemplos
 •M100,100L150,200z
 •M100,100L150,200h50z
 •M100,100L150,200h50v-100z
 •M100,100L150,200h50v-100l-50,50z
 •M100,100L150,200h50v-100l-50,50L150,50 100,50z



 Curvas (deslocamentos curveto)
 •Há três tipos de curvas
 •Bézier cubico
 •Bézier quadrático
 •Arco
 •Curvas Bézier cúbicas são definidas por três pares de coordenadas
 •Coordenadas x,y de DOIS pontos de controle tangenciais
 •Coordenadas x,y do fim da curva
 •Curvas Bézier quadráticas são definidas por dois pares de coordenadas
 •Coordenadas x,y de UM ponto de controle tangencial
 •Coordenadas x,y do fim da curva
 •Arcos são definidos por
 •Par de raios (rx,ry) do elipse do qual será extraído o arco
 •Ângulo de rotação do eixo x
 •Um par de flags indicando um dos quatro possíveis arcos possíveis
 •Coordenadas x,y do fim da curva

 Curvas Bézier cúbicas
 •Podem ser expressas de duas formas
 •Curva normal: C ou c com coodenadas x1,y1  x2,y2  x,y onde
 •x,y são as coordenadas do ponto final da curva
 •x1,y1 são as coordenadas do controle tangencial do ponto inicial
 •x2,y2 são as coordenadas do controle tangencial do ponto final
 •Curva suave: Comando S ou s com coordenadas x2,y2  x,y
 •Neste caso, o controle do ponto inicial será simétrico ao controle final da curva anterior, fazendo com que a junção seja suave
 •Exemplos


 Exemplos: Bézier cúbicas


 Curvas Bézier quadráticas
 •Podem ser expressas de duas formas
 •Curva normal: Q ou q com coodenadas x1,y1  x,y onde
 •x,y são as coordenadas do ponto final da curva
 •x1,y1 são as coordenadas do controle tangencial
 •Curva suave: Comando T ou t com coordenadas x,y
 •O controle tangencial será simétrico ao controle da curva anterior, fazendo com que a junção seja suave
 •Exemplo


 Arcos
 •Arcos são obtidos escolhendo dois pontos da borda de um elipse



 •São especificados com o comando A ou a
 •A sintaxe é: 	A rx,ry q lf,sf x,y onde
 •rx e ry são respectivamente o raio horizontal e vertical do elipse
 •q é o ângulo de rotação do eixo x onde está o elipse




 •lf,sf pode ter os valores 0,0 0,1 1,0 ou 1,1 e representam quatro formas de obter o arco (exemplo no próximo slide)
 •x,y são as coordenadas do ponto final

 Exemplos de arcos simples


 Tipos de arco

 •Os arcos são obtidos pela intersecção de dois elipses
 •Quatro diferentes arcos são possíveis
 •O par de flags lf,sf define qual será usado


