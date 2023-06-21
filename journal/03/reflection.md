# Weekly Reflection

This reflection is open-format, so it can be whatever you like. Take this opportunity to write a bit on some of the things you have learned this week or some of the things that you are still struggling with; identify some challenges you had at the beginning of the week that you were able to overcome, or just generally reflect on how you are feeling at this point in the course.

## Prompts

- What went well this week?
- What did you learn that was a shock or surprise?
- What are you struggling with?
- What would you count as a victory?

// SECTION week 3 day 1 notes

create file "PlayersController.js" in controller.js file

export class PlayersController {
(router)
constructor(){
console.log("Players controller loaded");
}
}
--> router.js
open inspect, look for players controller tab

in PlayersController.js
under contructor

write out function directly (no function or let at the beginning when you are writing it in the export class)

creating objects in "player.js"
under value.js
Export class Player {

constructor (name, imageUrl){
this.score = 0
this.name = name
this.imgUrl = imageUrl
}

// getters must return a value
// getters do not take in any parameters

get PlayerDetails(){
let details = `Hello, my name is ${this.name} and my score is ${this.score}`

    return details

}
}

new Player('Jeremy')

store players in "appstate.js"

players = [
new Player()
]
update view with data in app state

private functions not accessible to the user but can still be called by the controller

writing a function outside of the class

function \_drawPlayers(){
console.log('draw players works')

let players = AppState.players

console.log(players[0].PlayerDetails);

}

class PlayersService.js
class PlayersService{

}

//NOTE singleton

export const playersService = new PlayersService()

//NOTE services do not generally have a constructor

//SECTION week 3 day 2

remove the id/view in the router.js
set view to empty string

to set up a variable, go into appstate

create variable in Appstate
coins = 0

write file in index.html

create file in controllers
"export class" in controller file
export class coinscontroller

put constructor in export class
console.log('coins controller')

need to update which controller is loaded in router.js
import coinscontroller file

any functions need to be inside the export function
console log in coinscontroller
add onclick

control/command P to move between files

index.html to add onclick
app.CoinsController.addCoin()

in ValuesService, add coinsService file
class CoinsService {

}
export const coinsService = new CoinsService()

once CoinsServce has been added, import to CoinsCointroller
appstate.coins++

controller updates the html
private functions are written outside of the export

in coincontroller.js

function drawcoins(){
let stringOfCoins = ''

for(let i = 0; i < Appstate.coins; i++){
stringOfCoins += 'coin emoji'
}

setText('coinsCount', Appstate.coins)
}
put id on p tag

addCoin(){
coinsService.addCoin()
drawCoins()
}

create a file in model.js

export class gachamon{
constructor(data){
this.name = data.name
this.rarity = data.rarity
this.emoji = data.emoji
}
}

Appstate.js
gachamons = [
new Gachamon({name: 'Mikey', emoji: 'monkey emoji', rarity: 'ultra-rare'}),
]

under service.js
write GastomansServie
export const gachamonsPersvice =

activeGachamon =

under gochcamons.

getGatchamon Large Tmeplate(){

}

function save

//SECTION
//NOTE week 3 day 3 notes

router view/ router.js controls what you see
router view --> homecontroller

//NOTE
router is "waiter" function--redirects

//NOTE -
add new object in router (new path)
path: '#/cars',
controller: CarsController,
view: '<h1>this is the cars page<h1>'

//NOTE -
router function --> controller function
export class CarsController {
constructor(){
console.log('cars controller is loaded')
}
}

//NOTE -
controller function --> index.html
add navlink
'#/cars'

//NOTE
index.html 'primary viewport'
create html
put stuff into index.html

//NOTE
index.html --> create CarView
in views folder
export const CarView = '' /_html_/
copy html created in index.html

//NOTE
Carview -->router.js

path: #/cars
COMMENT OUT INDEX HTML
MOVE TO "carview"

//NOTE
under "models"
create "car.js"

//NOTE
export class Car {

constructor (data) {

    this.id = // (utility function) // generateId()

this.img = data.img
this.year = data.year
this.make = data.make
this.model = data.model
this.miles = data.miles
this.price = data.price
this.description = data.description
this.color = data.color
this.ownedByGrandma = data.ownedbyGrandma

//REVIEW come back to this

this.listingDate = newDate
}
}

//NOTE -
car model --> carView

get CardTemplate (index.html file)

index.html becomes CardTemplate

//NOTE -

carView --> AppState

cars = [
//NOTE passing in object from model --> Car.js

    new Car({
        make: 'Honda',
        model: 'Corolla',
        year: 2004,
        price: 79000,
        miles: 790000,
        color:
        ownedbyGrandma: true,
        description: 'lightly used',
    })

]

//NOTE -
AppState-->CarsController

function \_drawars(){
const cars = AppState.cars
let template = ''

    cars.ForEach(car => template += car.cardTemplate)

//NOTE add "id" to section id in html in "carview.js"
setHTML('carListings', template)

//NOTE back to CarsController.js
}
console.log('cars controller loaded', Appstate.cars)

//NOTE Car.js
img src-- string interpolate
${this.img}
export class C

//NOTE add form in index.html

//NOTE index.html --> Carview.js

//NOTE CarView.js
after form has been submitted

form onsubmit="carController.

//NOTE CarView.js --> CarController.js
createCar(){
event.preventDefault()
console.log('Did the form submit?', );

const form = event.target

const carData = getFormData(form)

carData.ownedByGrandma = carData.ownedByGrandma == 'on' ? true : false

console.log('car data!, carData.ownedByGrandma);

carsService.createCar(carData)
//NOTE create carService, import
}

//NOTE - CarView --> CarService

class CarsService {
createCar(carData){
const NewCar = new Car(carData);
console.log('constructed', newCar)

AppState.emit(newCars)
\_drawCars()

        //SECTION form changes

        AppState.cars.push(newCar)
    }

}
