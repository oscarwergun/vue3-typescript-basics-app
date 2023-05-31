See [Deploy website on Netlify](https://fanciful-chimera-360946.netlify.app/)
<img width="1722" alt="Screenshot 2023-05-31 at 15 51 18" src="https://github.com/oscarwergun/vue3-typescript-basics-app/assets/127099022/c1ecf1e3-57cc-4245-9131-a7e69c1b4d99">

# job-viewer

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

##
Reactive property with composition API
```
const state = reactive({
  title: 'Find your dream work with CodeGuruOzzy',

  })
//toRef use to create a ref for a property on source reactive object
  return { ...toRefs(state) }
```

## 
Ref property with 
```
! KEEP IN MIND YOU NEED TO USE GENERIC ARGUMENTS TO SPECIFY THE TYPE OF THE VARIABLE AND YOU NEED TO USE .value property to change the value of the variable 

  const title = ref('Oscar');
  const age = ref<number>(25)

  return {title ,age}
```
### PASS PROPS THROUGH INTO CHILD COMPONENT
```
export default defineComponent({
    name: "JobList",
    props: {
        jobs: {
            required: true,
            type: Array as PropType<Job[]>
        }
    }
})
```
