#4. Estrutura do documento

 Estrutura de um documento
 •Documentos SVG podem declarar figuras como elementos de primeiro nível logo abaixo do elemento <svg>
 •Há muita repetição: arquivos grandes e ineficientes
 <svg xmlns:xlink="http://www.w3.org/1999/xlink"
      xmlns="http://www.w3.org/2000/svg" width="1050" height="600" viewBox="0 0 1050 600">

     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)"  transform="translate(40)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(60)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)"  transform="translate(80)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(100)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)"  transform="translate(120)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(140)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)"  transform="translate(160)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" transform="translate(20,20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(40,20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" transform="translate(60,20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(80,20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" transform="translate(100,20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(120,20)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" transform="translate(140, 20)" />
      ...
     <rect x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" transform="translate(140,140)" />
     <rect x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" transform="translate(160,140)" />
 </svg>

 •Ideal é reusar componentes: + eficiente, + fácil de manter/gerar
 •SVG sugere uma estrutura para organizar o documento


 66 linhas
 ~3500 chars

 Elementos estruturais

 Documento estruturado
 <svg xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg"
            width="1050" height="600" viewBox="0 0 1050 600">
     <defs>
         <rect id="preto"  x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" />
         <rect id="branco" x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" />

         <g id="quatroCasas">
             <use xlink:href="#preto" />
             <use xlink:href="#branco" transform="translate(20)"/>
             <use xlink:href="#branco" transform="translate(0,20)"/>
             <use xlink:href="#preto"  transform="translate(20,20)"/>
         </g>

         <g id="fileiraDupla">
             <use xlink:href="#quatroCasas" />
             <use xlink:href="#quatroCasas" transform="translate(40)" />
             <use xlink:href="#quatroCasas" transform="translate(80)" />
             <use xlink:href="#quatroCasas" transform="translate(120)" />
         </g>

         <g id="tabuleiro">
             <use xlink:href="#fileiraDupla" />
             <use xlink:href="#fileiraDupla" transform="translate(0,40)" />
             <use xlink:href="#fileiraDupla" transform="translate(0,80)" />
             <use xlink:href="#fileiraDupla" transform="translate(0,120)" />
         </g>
     </defs>
     <use xlink:href="#tabuleiro" />
 </svg>

 28 linhas
 ~1400 chars



 id e <use>
 •<use> acessam outro elemento SVG por referência
 •Elementos que serão referenciados devem ter um id
 •O elemento referenciado pode estar no mesmo arquivo ou em outro, local ou remoto
 •<use> não muda atributos do elemento referenciado
 •Sintaxe
 <use xlink:href="uri"
      x="coordinate"
      y="coordinate"
      width="length"
      height="length"
      style-attribute="..." (atribs fill, stroke, etc.)
 >
 •URI local
 •xlink:href="#name"
 •URI externa
 •xlink:href="../struct/Use01.svg/#name"

 Definições <defs>
 •Se você deseja reusar um recurso SVG, coloque em seção <defs>
 •O bloco <defs> armazena definições
 •Elementos declarados em <defs> não serão desenhados (para desenhá-lo, é preciso referenciá-lo com <use>
 •Use <defs> para guardar objetos que serão reusados com freqüência
 •Ao reusar um objeto, pode-se mudar seu estilo e coordenadas
 •Exemplo:

 <svg ...>
   <defs>
     <rect id="preto" x="0" y="0" width="20" height="20" fill="rgb(64,32,32)" />
     <rect id="branco" x="0" y="0" width="20" height="20" fill="rgb(255,225,200)" />
   </defs>

   <use xlink:href="#preto" />
   <use xlink:href="#branco" transform="translate(20)"/>
   <use xlink:href="#branco" transform="translate(0,20)"/>
   <use xlink:href="#preto"  transform="translate(20,20)"/>

 </svg>



 Grupos <g>
 •Grupos permitem tratar um conjunto de objetos como um só
 •O grupo comporta-se como um objeto único
 •Elementos contidos no grupo herdam estilos e atributos comuns
 •Podem conter outros grupos
 •Sintaxe
 <g id="nome"
    atributos de estilo
    transform="comandos de transformação">
   <!– conteudo do grupo -->
 </g>

 <svg ...>
   <defs>
     ...
     <g id="quatroCasas" transform="translate(10,10)">
       <use xlink:href="#preto" />
       <use xlink:href="#branco" transform="translate(20)"/>
       <use xlink:href="#branco" transform="translate(0,20)"/>
       <use xlink:href="#preto"  transform="translate(20,20)"/>
     </g>
   </defs>
   <use xlink:href="#quatroCasas" />
 </svg>



 <title> e <desc>
 •<title> e <desc> são elementos usados para documentar um SVG
 •Podem ser usados em qualquer elemento
 •O visualizador não precisa mostrá-los
 •Geralmente <title> aparece como tooltip*; o mesmo pode acontecer com <desc>

 <g id="tabuleiro">
 	<title>Isto eh um tabuleiro</title>
 	<desc>O tabuleiro é construido da seguinte ...</desc>
     <use xlink:href="#fileiraDupla" />
     <use xlink:href="#fileiraDupla" transform="translate(0,40)" />
     <use xlink:href="#fileiraDupla" transform="translate(0,80)" />
     <use xlink:href="#fileiraDupla" transform="translate(0,120)" />
 </g>

 Símbolos <symbol>
 •Um <symbol> é uma figura definida pelo usuário
 •Use para criar figuras complexas que serão reusadas, redimensionadas e reposicionadas
 •Símbolos podem conter figuras, outros símbolos, grupos
 •É um elemento estrutural
 •Mais importante pelo que representa do que pelo que faz
 •Você também pode criar figuras com <g> (mas <g> deve ser usado para agrupar objetos)
 •Símbolos não são desenhados automaticamente (como acontece com um grupo, se estiver fora de um <defs>): é preciso referenciá-los (ex: via <use>)
 •Símbolos podem ter um viewBox
 •A figura é geralmente desenhada dentro de um viewBox

 S[imbolos




 Marcadores <marker>

 •Um marcador é um símbolo que pode ser concatenado a vértices de caminhos, linhas, polígonos e polilinhas
 •Geralmente usados para fazer pontas de setas ou similares
 •Para criar
 •Defina um <marker> da mesma forma que um <symbol>
 •Use atributos refX e refY para marcar o ponto de conexão
 •Defina a orientação com orient (se for seta use auto)
 •Se markerUnits for userSpaceOnUse, use markerHeight e markerWidth para determinar as dimensões fixas do marcador
 •Se markerUnits for strokeWidth, o tamanho será proporcional à espessura da linha
 •Para usar
 •<path>, <line>, <polyline> ou <polygon> têm atributos marker-end, marker-start ou marker-mid

 Marcadores



 Marcadores e símbolos



 Transparência e visibilidade

 •Há três formas de variar a visibilidade de um objeto em SVG
 •Atributo opacity: mais abrangente que fill-opacity e stroke-opacity – se aplicado a um grupo, afeta todos os objetos; com opacity="0" todo o grupo fica invisível
 •Atributo visibility: pode ser visible ou hidden; se hidden o objeto fica invisível
 •Atributo display="none": não apenas torna o objeto invisível, como remove-o da árvore (não é possível capturar eventos)
 •A visibilidade pode ser controlada dinamicamente através de scripts
 •Todas as propriedades podem ser manipuladas via DOM (com JavaScript) e animações
 •Símbolos, e quaisquer definições de grupos ou elementos em <defs> não existem (e são, portanto, invisíveis) enquanto não forem refereciados com <use>

 Links

 •SVG permite links internos e externos através de IRIs (Internationalized Resource Identifier*)
 •Referêcias locais podem ser especificadas diretamente em atributos do XLink xlink:href
 •#referencia
 •Em atributos dos elementos SVG é preciso chamar a referência através de uma função IRI
 •url(#referencia)
 •Referências também podem ser feitas a arquivos externos
 •http://w.com/outro.svg#referencia
 •url(http://w.com/outro.svg#referencia)
 •Elementos <a> permitem lincar para fora do SVG
 •<a xlink:href="http://www.site.com/a.html"> <rect...> </a>
