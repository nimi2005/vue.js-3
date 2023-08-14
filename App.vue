<template>
  <div> {{ greet }} {{name}}</div> 
  <div class="new" v-html="text"></div>

      <!-- v-bind --> 
              <h2 v-bind:id="headingId"> heading</h2> 
              <button v-bind:disabled="isDisabled">Bind</button>
              <h3 class="underline" v-bind:class="status">Underlined text</h3>
              <h2 v-bind:class="isPromoted && 'promoted'">Promoted Movie</h2>
              <h2 v-bind:class="!isSoldout? 'soldout' : 'new2'"> sold out</h2>
              <h2 v-bind:class="['new2' , 'promoted']">Newly Pomoted Movies</h2>
              <h2 v-bind:class="[isPromoted && 'promoted', !isSoldout? 'soldout' : 'new2']">Array conditional movies</h2>
              <h2 v-bind:class="{promoted: isPromoted,
                                  new2: isSoldout,
                                 soldout: !isSoldout,}">Object conditional array</h2>

              <h2 v-bind:style="{
                   color: highLightColor,
                   fontSize: headerSize + 'px',}">Inline style</h2>
      <!-- End of v-bind -->
           
           <!-- V-if, v-else-if, v-else -->
        <h2 v-if="number === 0">The number is {{ number }}</h2>
        <h2 v-else-if="number < 0">The number is Negative</h2>
        <h2 v-else-if="number > 0">The number is Positive</h2>
        <h2 v-else> Not a number</h2>
          <!-- End of V-if, v-else-if, v-else -->

      <!-- v-if display -->
            <template v-if="display">
               <h2>Hello world</h2>
               <h2>Codevolution</h2>
               <h2>Nimot</h2>
            </template>
      <!-- End of v-if display -->

      <!--v-show -->
       <h2 v-show="show">using v-show</h2>
       <h2 v-if="show">using v-if</h2>
       <button v-show="!isTrue">Mini</button>
      <!-- End of v-show -->
     

       <!-- v-for -->
    <h2 v-for="(name , index) in names" :key="name">{{ index }} {{ name }}</h2>
       <!-- using arrays of objects -->
    <h2 v-for="name in fullName" :key="name.first">{{name.first}} {{name.last}}</h2>
       <!-- End of using arrays of objects -->
    
    <div v-for="actor in actors" :key="actor.name"> 
    <h2>{{actor.name}}</h2>
    <h4 v-for="movies in actor.movies" :key="movies"> {{movies}} </h4>
    </div>
  <template v-for="name in loves" :key="name">
  <h2 v-if="name === 'Zeenat'"> {{ name }}</h2>
  </template>      
</template>

<script>


export default {
  name: 'App',
     data() {
       return {
         name: 'Nimot',
         greet: 'Hello',
         text: '<b>Hello-world</b>',
         headingId: 'heading',
         isDisabled: true,
         status: 'danger',
         isPromoted: true,
         isNew: true,
         isSoldout: true,
         highLightColor: 'cyan',
         headerSize: 60,
         number: -5,
         display: true,
         show: false,
         isTrue: true,
         names: ['Muneebah', 'Zeenat', 'Al-ameen'],
         fullName: [
           { first: 'Muneebah', last: 'Matti' },
           { first: 'Zeenat', last: 'Matti' },
           { first: 'Al-ameen', last: 'Matti' },
                       ],
         actors: [
           {
             name: 'Adedimeji',
             movies: ['jagunjagun', 'sugarrush'],
                          },
                          {
             name: 'Odunlade',
             movies: ['samualajo', 'Alanipomolekun'],
                            },
                            ],
         loves: ['Muneebah', 'Zeenat', 'Al-ameen'],
       }
     },
    methods: {
      
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.new{
  color: red;
}

.underline{
  text-decoration: underline;
}
 
 .danger{
   color: red;
 }

.promoted{
  font-style: italic ;
}

.new2{
  color: olivedrab;
}

.soldout{
  color: blue;
}
</style>
