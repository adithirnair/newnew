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
  
  
  
  
