#6. Texto e fontes
 Texto
 •Pode ser desenhado com o elemento <text>
 •Atributos e sub-elementos permitem controle sobre muitos aspectos do texto e caracteres individuais
 •Dimensões, espaçamento, rotação, etc.
 •Pode ser desenhado na vertical, na diagonal, em caminhos arbitrários (associado a um <path>)
 •Assim como ocorre com as figuras, pode-se aplicar cor, filtros, gradientes, padrões, clipping, etc.
 •Amplo suporte para acessibilidade e internacionalização
 •Especificação
 •http://www.w3.org/TR/SVG/text.html

 Baseline
 •As coordenadas iniciais de um elemento de texto não ficam no canto superior esquerdo como as figuras
 •A posição exata depende de fatores culturais (idioma), da natureza do texto (alfabético, matemático, etc.)
 •Âncora default tem origem na linha base (baseline) para textos latinos alfabéticos
 •Tanto o retângulo abaixo como o texto têm as mesmas coordenadas x,y



 Fontes

 •Associadas a texto através de atributos de estilo em <text> ou elementos mais altos na hierarquia (ex: <g>)
 •Podem ser aplicados via XML ou CSS
 •São identificadas pelo nome
 •O atributo font-family permite especificar uma lista de nomes: caso o primeiro não seja encontrado, será usado o segundo, e assim por diante
 •Há nomes default como sans-serif, serif, monospace
 •Há vários atributos para controlar aspectos de fontes, como peso, inclinação, tamanho, etc
 •Mesmas propriedades do CSS 2 e mesma sintaxe
 •Na ausência de uma fonte, o texto é desenhado em uma fonte default, como serif

 Atributos de estilo para fontes

 Podem ser especificados tanto
 em XML (como atributos próprios) como
 em CSS (dentro de folhas de estilo,
 blocos <style> ou atributos style)

 Fontes embutidas e SVG Fonts
 •Fontes do sistema não podem ser embutidas em SVG
 •Mas é possível definir fontes em SVG, que podem ser referenciadas por arquivos CSS ou SVG
 •Elemento <font> permite a definição de bibliotecas inteiras de fontes usando SVG, referenciáveis via ID por CSS
 •Dentro de <font> são definidos
 •Características da fonte como família, altura, linha-base, etc: <font-face>
 •Identificadores para a fonte (<font-face-src>, <font-face-Uri>, etc.)
 •Glifos* <glyph> individuais de cada caractere são desenhados dentro deste elemento usando sintaxe de <path>
 •Atributos de <glyph> permitem especificar para cada glifo códigos Unicode, identificadores, códigos de idioma, métricas, ligaduras, etc.
 •Detalhes da criação e manipulação de SVG Fonts foge ao escopo deste curso. Para mais detalhes consulte a especificação em:
 •http://www.w3.org/TR/SVG/fonts.html

 Exemplo de definição de fontes (W3C)
 svg width="400px" height="300px" version="1.1" xmlns = 'http://www.w3.org/2000/svg'>
    <defs>
      <font id="Font1" horiz-adv-x="1000">
             <font-face font-family="Super Sans" font-weight="bold" font-style="normal"
                 units-per-em="1000" cap-height="600" x-height="400" ascent="700"
                 descent="300" alphabetic="0" mathematical="350" ideographic="400" hanging="500">
                 <font-face-src>
                     <font-face-name name="Super Sans Bold"/>
                 </font-face-src>
             </font-face>
             <missing-glyph><path d="M0,0h200v200h-200z"/></missing-glyph>
             <glyph unicode="!" horiz-adv-x="300"><path d="..."/></glyph>
             <glyph unicode="@"><path d="..."/></glyph>
             ...
      </font>
 <font id="Font2" horiz-adv-x="1000">
       <font-face font-family="Super Sans" font-weight="normal" font-style="italic" ...>
            <font-face-src>
                <font-face-name name="Super Sans Italic"/>
            </font-face-src>
        </font-face>
        <missing-glyph><path d="M0,0h200v200h-200z"/></missing-glyph>
        <glyph unicode="!" horiz-adv-x="300"><path d="..."/></glyph>
        <glyph unicode="@"><path d="..."/></glyph>
           ...
      </font>
    </defs>
 </svg>

 Como usar uma fonte SVG
 •Uma vez definida a fonte, ela deve ser referenciada via CSS
 @font-face {
      font-family: 'Super Sans';
      font-weight: normal;
      font-style: italic;
      src: url("myfont.svg#Font2") format("svg")
  }
  @font-face {
      font-family: 'Super Sans';
      font-weight: bold;
      font-style: normal;
      src: url("myfont.svg#Font1") format("svg")
  }

 •Depois, qualquer elemento SVG pode usá-la
 <text x="100" y="100"
       style="font-family: 'Super Sans';
              font-weight: normal;
              font-style: italic">Texto usando uma SVG Font</text>

 Como gerar SVG Fonts
 •Criar uma família de fontes usando SVG Fonts requer muito trabalho
 •Se você tem fontes true-type, pode convertê-las para SVG através do framework Apache Batik (http://xmlgraphics.apache.org/batik)
 •O Batik também fornece uma ferramenta de linha de comando: batik-ttf2svg que pode ser chamada por quaisquer aplicações
 •Exemplo de uso
 •O exemplo abaixo gera um arquivo contendo fontes SVG para os caracteres `0` (Unicode 0048) a `9` (Unicode 0057) em uma fonte SVG
    java 	-jar batik-ttf2svg.jar /fontes/Corbel.ttf  \
    	-l 48 -h 57 –id ncorbel -o NumCorbel.svg
 •A fonte deve ser referenciada via CSS
 	<style>
    @font-face {font-family: 'Corbel';
                src: url("NumCorbel.svg#ncorbel") format("svg")
 </style>
 •E depois pode ser usada normalmente em qualquer elemento:
 	<text font-family="Corbel" ... />

 Atributos de <text>
 •x e y representam coordenadas absolutas
 •Podem conter um ou mais valores
 •Primeiros n valores são posições dos n primeiros caracteres. Ex:
 •<text x="0 5 10" y="0">OLÁ</text> desenha O na posição 0, L na posição 5 e Á na posição 10
 •Os atributos dx e dy representam coordenadas relativas
 •Deslocam o caractere (ou os primeiros n caracteres, se houver n valores) em relação à posição anterior do texto
 •rotate gira o primeiro caractere
 •Ou primeiros n caracteres se houver n valores
 •textLength determina o comprimento do texto
 •O texto é ajustado para caber no espaço
 •lengthAdjust="spacing | spacingAndGlyphs"
 •Define a forma como textLength ajusta o texto para caber no comprimento (variando espaço ou esticando a fonte)

 <tspan>

 •<tspan> é um bloco interno ao texto que permite alterar propriedades de um trecho do texto
 •Coordenadas
 •Estilo
 •etc.
 •Os atributos principais de <tspan> são os mesmos de <text>
 •Mas cada <tspan> está no contexto de um <text> pai.
 •SVG não possui recursos para automaticamente quebrar linhas (não há blocos de parágrafo)
 •Cada elemento <text> desenha uma única linha de texto.
 •Mas com <tspan> é possível construir blocos <text> multilinha com cada linha definida em um <tspan>.

 Exemplos com <tspan> e dx/dy

 •Nos exemplos abaixo, o deslocamento horizontal relativo é mantido
 •Incrementos com atributo dy, que leva em conta o valor anterior
 •Os dois arquivos produzem o mesmo resultado

 <svg xmlns="http://www.w3.org/2000/svg" ... viewBox="0 0 200 200">
     <text font-size="12" x="5" y="15">
         <tspan dx="0" dy="0">Um</tspan>
         <tspan dy="15">Dois</tspan>
         <tspan dy="15">Tres</tspan>
         <tspan dy="15">Quatro</tspan>
         <tspan dy="15">Cinco</tspan>
         <tspan x="5" dy="0">Um</tspan>
         <tspan dy="-15">Dois</tspan>
         <tspan dy="-15">Tres</tspan>
         <tspan dy="-15">Quatro</tspan>
         <tspan dy="-15">Cinco</tspan>
     </text>
 </svg>

 <svg xmlns="http://www.w3.org/2000/svg" ... viewBox="0 0 200 200">
   <text font-size="12" x="5" y="15">
     <tspan dx="0" dy="0 0 0  15 0 0 0 0  15 0 0 0 0  15 0 0 0 0 0 0  15 0 0 0 0">
            Um Dois Tres Quatro Cinco</tspan>
     <tspan x="5"  dy="0 0 0 -15 0 0 0 0 -15 0 0 0 0 -15 0 0 0 0 0 0 -15 0 0 0 0">
            Um Dois Tres Quatro Cinco</tspan>
     </text>
 </svg>



 Exemplos com rotate (W3C)




 Exemplos <text> e <tspan> (W3C)


 Atributos de estilo (CSS ou XML)
 •text-decoration="underline | overline | line-through | ..."
 •Texto sublinhado, sobrelinhado, riscado
 •letter-spacing="normal | valor| inherit"
 •E s p a ç o   e n t r e   l e t r a s
 •word-spacing="normal | valor| inherit"
 •Espaço        entre         palavras
 •kerning="auto | comprimento | inherit"
 •Espaçamento especial entre caracteres
 •Modo auto é default e automaticamente reduz o espaçamento entre caracteres específicos (ex: "VA")

 Atributos de alinhamento
 •text-anchor="start | middle | end"
 •Alinhamento do texto (onde ele é ancorado)
 •Posição depende do idioma, cultura, etc.
 •Para alfabeto latino start = esquerda, end = direita
 •baseline-shift="baseline | sub | super | n% | valor | ..."
 •Desvio relativo vertical em relação à linha base
 •Permite efeitos subescrito, sobrescrito, etc.
 •dominant-baseline="auto | ideographic | ..."
 •Linha base principal do texto
 •alignment-baseline="auto | ideographic | ..."
 •Linhas base secundárias (relativas à linha base principal)

 Suporte de atributos de estilo


 Alinhamento horizontal: text-anchor

 <svg xmlns="http://www.w3.org/2000/svg" width="600" height="300">
  <g transform="translate(300,50)" >
   <g id="grid" stroke="blue" ... stroke-dasharray="10 10">
      <line x1="0" y1="-25" x2="0" y2="150"  />
      <line x1="-300" y1="0"   x2="300" y2="0" />
      <line x1="-300" y1="60" x2="300" y2="60" />
      <line x1="-300" y1="120" x2="300" y2="120" />
   </g>
   <text font-family="monospace" font-size="24">
     <tspan x="0" y="0"  text-anchor="start">Pelo inicio (START)</tspan>
     <tspan x="0" dy="60" text-anchor="middle">Pelo meio (MIDDLE)</tspan>
     <tspan x="0" dy="60" text-anchor="end">Pelo final (FIM)</tspan>
   </text>
  </g>
 </svg>



 Alinhamento vertical: baseline

 •Resultado diferente webkit e mozilla
 •Apenas hanging e auto são confiáveis
 •Outros browsers: apenas auto funciona

 <g transform="translate(50,50)" ... >
   <line x1="0" y1="0"   x2="300" y2="0" />
   <line x1="0" y1="100" x2="300" y2="100" />
   <line x1="0" y1="200" x2="300" y2="200" />
   <line x1="0" y1="300" x2="300" y2="300" />
 </g>
 <g transform="translate(50,50)" text-anchor="start"
    font-family="monospace" font-size="24"
    font-weight="bold">
    <text x="0" y="0"
      dominant-baseline="ideographic">ideographic
                                      baseline</text>
    <text x="0" y="100"
       dominant-baseline="auto">auto baseline</text>
    <text x="0" y="200"
       dominant-baseline="mathematical">mathematical
                                        baseline</text>
    <text x="0" y="300"
       dominant-baseline="hanging">hanging baseline</text>
 </g>



 <tref>
 •Elementos <text> podem ser referenciados e reusados como qualquer outro objeto SVG através de <use>
 •Para segmentos de texto contidos no interior de blocos <text>, pode-se usar o elemento <tref>
 •Referencia apenas o conteúdo do texto (não preserva atributos de estilo ou posição)

 <svg viewBox="0 0 600 600" ... >

   <defs>
     <text id="svg">Scalable
           Vector Graphics</text>
   </defs>

   <text x="50" font-weight="bold" font-style="italic" y="100" font-size="12pt"
                lengthAdjust="spacingAndGlyphs" font-family="arial">
     <tspan textLength="250" x="100">Os arquivos foram criados com</tspan>
     <tspan textLength="300" dy="30" x="50"><tref xlink:href="#svg"/> 1.1</tspan>
     <tspan textLength="300" dy="30" x="50">e as animacoes geradas com </tspan>
     <tspan textLength="300" dy="30" x="50"><tref xlink:href="#svg"/> 1.2 Tiny.</tspan>
   </text>
 </svg>



 <textPath>
 •Texto pode ser desenhado na forma de um caminho curvo
 •Elemento <textPath> referencia um <path> que servirá de linha base para o texto
 •Atributo startOffset = percentagem %
 •Indica a posição, especificada como uma percentagem do comprimento total do caminho, onde o texto começa
 •method="align | stretch" (default = align)
 •Se o texto deve ser esticado para seguir o caminho ou alinhado pela tangente (default)
 •spacing="auto|exact"
 •Define a forma como os caracteres são calculados sobre o caminho (auto é default)

 Exemplos (W3C)


 Texto girando em caminho circular

 <defs>
    <path d="M100,200
             C100,100 250,100 250,200
             S100,300 100,200"
          id="circulo" stroke="red"
          stroke-width="1"
          fill-opacity="0">
    </path>
 </defs>
 ...
 <use xlink:href="#circulo" stroke-dasharray="5 5" />

 <text font-size="15" x="100" dy="-10" id="texto"
       font-family="monospace">
    <animateTransform attributeName="transform" type="rotate"
                      from="0,175,200" to="360,175,200"
                      repeatCount="indefinite" fill="freeze" dur="7s"/>
    <textPath xlink:href="#circulo">
 	palavras que giram confundem as letras
    </textPath>
 </text>


 Outros atributos
 •Outros atributos e propriedades de <text> são relacionados à internacionalização
 •direction="ltr | rtl" (left-to-right e right-to-left) indica a direção do texto; idiomas como árabe e hebraico lêem da direita para a esquerda
 •writing-mode="lr-tb | rl-tb | etc." (lr = right-left, tb = top-bottom) permite escrever em várias direções (como ideogramas orientais)
 •unicode-bidi="..." define forma de suporte à texto bidirecional (use com xml:lang e atributos de internacionalização http://www.w3.org/TR/xml-i18n-bp/)
