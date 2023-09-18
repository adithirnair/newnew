<template>
    <div>
      <h1>About Page</h1>
      <router-link to="/">Back to Home</router-link>
    </div>
  </template>

  <template>
    <div>
      <h2>{{ title }}</h2>
      <button @click="emitEvent">Emit Event</button>
      <slot></slot>
    </div>
  </template>
  



//childcomponents
  <script>
  import { defineProps, defineEmits } from 'vue';
  
  export default {
    props: {
      title: String,
    },
    setup() {
      // Define props to access them in the setup function
      const props = defineProps(['title']);
  
      // Emit custom event
      const emit = defineEmits();
  
      const emitEvent = () => {
        emit('custom-event', 'Data from child component');
      };
  
      return {
        props, // Make props accessible in the setup function
        emitEvent,
      };
    },
  };
  </script>


 //class and style bindings


  <template>
    <div>
      <!-- Class Binding -->
      <div :class="getClassObject"></div>
  
      <!-- Style Binding -->
      <div :style="getStyleObject"></div>
    </div>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  
  export default {
    setup() {
      // Class Binding
      const isActive = ref(true);
      const hasError = ref(false);
  
      // Computed property to generate class object dynamically
      const getClassObject = computed(() => {
        return {
          active: isActive.value,
          error: hasError.value,
        };
      });
  
      // Style Binding
      const textColor = ref('blue');
      const textSize = ref(16);
  
      // Computed property to generate style object dynamically
      const getStyleObject = computed(() => {
        return {
          color: textColor.value,
          fontSize: textSize.value + 'px',
        };
      });
  
      return {
        isActive,
        hasError,
        textColor,
        textSize,
        getClassObject,
        getStyleObject,
      };
    },
  };
  </script>



//computed properties
<template>
    <div>
      <p>Count: {{ count }}</p>
      <p>Doubled Count: {{ doubledCount }}</p>
      <p>Squared Count: {{ squaredCount }}</p>
      <button @click="increment">Increment</button>
    </div>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  
  export default {
    setup() {
      const count = ref(0);
  
      // Computed properties
      const doubledCount = computed(() => count.value * 2);
  
      const squaredCount = computed(() => count.value * count.value);
  
      const increment = () => {
        count.value++;
      };
  
      return {
        count,
        doubledCount,
        squaredCount,
        increment,
      };
    },
  };
  </script>

//event handling

<template>
    <button @click="handleClick">Click me</button>
  </template>
  
  <script>
  export default {
    setup() {
      const handleClick = () => {
        // Handle the click event
        console.log('Button clicked');
      };
  
      return {
        handleClick,
      };
    },
  };
  </script>

//form binding input
<template>
    <div>
      <!-- a. v-model with various input types -->
      <input type="text" v-model="textInput" />
      <input type="checkbox" v-model="checkboxValue" />
      <input type="radio" v-model="radioValue" :value="1" />
      <input type="radio" v-model="radioValue" :value="2" />
      <select v-model="selectedOption">
        <option value="option1">Option 1</option>
        <option value="option2">Option 2</option>
      </select>
      <textarea v-model="textareaValue"></textarea>
  
      <!-- b. v-model modifiers -->
      <input type="text" v-model.lazy="lazyInput" />
      <input type="text" v-model.number="numericInput" />
      <input type="text" v-model.trim="trimmedInput" />
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      // Data properties
      const textInput = ref('');
      const checkboxValue = ref(false);
      const radioValue = ref(1);
      const selectedOption = ref('option1');
      const textareaValue = ref('');
  
      const lazyInput = ref('');
      const numericInput = ref(0);
      const trimmedInput = ref('');
  
      return {
        textInput,
        checkboxValue,
        radioValue,
        selectedOption,
        textareaValue,
        lazyInput,
        numericInput,
        trimmedInput,
      };
    },
  };
  </script>



//helloworld vue

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>



//home 

<template>
    <div>
      <h1>Home Page</h1>
      <router-link to="/about">Go to About</router-link>
    </div>
  </template>

//list rendering 

<template>
    <div>
      <!-- a. v-for with an Object -->
      <ul>
        <li v-for="(value, key) in myObject" :key="key">{{ key }}: {{ value }}</li>
      </ul>
  
      <!-- b. v-for with a Range -->
      <ul>
        <li v-for="n in 5" :key="n">{{ n }}</li>
      </ul>
  
      <template>
  <div>
    <template v-for="item in items" :key="item.id">
      <div>{{ item.name }}</div>
      <hr />
    </template>
  </div>
      </template>

  
      <!-- d. v-for with v-if -->
      <ul>
        <li v-for="item in items" :key="item.id" v-if="item.active">{{ item.name }}</li>
      </ul>
  
      <!-- e. v-for with a Component -->
      <ul>
        <custom-item
          v-for="item in items"
          :key="item.id"
          :item="item"
          @custom-event="handleCustomEvent"
        ></custom-item>
      </ul>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const myObject = ref({ a: 1, b: 2, c: 3 });
      const items = ref([
        { id: 1, name: 'Item 1', active: true },
        { id: 2, name: 'Item 2', active: false },
        { id: 3, name: 'Item 3', active: true },
      ]);
  
      const handleCustomEvent = (data) => {
        // Handle custom event from child component
      };
  
      return {
        myObject,
        items,
        handleCustomEvent,
      };
    },
  };
  </script>


//parent component

<template>
    <div>
      <child-component :title="childTitle" @custom-event="handleChildEvent">
        <p>Slot content goes here</p>
      </child-component>
    </div>
  </template>
  
  <script>
  import ChildComponent from './ChildComponents.vue';
  
  export default {
    components: {
      ChildComponent,
    },
    setup() {
      const childTitle = 'Child Component Title';
  
      const handleChildEvent = (data) => {
        console.log(`Received event from child component with data: ${data}`);
      };
  
      return {
        childTitle,
        handleChildEvent,
      };
    },
  };
  </script>
  
  
  
  
  
  
