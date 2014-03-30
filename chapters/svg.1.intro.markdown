#1. Introdução

##O que é SVG
•Scalable Vector Graphics
•Gráfico
•linhas, poligonos, figuras, texto, filtros, efeitos
•Escalável
•Zoom eficiente e rápido
•Pode ampliar e reduzir sem perder qualidade
•Vetorial
•Armazena a equação dos gráficos (e não um mapa de pixels como imagens bitmap)
•Imagens maiores ocupam mesmo espaço que imagens menores, e não perdem qualidade
•Pode tratar gráficos separadamente (como objeto), permitindo animações

Vetores e bitmaps


SVG é XML
•Tudo expresso em XML
•Pode ser alterado em editor de textos
•Pode ser processado como texto
•Pode ser transformado via XSLT
•Pode ter objetos selecionados via XPath
•Pode ser validado com XML Schema
•Pode ter a aparência de objetos alteradas com CSS
•Pode ter comportamento de objetos alterado com JavaScript e DOM
•Pode ser embutido em HTML como texto
•Qualquer elemento pode ser animado

SVG é um formato gráfico

•Desenhos podem ser produzidos em ferramentas gráficas populares
•Corel Draw
•Adobe Illustrator
•OpenOffice
•Formato aberto e multiplataforma
•Pode-se criar um SVG no Illustrator e fazer alterações em um editor de texto e vice-versa
•Pode-se desenhar partes de um SVG no Corel Draw, e usar XSLT para gerar gráficos maiores usando as partes como componentes básicos

Tecnologias similares

•Flash / Flex
•Solução + popular de gráficos vetoriais e animação 2D na Web
•Proprietária
•Perdendo espaço para tecnologias emergentes como SVG
•HTML5 Canvas
•Linguagem gráfica 2D baseada em JavaScript, embutida em HTML com recursos similares a SVG
•É possível interagir com SVG via HTML DOM
•WebGL
•Linguagem gráfica 3D em HTML 5 Canvas com sintaxe do OpenGL ES
•Outros formatos de gráfico vetorial (obsoletos, em extinção, proprietários, incompatíveis com a Web, etc.)
•VML, PGML, WebCGM, EPS, AI, DWG, CGM, WMF, etc.

##Origens e suporte do SVG

•SVG foi criado em 1998 a partir de propostas enviadas à W3C para a padronização de linguagem vetorial para a Web
•Especificação final 1.0 publicado em 2001
•Especificação 1.1, 2a. ed, 2010: http://w3.org/Graphics/SVG
•As principais influências do SVG são
•VML da Microsoft (com HP, Autodesk e Macromedia)
•PGML, da Adobe (com IBM, Netscape e Sun)
•CSS e HTML (W3C)
•Primeira especificação escrita por Jon Ferraiolo (Adobe)
•A Adobe foi a empresa que mais investiu no SVG nos primeiros anos
•Produziu o viewer mais popular  (Adobe SVG Viewer)
•Introduziu suporte nativo no Adobe Illustrator.

Mercado

•Mercado crescente
•Muitas aplicações populares e plataformas suportam, produzem ou exportam SVG desde as primeiras versões
•Exemplos: Adobe Illustrator, Corel Draw, OpenOffice.org, Blender, GIMP, Nokia S60, ...
•Google indexa conteúdo SVG desde agosto de 2010.
•Suporte nativo SVG em browsers (StatCounter):
•Internet Explorer (46% mercadoê): SVG 1.1 a partir do IE 9.0
•Firefox (30%ê): SVG 1.1 desde 2005 (parcial)
•Webkit: Chrome e Safari (18%é): SVG 1.1 desde 2006 (parcial)
•Opera (2%çè) SVG 1.1 desde versão 8.0, completo desde 10.0
•Mobile* (4%é): SVG 1.1/SVG 1.2 Tiny
	* vários fabricantes, geralmente Webkit (Android, Palm, Symbian, Safari)

Plataformas SVG
•SVG Full
•SVG 1.0 e SVG 1.1 – quase iguais no que se refere à componentes e sintaxe (em 1.1, o DTD é modular)
•Formato SVGZ (SVG comprimido com ZIP)
•SVG Mobile
•SVG 1.2 Tiny (SVGT) e SVG Basic (SVGB): destinados a dispositivos móveis, tablets, etc.
•A 3GPP adotou SVG Tiny como padrão de mídia vetorial
•Em desenvolvimento
•SVG 2.0 (antes chamado de SVG 1.2) – tem recursos de transformação 3D
•SVG Print (Canon, HP, Adobe e Corel) – impressão

Suporte SVG 1.1
•Para testar, executar e exibir os exemplos demonstrados neste curso foram usados os seguintes browsers e plataformas
•Plataforma Mac OS X (10.6) e Linux (Ubuntu)
•Google Chrome 10.0 (Webkit)
•Safari 4.04 e 5.03 (Webkit)
•Firefox 4 (Beta) (Mozilla)
•Opera 10.62 (Presto)
•Plataforma Windows (XP)
•Internet Explorer 8 (Windows XP) com diversos plug-ins JavaScript
•Chrome 10, Opera 10, Firefox 4, Safari 4 (Windows XP)
•Plataforma Windows 7
•Internet Explorer 9
•Ferramentas (multiplataforma – usadas em Mac OS X)
•Squiggle (SVG Viewer do framework Batik)
•SVG Viewer do editor Oxygen XML

Suporte no Windows
•Nenhum suporte nativo: Internet Explorer 6, 7, 8
•IE foi um dos primeiros browsers a ter suporte SVG 1.0 através do Adobe SVG Viewer Plugin (2000, Windows 98/2000/XP)
•Mas Microsoft nunca investiu no suporte nativo a SVG, e Adobe – proponente da especificação SVG 1.0 –  deixou de dar suporte ao popular plug-in em janeiro de 2009.
•Adobe Plugin ainda funciona em IE 6, 7, 8: parcial e com bugs
•Soluções usando o Internet Explorer
•Usar Internet Explorer 9 (mas só roda em Vista ou Seven)
•Plug-in SVGWeb do Google: http://code.google.com/p/svgweb/
•Outros plug-ins que embutem SVG: http://www.amplesdk.com/
•Usar outros browsers no Windows
•Melhor suporte (12/2010): Opera, Google Chrome, Firefox 4
•Firefox 3.x tem menos suporte (ex: não suporta animação SMIL)

##Como criar SVG

###Como criar um SVG em XML

Como exibir
•Em um browser
•Simplesmente abra o arquivo SVG em um browser

•Em outras aplicações
•Ferramentas gráficas: Inkscape, Sketsa, Illustrator, Corel Draw
•SVG Viewers (Apache Squiggle), interfaces de tablets, celulares, etc.



•Visualizador e editor SVG da Apache (open-source)
•Permite exibir SVG, depurar scripts, analisar código-fonte como árvore, alterar código, etc.

Batik Squiggle


Como vincular em HTML e XHTML
•A forma recomendada é usar <object>
•<object src="svgdemo.svg"
        classid="image/svg+xml"
        type="image/svg+xml"
        height="300" width="400" />
•Outras formas também funcionam (mas não em todos os browsers)
•<img src="svgdemo.svg"
     height="300" width="400" />
•<embed src="svgdemo.svg"
       type="image/svg+xml"
       height="300" width="400" />

Como embutir

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <xsl:template match="figura">
        <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
            <circle r="50" cx="100" cy="100" fill="green"/>
        </svg>
    </xsl:template>
</xsl:stylesheet>
```

```
<catalogo xmlns="http://www.acme.com/Catalogo"
          xmlns:svg="http://www.w3.org/2000/svg">
    <imagem>
        <svg:svg  width="200" height="200">
            <svg:circle r="50" cx="100" cy="100" fill="green"/>
        </svg:svg>
    </imagem>
</catalogo>
```

```
<!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
            <title>Hello SVG!</title>
    </head>
    <body>
        <h1>Hello SVG!</h1>
        <svg>
            <circle r="50" cx="50" cy="50" fill="green"/>
        </svg>
    </body>
</html>
```

Como programar
•Interatividade: para interagir e manipular SVG em tempo de exibição
•Scripting em SVG 1.1 com W3C Document Object Model Level 2 (DOM 2.0)
•Para programar o DOM, pode-se usar qualquer linguagem suportada pelo viewer utilizado
•JavaScript (ECMA Script) é a linguagem mais usada (e única suportada pela maioria dos visualizadores SVG)
•Geração: Para gerar e manipular SVG antes da exibição
•Com Java, pode-se usar o popular framework open-source Apache Batik: http://xmlgraphics.apache.org/batik
•Pode-se gerar SVG através de XSLT com amplo suporte em diversas plataformas e linguagens
•XSL-FO e APIs gráficas também têm opção de gerar SVG


Geração de imagem
•Muitas vezes é necessário converter um SVG em imagem
•Ex: para gerar uma visualização alternativa a browsers que não suportam SVG
•Isto pode ser feito dinamicamente através do framework Batik, em aplicações Web escritas em Java
•Ou executado via linha de comando usando o SVG Rasterizer do Batik
•http://xmlgraphics.apache.org/batik/tools/rasterizer.html
•Exemplo de uso: default é gerar PNG
•O comando abaixo gera arquivo.png
	java -jar batik-rasterizer.jar arquivo.svg
•Mas também é possível gerar outros formatos
•O comando abaixo gera um JPEG
	java -jar batik-rasterizer.jar -m image/jpeg arquivo.svg

Soluções para IE e browsers antigos
•Fornecer uma imagem alternativa quando um browser não suporta SVG é recomendado, mas há perdas:
•Perde-se interatividade e animação
•Zoom perde qualidade
•Imagens geralmente são maiores
•Alguns plug-ins e extensões tentam converter SVG em VML ou Flash, usando JavaScript, para que funcionem em browsers antigos e no Internet Explorer com mais recursos que imagens
•A maioria ainda está em versões alfa ou beta, e não implementam vários recursos
•Mas alguns já conseguem implementar interatividade e animação
•Alternativas mais maduras (em 12-2010)
•SVGWeb (Google Code)
•Ample SDK
•FlashCanvas (converte HTML 5 Canvas em Flash) + canvg (converte SVG em HTML5 Canvas)

SVGWeb
•http://code.google.com/p/svgweb/
•Requer instalação de biblioteca JavaScript e hacks que usam Flash para exibir SVG
•Browser precisa ter plug-in Flash
•Suporte SVG 1.1 ainda limitado (versão alfa – 12/2010)
•Suporta animações SMIL simples e scripting
•Código SVG pode ter que ser adaptado (evitar usar symbol, filter, etc.)
•Se browser suportar SVG, o plug-in é ignorado
•É preciso carregar via HTML (embutir dentro de um bloco <script> ou usar <object> para vincular):

```
<html>
<script src="src/svg.js" data-path="src" />
<body>
  <object src="svgdemo.svg"
                classid="image/svg+xml"
                width="800" height="600"
                id="mySVGObject" />
</body>
```

Precisa carregar biblioteca antes de qualquer outro script!

Ample SDK

•http://www.amplesdk.com/
•Também usa bibliotecas JavaScript
•Mas suporta outros recursos além do SVG, como XUL, HTML 5, etc.
•Suporta scripts rodando dentro do SVG (interatividade e animação)
•Suporta gráficos complexos (porém ainda não suporta alguns elementos – pode-se re-escrever o SVG com apenas elementos suportados)
•É preciso carregar via HTML (embutido ou externo)

```
<!DOCTYPE html>
<html>
    <head>
        <script type="text/javascript" src="ample/runtime-dev.js" />
        <script type="text/javascript" src="ample/languages/svg/svg.js" />
    </head>
    <body>
        <script type="application/ample+xml" src="svgdemo.svg" />
    </body>
</html>
```

FlashCanvas e canvg
•Na verdade são duas bibliotecas
•É preciso usar as duas
•FlashCanvas converte HTML 5 Canvas em Flash
•http://flashcanvas.net/
•canvg converte SVG em HTML 5 Canvas
•http://code.google.com/p/canvg/
•Para usar FlashCanvas apenas importe a biblioteca
<script type="text/javascript" src="flashcanvas.js"/>
•Para usar canvg, crie um <canvas> com um id, e inicialize via uma chamada JavaScript

```
<script type="text/javascript" src="canvg/rgbcolor.js"/>
<script type="text/javascript" src="canvg/canvg.js"/>
<script type="text/javascript">
   function init() {   canvg('tela', 'svgdemo.svg');   }
</script> ...
<body onload="init()">
     <canvas id="tela" width="800" height="600" />
</body>
```

•Experimente
•Testar se seu browser suporta SVG (como? independente, embutido em HTML5?)
•Digitar o SVG mostrado como exemplo, alterá-lo e observar o que acontece
•Exemplos e recursos
•Veja vários exemplos de SVG em exemplos/
•Biblioteca SVGWeb e outras em software/
•Ferramentas Sketsa e Squiggle em software/
•SVG Rasterizer em software/
