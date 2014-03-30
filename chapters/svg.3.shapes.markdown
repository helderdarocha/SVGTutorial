#3. Figuras básicas

 •Figuras vetoriais
 •<rect> – Retângulo
 •<circle> – Círculo
 •<ellipse> – Elipse
 •<line> – Linha reta
 •<polyline> – Linha com múltiplos segmentos
 •<polygon> – Polígono
 •Bitmaps
 •<image> – Imagem PNG ou JPEG

 Retângulo <rect>
 •Atributos
 •x – coordenada esquerda
 •y – coordenada superior
 •width – largura
 •height – altura
 •rx – distância horizontal para cantos arredondados (opcional)
 •ry – distância vertical para cantos arredondados (opcional)

 <rect x="25" y="50" width="90" height="90"
 		stroke="green" fill-opacity="0" stroke-width="1"
 		stroke-dasharray="5 5"/>
 <rect x="50" y="150" width="125" height="125" rx="40" ry="40"
 		stroke="red" fill-opacity="0" stroke-width="5"
 		stroke-opacity="0.5" />
 <rect x="150" y="50" width="150" height="150"
 		stroke="green" fill="blue" fill-opacity="0.2"
 		stroke-width="20" stroke-opacity="0.2" />



 Círculo <circle>
 •Atributos
 •cx – coordenada do centro
 •cy – coordenada do centro
 •r – raio
 •Raio é obrigatório

 <circle cx="250" cy="250" r="200"
 		 fill="rgb(100%,30%,0%)"
 		 stroke="yellow" stroke-width="20"
 		 stroke-opacity="0.5"/>

 <circle cx="350" cy="320" r="120"
 		 fill="yellow" fill-opacity="0.9"
   		 style="fill-opacity: 0.9;
 				stroke-width: 20; stroke: blue;
 				stroke-opacity: 0.3; fill: green" />



 Linha simples <line>
 •Atributos
 •x1 – coordenada x do primeiro ponto
 •y1 – coordenada y do primeiro ponto
 •x2 – coordenada x do segundo ponto
 •y2 – coordenada y do segundo ponto
 •A omissão de um valor é considerado zero.

 <line x1="25" y1="50" x2="190" y2="190"
 	stroke="blue" stroke-width="1" stroke-dasharray="5 5"/>

 <line x1="50" y1="150" x2="125" y2="125"
 	stroke="red" stroke-width="5" stroke-opacity="0.5"/>

 <line x1="150" y1="50" x2="150" y2="150"
 	stroke="green" stroke-width="20" stroke-opacity="0.2" />


 Elipse <ellipse>
 •Atributos
 •cx – coordenada x do centro
 •cy – coordenada y do centro
 •rx – raio horizontal
 •ry – raio vertical

 <svg xmlns="http://www.w3.org/2000/svg"
 	 width="100%" height="100%">
     <ellipse cx="200" cy="100" rx="190" ry="90"
 		fill="yellow" fill-opacity="0.5"  stroke="blue"
 		stroke-width="1" stroke-dasharray="5 5"/>
     <ellipse cx="250" cy="150" rx="75" ry="125"
 		fill="red" fill-opacity="0.2"  stroke="red"
 		stroke-width="5" stroke-opacity="0.5"/>
     <ellipse cx="300" cy="200" rx="40" ry="150"
 		fill="black" fill-opacity="0" stroke="green"
 		stroke-width="20" stroke-opacity="0.2" />
 </svg>



 Linha irregular <polyline>
 •Atributos
 •points – uma lista de
 coordenadas com os pontos
 da linha

 <polyline points="150,150
 					50,150
 					100,20
 					150,50
 					200,200
 					50,200
 					20,154
 					48,82
 					32,20" fill="yellow" fill-opacity="0.2"
 							stroke="red" stroke-width="10"/>


 Polígono <polygon>
 •Semelhante a polyline, mas é sempre uma figura fechada
 •Atributos
 •points – lista de coordenadas
 com os vértices do polígono

 <polygon points="	150,150     50,250    50,150   100,50
 					200,50     250,100   300,150   350,250
 					250,250"
 		fill="red" fill-opacity="0.2"
 		stroke-opacity="0.5" stroke="navy"
 		stroke-width="10" stroke-linecap="round"
 		stroke-linejoin="round"
 		stroke-dasharray="40 20 5 20"/>


 Imagens

 •O elemento <image> permite inserir uma imagem PNG ou JPEG em um gráfico SVG
 •A imagem inserida pode ser usada em clipping, máscaras, preenchimento, padrões
 •Pode-se girar, alterar a proporção e tamanho, etc.

 <svg width="4in" height="3in" version="1.1"
   xmlns="http://www.w3.org/2000/svg"
   xmlns:xlink="http://www.w3.org/1999/xlink">

   <image x="200" y="200" width="100px" height="100px"
     xlink:href="imagem.png">
     <title>Uma imagem</title>
   </image>
 </svg>
