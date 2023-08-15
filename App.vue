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
                   fontSize: headerSize + 'px',}">Inline style
              </h2>
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
<!-- end of v-for -->


<!-- learning how to use methods --> 
       <h2>add numbers - {{ add(2,4,8)}}</h2>
       <h2>Multiply method - {{ multiply(baseValue) }} </h2>  
<!-- End of learning methods --> 


<!-- learning how to handle events -->
      <h3>{{movieName}}</h3>
     <div>
      <h2> {{ count }}</h2>
      <button v-on:click=" count ++">Increament</button>
      <button v-on:click=" count --">Decreament</button>
     </div>
<!-- End of how to handle events -->


<!-- learning form handling --> 
    <div> 
    <pre>
    {{ JSON.stringify(formValues, null, 2)}}
    </pre>
    </div>

    <form @submit.prevent="submitForm">

  <!-- the tim and lazy modifiers -->
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" v-model.trim.lazy="formValues.name" />
    </div>

    <div>
      <label for="country">Profile summary</label>
      <textarea id="profile" v-model="formValues.profileSummary" />
    </div>
  
    <div>
      <label for="country">Country</label>
      <select id="country" v-model="formValues.country">
        <option value="">select a country</option>
        <option value="nigeria">Nigeria</option>
        <option value="germany">Germany</option>
        <option value="dubai">Dubai</option>
        <option value="south korea">South Korea</option>
      </select>
     </div>

    <div>
      <label for="job-location">Job Location</label>
      <select id="job-location" multiple v-model="formValues.jobLocation">
        <option value="nigeria">Nigeria</option>
        <option value="germany">Germany</option>
        <option value="dubai">Dubai</option>
        <option value="south korea">South Korea</option>
      </select>
     </div>

     <div>
      <input type="checkbox" id="remoteWork" v-model="formValues.remoteWork" true-value="Yes" false-value="No" />
      <label for="remoteWork">Open to remote work?</label>
     </div>

     <div>
     <label>Skill Set</label>
      <input type="checkbox" id="html" value="html" v-model="formValues.skillSet" />
      <label for="html">Html</label>
      <input type="checkbox" id="css" value="css" v-model="formValues.skillSet" />
      <label for="css">Css</label>
      <input type="checkbox" id="javascript" value="javascript" v-model="formValues.skillSet" />
      <label for="javascript">javascript</label>
     </div>

     <div>
     <label>Skill Set</label>
      <input type="radio" id="0-2" value="0-2" v-model="formValues.yearsofExperience" />
      <label for="0-2">0-2</label>
      <input type="radio" id="3-5" value="3-5" v-model="formValues.yearsofExperience" />
      <label for="3-5">3-5</label>
      <input type="radio" id="6-10" value="6-10" v-model="formValues.yearsofExperience" />
      <label for="6-10">6-10</label>
      <input type="radio" id="10+" value="10+" v-model="formValues.yearsofExperience" />
      <label for="10+">10+</label>
     </div>


  <!-- number modifier -->
      <div>
      <label for="age">Age</label>
      <input type="number" id="age" v-model.number="formValues.age" />
      </div>

     <div>
     <button >Submit</button>
     </div>
    </form>

<!-- End of form handling -->


<!-- v-once -->

   <h2 v-once>{{ fruit }}</h2>
   <button @click="fruit = 'Banana'">Change fruit </button> 

<!-- End of v-once-->

<!-- v-pre -->
    
    <h2 v-pre>{{ fruit }}</h2>
 
<!-- End of v-pre -->

<!-- computed properties--> 
   <h2>About- {{place}} {{month}}</h2>
   <h2>Computed Properties - {{address}}</h2>
   <button @click="changeAddress">change Address</button>

     <template v-for="read in items" :key="read">
  <h2 v-if="read.price > 100">{{ read.title }} {{ read.price}}</h2>
    </template>

  <h2 v-for="read in expensiveItems" :key="read">{{read.title}} {{ read.price }}</h2>
<!-- end of computed properties--> 
 
<!-- Learning how to use watchers -->
   <h2>Volume Tracker (0-20)</h2>
   <h2>Current Volume {{ volume }}</h2>
   <button @click="volume += 2">increase volume</button>
   <button @click="volume -= 2">decrease volume</button>
   <input  type="text" v-model="movie" />
   <input  type="text" v-model="movieInfo.title" />
   <input  type="text" v-model="movieInfo.actor" />
<!-- Learning how to use watchers Ends here -->
</template>

<script>


export default {
  name: 'App',

// using the data property
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
         items: [
           {
             id: 1,
             title: 'Tv',
             price: 100,
           }, 
           {
            id: 4,
             title: 'phone',
             price: 200,
           }, 
           {
            id: 3,
             title: 'laptop',
             price: 300,
           }, 
           {
             id: 1,
             title: 'cloth',
             price: 400,
           }
         ],
         baseMultiplier: 5,
         baseValue: 2,
         movieName: 'Eternals',
         count: 2,
         formValues:{
           name: "",
           profileSummary: "",
           country: "",
           jobLocation: [],
           remoteWork: "No",
           skillSet: [],
           yearsofExperience: "",
           age: null,
         },
         fruit: "melons",
         place: "Lagos",
         month: "May",
         volume: 0,
         movie: '',
         movieInfo: {
           title:'',
           actor:'',
         }
       }
     },

     
//using the computed property
    computed: {
      address:{
        get() {
          return `${this.place} ${this.month}`
        },
        set(value){
          const names = value.split(' ')
          this.place = names[0]
          this.month = names[1]
        },
      },
      expensiveItems(){
        return this.items.filter( read => read.price > 100)
      }
    },

// using watcher 
    watch:{
     volume(newValue, oldValue){
       if(newValue > oldValue && newValue=== 16){
         alert('Listening to a high volume for long time may damage your hearing')
     }
     },
     movie:{
      handler(newValue){
    console.log(`calling API with movie name = ${newValue}`)
     },
     immediate: true,
     },
     movieInfo: {
       handler(newValue){
         console.log(`calling API with movie title = ${newValue.title} and actor= ${newValue.actor}`)
       },
      deep: true,
     }
     
     },


// using the methods
    methods: {
      add(a,b,c){
        return a + b + c 
      },
      multiply(num){
       return  num * this.baseMultiplier
      },
      submitForm(){
         console.log('form.values', this.formValues)
      },
      changeAddress(){
       this.address = 'Ibadan June'
      }
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
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

 label{
   font-weight: bold;
   display: flex;
   margin-bottom: 5px;
 }

 input + label{
   font-weight: bold;
   display: inline-flex;
   margin-right: 20px;
 }

input[type = "text"],
textarea,
select{
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
