# Single Page Applications with Vue

1.  What is the entrypoint of an application?

resource that is accesspoint to the application

2.  What is the difference between a vue `component` and `page`?

component is a small feature that makes up part of the UI 

page is a new part of the application

3.  What is **_Component-Based Architecture_**?

a method for encapuslating larger pieces of UI into independent micro systems 

4.  What are the three tags that make up a Vue component?

script, template,

5.  What are **_lifecycle hooks_**? What are lifecycle hooks used for?

window into how library works behind the scenes

6.  Which component in Vue does the vue-router use to mount pages onto?
index.html

7.  What is the difference beteen the `AppState` and the state object within a component?

> | ANSWER HERE |

8.  What is the responsibility of `Services` in our Vue projects?

> | ANSWER HERE |

9.  What are **_props_** and how are they used? Provide an example

how to pass variables and other variables to other compenents



10. What is the Vue method used to create watchable objects such as `state` or `AppState`?

watchEffect

WEEK 6 DAY 2 NOTES

export const movieApi = Axios.create({
baseURL: '',
params: {
api_key: ''
include_adult: false
}
})

<!--NOTE--> pages--> HomePage.vue

template in homepage.vue

script
import { onMounted } from 'vue' ;
import { logger } from logger;

export default {
setup(){

    async function getMovies(){

try {

await moviesService.getMovies()

} catch (error) {
Pop.error(error, '[getting movies]')
}
}

    onMounted(() => {
      logger.log('Home Page mounted')
      getMovies()
    })

    onUnmounted

}
}

<!--NOTE create moviesService-->

class MoviesService {

async getMovies(){
const res = await movieApi.get('discover/movies')
logger.log('got movies', res.data)
}
}

<!--NOTE movie.js-->

create movie model

<!--NOTE appstate.js-->

<!--NOTE moviesservice.js-->

const movies - res.data.results.map(moviePojo => new Movie(moviePojo))

AppState.movies = movies

<!--NOTE create moviecard-->

props are used when v-for ing over a collecting

props are for passing down data from parent component to child component

props are on the child

router links are used with router.js

<!-- NOTE router-link :to="{ name: About }"-->

<!--NOTE moviedetails.vue-->

<!--NOTE store in appstate-->

<!--SECTION pokedex fireside-->

<!--SECTION week 6 day 3-->

<!--NOTE color-->

grab text color

select tool

eye dropper, copy hex value

<!--NOTE App.vue-->

router.js
create file path

<!--NOTE create CarsPage.vue-->

template

<!--NOTE Navbar.vue-->

router-link :to="{name: 'Cars'}"

should match name

<!--NOTE CarsPage.vue-->

onMounted
logger.log

async function getCars(){
  try {
await carsService.getCars()
  } catch (error) {
    Pop.error(error)
  }
}

<!--NOTE import/create carsService-->

async getCars(){
  const res = await api.get('api/cars')
  logger.log('got cars', res.data)
}

<!--NOTE car.js-->

let CarData = {}

<!--NOTE AppState store cars-->

<!--NOTE Carservice-->

const cars = res.data.map(carPojo => new Car(carPojo))

AppState.cars = cars

<!--NOTE CarsPage.vue-->

carspage.vue

return {
  cars: computed(() => AppState.cars)
}

{{cars}}

<!--NOTE CarCard.vue-->

in CarsPage.vue IMPORT CarCard.vue

in CarCard.vue CREATE prop 

in script export default

props: {
  carProp: { type: Car, required: true }
},
setup(){
  return{ }
}

 <!--NOTE in CARPAGE.VUE -->

 CARCARD :carProp="car" />

 RENAME car in template to CarProp

 <!--NOTE CarFormModal.vue-->

 template
 modal template

 CarsPage

 import CARFORMMODAL after CarCard

 engineTypes is an enum

 export default

 put in enums from cars API

 option v-for="(engineType, index) in engineTypes" :key="engineType + index" value="1"

 {{ engineType }}

 async createCar(){
  try {

    const carData = editable.value

    await carsService.createCar(carData)
  } catch(error){
    Pop.error(error)
  }
 }

 const editable = ref ({ })
 v-model="editable.make"

 onMounted(() => {
  editable.value.engineType = 'unknown'
  editable.value.color = '#FFFFF'
 })

 setup()

<!--NOTE carsService-->

async createCar(carData) {
  const res = await api.post('api/cars', carData)

  logger.log('created car', res.data)

  const car = new Car(res.data)

  AppState.cars.push(car)
}

<!--NOTE to login/provide credentials-->

account: object 

under return {
  account (( => computed ))
}
button v-if="account.id"

<!--NOTE CarCard.vue-->

delete button

setup(props){
  return{
async removeCar(){
  try {
  const carId = props.carProp.id
  logger.log(carId)
  await carsService.removeCar(carId)
} catch (error) {
  Pop.error(error)
}
}
  }
}

<!--NOTE carservice-->

async removeCar(carId)
  const res = await api.delete(`api/cars/${cars/carId}`)
  logger.log('removed car', res.data)

  const carIndex = AppState.cars.findIndex(c => c.id == carId)

  AppState.cars.splice(carIndex, 1)

  <!--NOTE create carform.vue-->

  in CarFormModal.vue

  import CarFormModal

  move createCar function to CarForm.vue

  <!--NOTE modalcomponent.vue-->

  slots?

  <!--NOTE edit car-->

  add button to carcard.vue

  @click="setCarToEdit()"

  setCarToEdit(){
    const carToEdit = props.carProp

    carsService.
  }

  <!--NOTE carsservice-->

  setCarToEdit(carToEdit){
    AppState.activeCar = carToEdit
  }

  <!--NOTE AppState-->

  activeCar = null

  <!--NOTE carCard.vue-->

  watchEffect(() => {
    if(AppState.activeCar){
      const carWithBrokenReference
      editable.value = AppState.activate
    }
  })

  handleSubmit(){
    if(editable.value.id){
      this.editCar()
    }
    else{
      this.createCar()
    }
  },

  editCar(carData)

  const res 

  const carIndex = AppState.cars.findIndex(c => c.index == carData.id )

  <!--NOTE clear form-->

  CarsPage

  @click="clearActiveCar"

  on button that opens the modal

  create function clearActiveCar(){
    const 
    carsService.setCarToEdit()
  }