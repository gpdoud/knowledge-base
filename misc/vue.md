# Vue

## Table of Contents

- [Syntax](#syntax)
- [Creating a project](#create-a-new-project)
- [Adding Bootstrap](#add-bootstrap)
- [Composite API](#composite-api)
- [Binding](#binding)
    - [Structural binding](#template)
    - [Attribute binding](#attribute)
- [Reactive binding](#reactive-data)
- [Watchers](#watchers)
- [Events](#events)
- [Fall-through inheritance](#fall-through-inheritance)
- [Routing](#routing)

## Syntax

Camel case is used extensively. It can be used in a template as:

    <RouterLink ..>
    <router-link ..>

## Create a new project

To create a Vue application:

    npm init vue@latest

Prompted for project name, routing, etc.

    cd <project folder>
    npm update
    npm run { dev | build } // build for production

## Add Bootstrap

    npm i bootstrap

    // in main.js
    import 'bootstrap/dist/css/bootstrap.min.css';

## Composite API

This is the recommended API vs Option API

    // SFC - Single File Component
    // setup in script is called each activation
    <script setup>
        import { ref } from 'vue';
        import HomeComponent from './HomeComponent.vue';
        const active = ref(true);
        const props = defineProps(
            stateCode: { 
                type: String,
                required: true, // optional: defaults to false
                default: 'OH', // optional
                validator(value) {
                    return ['OH', 'IN', 'KY'].includes(value)
                }
            }
        )
    </script>
    <template>
        <h1>Component works!</h1>
    </template>

    // css applies only to this component
    <style scoped>
        h1 { color: red; font-weight: bold; }
    </style>

Can place the script, template, and style in separate files

    <script src='./component.js' setup></script>
    <template src='./componnet.html'></template>
    <style src='./component.css' scoped></style>

## Binding

### Template

`v-model`

For two-way binding

    // text
    <input v-model='phone' type='text'>
    // checkbox
    <input v-model='checked' type='checkbox'>
    // checkbox
    <input v-model='toggle' type='checkbox' 
        true-value='Yes' false-value='No'>
    // select
    <select v-model='selected'>
        <option v-for="option in options" :value='option.value'>
            {{ option.name }}
        </option
    // select

`v-for` and `v-for w/Key`

The `:key` is used to help Vue keep track of collections as they change

    <tr v-for="item { in|of } items">..</tr>
    <tr v-for='item in items' :key='item.id'>..</tr>
        <td>{{ item }}</td>

`v-if, v-else, v-elseif`

With `v-if, v-else, v-elseif`, the DOM is updated with the template. If the property value is not true, the template is NOT rendered in the DOM

    <button v-if="showButton">..</button>
    <button v-else="!showButton">..</button>

`v-show`

With `v-show`, the template always inclide the template but if the property is false, the template is hidden but still exists in the DOM

`v-html`

    const aStyle = "style='color:blue'";
    <span v-html="aStyle">..</span.
    // <span style='color:blue;'>..</span>

### Attribute

`v-bind:class or :class`

    const pStyle = ref({
        color: 'blue', font-size: '2em', font-weight: 'bold'
    })
    <p :class="pStyle">..</p>


`v-bind:id or :id`

    // const pid = "pageTitle"
    <div :id="pid">..</div>

`v-bind:disabled or :disabled`

    // const isDisabled = true
    <lable :disabled="isDiabled">..</label>

## Reactive data

`ref()`

    const name = ref('') // init to empty string

Using `ref()` defines a property that is a proxy that provides a reactive property. The data for the property (i.e. name) is accessible via the `value` property.

    console.log(name.value); // displays the value of name

But when used in the template, it is automatically unbound

    <span>{{ name }}</span> // displays the value without referencing name.value

`computed()`

Keeps a derived property up to date when a dependent property changes

    firstname.value = 'Greg';
    const fullname = computed(() => {
        return firstname.value + " " + lastname.value;
    });
    <h1>{{ fullname }}</h1>
    
## Watchers

Monitors properties and executes function on changes

    const nbr = ref(0);
    watch(nbr, (x) => {
        console.debug('x =>', x);
    });

    // watching multiple properties
    const balance = ref(0);
    const rate = ref(0);
    const months = ref(0);
    const interest = ref(0);
    watch([balance, rate, months], ([balance, rate, months], [prevBal, prevRate, prevMonths) => {
        interest.value = balance * (rate / 12) * months;
    })

## Events

Child to parent communication

    // Child component
    <script setup>
        defineEmits(['alert']);
    </script>
    <template>
        <button @click='$emit(['alert'])>Alert</button>
    </template>

    // Parent component
    <script setup>
    const onAlert = (evt) => {
        console.warn(evt);
    }
    <template>
        <ChildComponent @event="onAlert" />
    </template

## Fall-through inheritance

When a `class` or `style` prop is used on a child component, the prop is passed to the root template of the child automatically

    // Parent component
    <template>
        <ChildComponent class='text-danger fw-bold' />
    </template

    // ChildComponent
    <template>
        // <h1>..</h1> actual template
        <h1 class='text-danger fw-bold'>..</h1>
    </template>

## Routing

Can add routing when a project is created.

Router code resides in `./router/index.js`.

All routed components must be imported.

    import UserList from '../component/UserList.vue';

Add imported components to routes:

    { path: '/user/list', name: 'UserList', component: UserList },
    { path: '/user/detail/:id', name: 'UserDetail', component: UserDetail, params: true }
    // lazy load components
    { path: '/about', name: 'about', 
        component: () => import('../component/About.vue')}

`RouterLink`

    <RouterLink :to='/user/list'>User list</RouterLink>

    <RouterLink :to='`/user/detail/${id}`'>Detail</RouterLink>

`Programmatic routing`

    <script setup>
        import { useRouter } from 'vue-router';
        const router = useRouter();
        // navigate
        const navToList = () => {
            router.push('/user/list');
        }
    </script>