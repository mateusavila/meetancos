<template>
  <div class="home">
    <div class="container">
      <h1><img src="~assets/img/vue.svg" alt="Vue Js"><strong>Utilizando o lado verde da força</strong><br>Vue.js e o front-end mais próximo do que deveria ser.</h1>
      <h2>Introdução</h2>
      <div class="block">
        <div class="block-text">
          <p>O Vue Js (leia-se VIU, do francês visão) é um framework progressivo, criado inicialmente por Evan You (<a href="https://twitter.com/youyuxi" target="_blank" rel="noopener noreferrer">https://twitter.com/youyuxi</a>), ex-funcionário do Google. Ele comentou em entrevistas, em 2014, que queria criar um framework com as partes boas do AngularJS (Angular 1), algo mais leve, performático e que extenda o poder da HTML. A primeira versão foi lançada em junho de 2013, e o lançamento oficial dele foi no ano seguinte, em 2014.</p>
          <p>O foco deste tutorial é a Vue 2, pois ela estará ativa até janeiro de 2021. As mudanças que teremos para vue 3 serão pequenas, mais afetadas pela inclusão da Composition API e partes do lifecycle com nome atualizado. Este não é um tutorial completo, que apresentará todo o Vue.js para você, e sim algo resumido para um primeiro contato. Muitas funções importantes não estarão presentes aqui, para não ser uma palestra maçante.</p>
        </div>
        <figure>
          <picture>
            <source srcset="~assets/img/evan.avif" type="image/avif">
            <source srcset="~assets/img/evan.webp" type="image/webp">
            <source srcset="~assets/img/evan.jpg" type="image/jpg">
            <img src="~assets/img/evan.jpg" alt="Evan You">
          </picture>
          <figcaption>Evan You. Créditos @github.com</figcaption>
        </figure>
      </div>
      <h2>Bases da Vue.js</h2>
      <p>A Vue Js baseia-se em 3 grandes premissas:</p>
      <div class="list">
        <div class="list-item third">
          <h4>Acessível</h4>
          <p>Você sabe HTML, CSS e Javascript? Não tem necessidade de aprender JSX (apesar do suporte recente de JSX dentro de VUE).</p>
        </div>
        <div class="list-item third">
          <h4>Versátil</h4>
          <p>Você pode usar ele facilmente como CDN dentro de seu tema em WP, passando para gerar SPAs e SSR (com Nuxt, por exemplo) até mesmo em plataformas complexas e escaláveis, como sendo um framework completo.</p>
        </div>
        <div class="list-item third">
          <h4>Performático</h4>
          <p>20KB min+gzip Runtime, Virtual DOM Incrivelmente Rápido, Esforço Mínimo para Otimizações <br> <small>(fonte: https://br.vuejs.org/index.html)</small> </p>
        </div>
      </div>
      <h2>Indicado para iniciantes...</h2>
      <p>Você começou a desenvolver com HTML, CSS recentemente. Viu que o jQuery está sumindo do mercado, e quer apostar em um framework de Javascript para seus projetos, a VUE.js é recomendada por ter uma curva de aprendizagem bem <strong>curta</strong>. Em pouco tempo, olhando na <a href="https://br.vuejs.org/v2/guide/" target="_blank" rel="noopener noreferrer">documentação</a> (uma das melhores do mercado, diga-se de passagem), você pode criar soluções robustas e de qualidade. Não precisa nem de node para rodar uma aplicação em Vue, como é mostrado na imagem abaixo.</p>
      <div class="image-full">
        <picture>
          <source srcset="~assets/img/documentacao-1.avif" type="image/avif">
          <source srcset="~assets/img/documentacao-1.webp" type="image/webp">
          <source srcset="~assets/img/documentacao-1.jpg" type="image/jpg">
          <img src="~assets/img/documentacao-1.jpg" alt="Documentação fácil">
        </picture>
      </div>
      <h2>... robusto para os experientes</h2>
      <p>Para quem desenvolveu puxando os assets de CDN, é uma saudosa lembrança, não? Mas há também a forma mais moderna de desenvolver aplicações usando o vue.cli.</p>
      <pre><code>npm install -g @vue/cli <br><br><span class="comment">#OU</span><br><br>yarn global add @vue/cli<br><br><br><br><span class="comment"># depois de executar o projeto, rode// </span> <br><br>vue create my-project <br><br><span class="comment">#OU</span><br><br>vue ui <span class="comment">// Sim, tem uma versão de UI para tu olhar</span></code></pre>
      <p>Ele atende gostos bem amplos, diferentemente do <span class="react">React</span>, que exige a aprendizagem do JSX para trabalhar com a tecnologia.</p>

      <h2>A instância Vue</h2>
      <p>Toda aplicação Vue é iniciada com a criação de uma nova instância Vue com a função <strong>Vue</strong></p>
      <pre><code>var app = new Vue({<br> <span class="comment">// opçoes</span> <br>})</code></pre>
      <p>Após criar a instância, para ele funcionar corretamente, precisamos setar algumas opções fundamentais, tais como:</p>
      <h4>$el</h4>
      <p>Para executar a Vue, precisamos primeiramente buscar uma div, que será o escopo da aplicação.</p>
      <pre><code>var app = new Vue({<br>  el: '#app'<br>  <span class="comment">// no seu html, precisará ter uma div com a ID app</span><br>})</code></pre>
      <p>Com este código setado, a Vue iniciará os trabalhos! :)</p>
      <h4>data()</h4>
      <p>Aqui instanciamos um objeto com chave: valor contendo todos os dados da aplicação. Uma pequena explicação importante: se você executa vue.js puro, sem ser em ambiente vue.cli ou nuxt (ou qualquer gerador em node), você declara data da forma abaixo:</p>
<pre><code>var app = new Vue({
  el: '#app'
  data: {
    menu: false,
    dados: [], 
    objeto: {
      status: true,
      amount: 10
    }
    <span class="comment">// pode ser qualquer formato de valor</span>
  }
})</code></pre>
      <div class="warning">
        <h4>IMPORTANTE!</h4>
        <p>Se você está em ambiente vue.cli, Nuxt, Quasar, que esteja lidando diretamente com componentes, utilize a sintaxe de funções, para manter o escopo dos dados dentro do próprio componente. Um exemplo está no código abaixo.</p>
      </div>
      <pre><code>export default ({
  data () {
    return {
      menu: false,
      dados: [], 
      objeto: {
        status: true,
        amount: 10
      }
      <span class="comment">// pode ser qualquer formato de valor</span>
    }
  }
})</code></pre>
      <h4>methods</h4>
      <p>Os métodos são as funções que podemos chamar dentro da vue. No exemplo abaixo chamaremos uma função dentro de mounted.</p>
<pre><code>var app = new Vue({
  el: '#app'
  data: {
    menu: false,
    <span class="comment">// pode ser qualquer formato de valor</span>
  },
  methods: {
    toggleMenu () {
      this.menu = !this.menu
    }
  }
})</code></pre>
      <p>Dentro do seu HTML, basta chamar o método e felicidade pura!</p>
<pre><code>{{code1}} <br><span class="comment">&lt;!-- Botei uma expressão dentro do botão que, se caso o valor de menu for true, ele exibe o texto de fechar o menu, caso contrário exibe o texto de abrir o botão. --&gt;</span></code></pre>
      <h4>computed()</h4>
      <p>A computed é uma forma de criar um dado a partir de outros dados, podendo ser filtragem, soma, simplificação de função da VUEX, ou qualquer necessidade. Segundo o link do <a href="https://blog.codecasts.com.br/estados-com-vue-js-data-computed-props-e-store-d8c6da4627ca" target="_blank" rel="noopener noreferrer">codecasts</a>, uma boa forma de usar as <strong>computed properties</strong>:</p>
      <ul>
        <li>Obter o total de uma lista.</li>
        <li>Uma nova lista com dados filtrados a partir de outra lista.</li>
        <li>Criar uma validação simples com base em outros dados.</li>
        <li>Obter um valor que esta muito “longe” dentro de outro objeto.</li>
        <li>Combinar, somar ou diminuir valores.</li>
      </ul>
      <p>Computed é um sistema muito inteligente, ele só executa a função quando solicitado, depois faz um cache do valor, só atualizando caso os dados originais sofram alguma modificação. (Extraído do link: https://blog.codecasts.com.br/estados-com-vue-js-data-computed-props-e-store-d8c6da4627ca)</p>
      <p>Exemplo de utilização:</p>
      <pre><code>var app = new Vue({
  el: '#app'
  data: {
    width: 100,
    height: 200
  },
  computed: {
    size () {
      return number(this.width) * number(this.height)
    }
  }
})</code></pre>
      <p>Este código acima retornaria para o usuário o valor de <strong>size</strong> que faz o calculo entre width e height. </p>
      <h2>HTML Expandido</h2>
      <p>No código acima, implementamos o básico do HTML expandido dentro da Vue. Temos a implementação de um evento click (com a sintaxe @click) e de uma expressão, dentro das chaves duplas. Há outras diretivas interessantes para expandir ainda mais o poder da vue.</p>
      <h4>v-html</h4>
      <p>Insere um html dentro de um bloco.</p>
      <pre><code>&lt;div v-html="html_content"&gt;&lt;/div&gt;</code></pre>
      <div class="warning">
        <h4>IMPORTANTE</h4>
        <p>Não recomendado o uso desta função sem nenhuma forma de sanitizar este dado. A VUE.js não provem, por padrão, de códigos que fazem sanitização de conteúdo.</p>
      </div>
      <h4>v-text</h4>
      <p>Adiciona o texto dentro de um elemento. Pode-se usar a sintaxe v-text, mas a documentação oficial recomenda a utilização da interpolação <strong>{{mustache}}</strong>.</p>
      <h4>v-if, v-else e v-else-if</h4>
      <p>Determina a exibição de um elemento na DOM se ele atender alguma determinada expressão. Exemplo:</p>
      <pre><code>&lt;div v-if="menu"&gt;ESTOU ATIVO!!&lt;/div&gt;</code></pre>
      <p>Se o nosso código que abre o botão lá setar o dado de <strong>menu</strong> para <strong>true</strong>, o texto será exibido. Caso contrário, esta informação não ficará visível na DOM (ao contrário de <strong>v-show</strong>, que exibe na DOM o elemento com o estilo display: block; aplicado). Caso a instrução seja negativa, há o <strong>v-else</strong> (desde que este código seja parente de v-if), que implementa o código da seguinte forma:</p>
      <pre><code>&lt;div v-if="menu"&gt;ESTOU ATIVO!!&lt;/div&gt;<br>&lt;div v-else&gt;ESTOU inativo!! Very sad times :'( &lt;/div&gt;</code></pre>
      <p>O <strong>v-else-if</strong> habilita a possibilidade de condicionantes especiais, de expressões que não batem originalmente com <strong>v-if</strong>. Exemplo abaixo:</p>
      <pre><code>&lt;div v-if="job === 1"&gt;Estou Empregado na empresa 1!!&lt;/div&gt;<br>&lt;div v-else-if="job === 2"&gt;Estou Empregado na empresa 2!!&lt;/div&gt;<br>&lt;div v-else-if="job === 3"&gt;Estou Empregado na empresa 3!!&lt;/div&gt;<br>&lt;div v-else&gt;Estou desempregado. MIM DÁ EMPREGO :'( &lt;/div&gt;</code></pre>
      <h4>v-for</h4>
      <p>Esta função realiza a iteração entre os ítens de um array, na renderização de listas. Esta diretiva é possivelmente a mais importante, pois é muito utilizada em CRUDs e em sites que utilizam ajax. Ela espera um <strong>Array | objeto | numero | string (sim) e um Iterável</strong>, mas o que é mais usado é um array de objetos. Exemplos abaixo:</p>
<pre><code>var app = new Vue({
  el: '#app'
  data: {
    jobs: [
      { title: 'Desenvolvedor Back-end', company: 'Apple' },
      { title: 'Desenvolvedor Front-end', company: 'Microsoft' },
      { title: 'Desenvolvedor Mobile', company: 'Samsung' },
    ],
    <span class="comment">// Este é um array de objetos. tu pode pegar de qualquer lugar que quiser, de resultado do banco de dados, por exemplo.</span>
  }
})</code></pre>
<p>Após pegar os dados de jobs, iteraremos uma lista no site.</p>
<pre><code>
&lt;div v-for="(job, index) in jobs" :key="index"&gt;
   &lt;strong&gt;{{ item }}&lt;/strong&gt; &lt;br&gt;
  {{ company }}
&lt;/div&gt;
</code></pre>
<p>Repare em dois códigos importantes:</p>
<ol>
  <li>A presença de <strong>:key</strong> para cada item da lista. Isto ajuda a vue identificar qual item da lista está sendo definido. É uma boa prática sempre atribuir o valor de <strong>key</strong>.</li>
  <li>A utilização do valor de plural para o array de objetos, e o valor singular por cada item. Isto ajuda na identificação de cada item.</li>
</ol>
      <h4>v-on ou @</h4>
      <p>Javascript é uma linguagem especial por ter <strong>eventos</strong> no Browser. A vue implementou uma forma fácil de definir os eventos, bastando definir a sintaxe <strong>v-on:</strong> na frente do evento desejado. Para uma lista completa de eventos que o Javascript possui, pode pesquisar neste <a href="https://developer.mozilla.org/pt-BR/docs/Web/Events" target="_blank">link</a>. No exemplo abaixo, temos a implementação do evento <strong>click</strong>.</p>
<pre><code>{{code1}}<br>{{code2}}</code></pre>
      <p>Ambos os botões estarão setando o evento da mesma forma, sendo o <strong>@</strong> um atalho para <strong>v-for.</strong></p>
      <h4>v-bind ou :</h4>
      <p>Esta função habilita sobrescrever os atributos de uma tag html. Ela pode ter a sintaxe <strong>v-bind</strong> antes ou <strong>:</strong> como forma mais econômica. Da documentação oficial, temos uma lista bem grande dela em ação:</p>
<pre><code>
<span class="comment">&lt;!-- Alterando um atributo --&gt;</span>
&lt;img v-bind:src="imageSrc"&gt;;

<span class="comment">&lt;!-- Adicionando um atributo dinamicamente --&gt;</span>
&lt;button v-bind:[key]="value"&gt;&lt;/button&gt;

<span class="comment">&lt;!-- alterando um atributo, usando o atalho : --&gt;</span>
&lt;img :src="imageSrc"&gt;

<span class="comment">&lt;!-- Adicionando um atributo dinamicamente, usando um atalho --&gt;</span>
&lt;button :[key]="value"&gt;&lt;/button&gt;

<span class="comment">&lt;!-- Adicionando classes --&gt;</span>
&lt;div :class="{ red: isRed }"&gt;&lt;/div&gt;
&lt;div :class="[classA, classB]"&gt;&lt;/div&gt;
&lt;div :class="[classA, { classB: isB, classC: isC }]"&gt;

<span class="comment">&lt;!-- adicionando estilos --&gt;</span>
&lt;div :style="{ fontSize: size + 'px' }"&gt;&lt;/div&gt;
&lt;div :style="[styleObjectA, styleObjectB]"&gt;&lt;/div&gt;

<span class="comment">&lt;!-- adicionando propriedades para esta div --&gt;</span>
&lt;div v-bind="{ id: someProp, 'other-attr': otherProp }"&gt;&lt;/div&gt;

<span class="comment">&lt;!-- Adicionando atributos com modificadores --&gt;</span>
&lt;div v-bind:text-content.prop="text"&gt;&lt;/div&gt;

<span class="comment">&lt;!-- Adicionando propriedade "prop". "prop" precisa ser definido dentro do componente para poder ser usado. Isto passa valores de pai para filho --&gt;</span>
&lt;my-component :prop="someThing"&gt;&lt;/my-component&gt;
</code></pre>

      <h4>v-model</h4>
      <p>Desenvolvedores de angular abrem um sorriso ao ver que <strong>ng-model</strong> foi implementado do mesmo formato <strong>two-way data-binding</strong>, isto é, o valor atribuido na View é o mesmo de Model, e se hover qualquer mudança dele, ele é refletido em ambos os locais.</p>
      <p>Formulários em vue são fáceis de gerenciar. No exemplo abaixo capturamos um formulário de login e senha e exibimos os valores dele.</p>
<pre><code>&lt;form action="#" method="post" v-on:submit.prevent="process"&gt;
  &lt;input type="email" name="email" v-model="login.email" placeholder="E-mail" required&gt;
  &lt;input type="password" name="password" v-model="login.password" placeholder="Senha" required&gt;
  &lt;button type="submit" name="button" class="button"&gt;Fazer login&lt;/button&gt;
&lt;/form&gt;
</code></pre>
      <p>Neste código html, defini que os filhos do objeto <strong>login</strong> serão os valores que serão enviados para o formulário. Abaixo o código que processa esta requisição. O formulário está setado com um modificador <strong>.prevent</strong> para o evento <strong>submit</strong> que evita que o formulário seja mandado para outra página, fazendo a mesma função do <strong>$event.preventDefault();</strong>.</p>
<pre><code>var app = new Vue({
  el: '#app'
  data: {
    login: {
      email: '',
      password: ''
    }
  },
  methods: {
    process () {
      console.log(this.login);
      <span class="comment">// esta função apenas exibe o valor de this.login</span>
    }
  }
})
</code></pre>
      <p>Não fiz nenhum evento especial de validar os campos, se você clicar no botão vai exibir o valor de <strong>this.login</strong>.</p>

      <h2>Entendendo o famoso Lifecycle da VUE</h2>
      <p>Dentro da instância da Vue, há um ciclo de vida, que determina como ela funciona. Não é necessário entender todos, neste nossa apresentação, o foco é explicar como ela se processa.</p>
      <div class="image-full">
        <picture>
          <source srcset="~assets/img/lifecycle.avif" type="image/avif">
          <source srcset="~assets/img/lifecycle.webp" type="image/webp">
          <source srcset="~assets/img/lifecycle.png" type="image/png">
          <img src="~assets/img/lifecycle.png" alt="Ciclo de vida">
        </picture>
      </div>
      <p>Mas podemos pontuar, pela minha experiência, os <strong>gatilhos</strong> mais utilizados em Vue:</p>
      <h4>created()</h4>
      <p>Ele é o primeiro gatilho a ser iniciado. Neste estágio, a instância terminou de processar as opções, o que significa que o seguinte foi configurado: observação de dados, propriedades calculadas, métodos, callbacks de observação/evento.</p>
      <h4>mounted()</h4>
      <p>Lembra da função ready() da jquery? É mais ou menos compatível com <strong>mounted</strong>. Este <strong>mounted</strong> se tem o acesso a funções de renderização da DOM, templates internos e reatividade dos componentes. Aquele plugin esperto de AOS.js? Aplica aqui.</p>
      <h4>updated()</h4>
      <p>Chamado após uma mudança de dados faz com que o DOM virtual seja renderizado novamente e corrigido.</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  layout: 'page',
  data () :object {
    return {
      code1: this.html2text('<button @click="toggleMenu">{{menu === true ? \'Fechar Menu\' : \'Abrir menu\'}}</button>'),
      code2: this.html2text('<button v-on:click="toggleMenu">{{menu === true ? \'Fechar Menu\' : \'Abrir menu\'}}</button>'),
      mustache: '{{ mustache }}',
      item: '{{ job.title }}',
      company: '{{ job.company }}'
    }
  },
  methods: {
    html2text (html:string) :string {
      const tag = document.createElement('div');
      tag.innerHTML = html;
      return tag.innerHTML;
    }
  }
})
</script>

<style lang="stylus">
  .warning
    padding 20px
    background #d63031
    color #fff
    width 100%
    margin 0 0 30px
    border-radius 3px
    p 
      margin 0
      color #fff
    h4
      color #fff
  pre
    margin 20px 0
    padding 0
    background #000
    border-radius 3px
    code
      color #fff
      padding 20px
      overflow auto
      display block
    .comment
      color #999
  .react
    color #61dafb
    font-weight bold
  .home
    margin-top 120px
  .list
    display flex
    justify-content space-between
    align-items flex-start
    flex-wrap wrap
    margin 30px 0
    .list-item
      text-align center
      p 
        font-size 16px
      &.third
        width calc(100% / 3 - 40px)
  .image-full
    width 100%
    display flex
    justify-content center
    margin-bottom 30px
    img
      max-width 100%
      display block
      height auto
  .block
    display flex
    justify-content space-between
    flex-wrap wrap
    align-items flex-start
    margin 30px 0
    img
      max-width 400px
    .block-text
      width calc(100% - 450px)
  h1
    font-size 30px
    text-align center
    margin 0 0 50px
    font-weight normal
    color #41B883
    img
      width 45px
      height 45px
      margin-right 10px
    strong
      font-size 40px
      font-weight 900
      color #35495E
  h2
    color #35495E
    font-size 25px
    margin 0 0 20px
  h3
    color #35495E
    margin 0 0 20px
    font-size 22px
  h4
    color #35495E
    margin 0 0 20px
    font-size 20px
  p, li
    font-size 18px
    color #454545
    line-height 1.5
    margin 0 0 20px
  a 
    color #35495E
    font-weight bold
    text-decoration none
    border-bottom 1px dotted #35495E
</style>
