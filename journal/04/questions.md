# Understanding Asynchronous Code, and API's

1.  What is the difference between `asynchronous` code and `synchronous` code?

async code awaits a response from another piece of code

2.  What is an event listener?

piece of code that waits for a particular "event" or piece of code to run

3.  What does _REST_ stand for, and in simple terms what does it mean??

representational state programming

allows an unlimited amount of arguments

4.  What is a callback / higher order function?

> | ANSWER HERE |


5.  What is a `promise`? How do you capture an error from a `promise`?

> waiting for a different piece of code to run

try catch

6.  Name three processes used to make requests over `HTTP`?

> XML, JSON, HTML

7.  What does the `API` acronym stand for?

> | application programming interface

8.  What must you do in order to `await` a promise inside of a function?

> async

9.  What is the purpose of encapsulation in programming?

> | keep like data together

10. What is `HTTP` response code for a successful request?

> 200

11. What is a 400 error?

bad request

controller
export class mon

getMonsters() {

}

class MonstersService {

//NOTE the hard way

async getMonsters(){

const response = fetch ()
console.log('here is the response', response);

const jsonData = await response.json()
console.log('here is the json', jsonData);

const response = zeldaApi.get()
console.log('got monsters', response);
}

//NOTE AxiosServices.js
export const zeldaApi = axios.create({
baseUrl: '',
timeout: 8000
})

create model monster.js

constructor (data) {

}

const monsterData = {

}

//NOTE week 4 day 2

env.js = environment

baseurl = local host:3000

CarsController.js
export class CarsController

constructor() {
console.log('cars controller loaded')
}

CarsController.js -->router.js
add <h1>html</h1>
add new #path
#cars, "CarsController"
view is empty string

the skeleton settings in index.html can be removed once login is possible

router.js --> CarsController.js

    async getCars() {
        try {
            await carsService.getCars()
                } catch (error) {
                    console.error(error);
                        Pop.error(error.message)
                        }

                        }

//NOTE create CarsService.js

import { api } from "./AxiosService.js"
class CarsService{

    getCars(){
        aync const res = await api.get('api/cars')
        console.log('got cars', res.data);

}
}

    export const CarsService.js

        export class Car
        constructor (data) {

        this.id = data.id
        this.make = data.make
        this.model = data.model
        this.imgUrl = data.imgUrl
        this.year = data.year
        this.price = data.price
        this.description = data.description
        this.engineType = data.
        this.color = data.color || '#00000'
        this.creatorId = data.creatorId
        this.createdAt = new Date(data.createdAt)
        this.updatedAt = new Date(data.updatedAt)
        this.creator = data.creator

}

CarsService.js -->AppState.js

/@@type {import cars}
cars = []

AppState.js -->CarsService.js

class CarsService {

    const builtCars = res.data.map(carPojo => new Car(carPojo))

    AppState.cars = builtCars

}

CarsServices --> CarsController

Appstate.on('cars', \_drawCars)

function \_drawCars() {

    const cars = AppState.cars

    console.log('drawing cars', cars);

    let template = ''

    cars.forEach(car => template += car.CardTemplate)

}

    function _showFormButton() {
        const account = AppState.account

        if (!account) {
            return
        }

        const carFormButton = document.getElementbyId('carFormButton')
        carFormButton(')
    }

Car.js

get CardTemplate()

Car.js --> CarsController.js

async CreateCar() {
try {
event.preventDefault()

        console.log('form submitted')

        const form = event.target

        const carData = getFormData(form)

        console.log('car data!', carData);

    } catch (error) {
        console.log('error')


    }

}

CarsController.js --> CarsService.js

    async getCars(){
        const res = await api.get('api/cars', carData)

        console.log('got cars')

        const builtCar = new Car(res.data)

        AppState.cars.push(builtCar)

        AppState.emit('cars')




    async deleteCar(carId) {
        try {
            await carsService
        }
    }
    }

    const carIndex = AppState.cars.findIndex(car => car.id == carId)

    AppState.cars.splice(carIndex, 1)

async createCar (carData) {

const res = await api.post('api/cars', {name: 'Jeremy' })

    console.log('created car)

    const newCar = new Car(res.data)

    //NOTE map exists on array, not object

}

    must authenticate before logging in/posting

    codeworks has auth/sign in settings for posting

    copy domain, audience, clientId and enter in env.js

//NOTE now you can remove your auth settings in index.html

400
CarsService.js

add newCar function

CarsService.js

add button to delete Car
button onclick"app.CarsController.deleteCar('${this.id}')"

index --> CarsController

add delete Car function

//NOTE in Car.js

get ComputeDeleteButton() {
if (!AppState.account.id == this.creatorId || AppState.account.id!= this.creatorId) {
return ''
}
return ` <button onclick="app.CarsController.deleteCar('${this.id}')" class="btn btn-danger">Delete Car</button>`

    }

}

write listener to redraw the cars in the CarsController

get ComputeEditButton() {
if (!AppState.account || AppState.account.id != this.creatorId) {
return ''
}
return `<button onclick="app.CarsController.drawEditForm('${this.id}')" class="btn btn-info">Edit Car</button>
}

get EditForm() {
return `
form from index.html
value ${}
on card
}

static get CreateForm() {
`return
    form
    `

    static means you don't have to build out the class

}

//SECTION week 4 day 3 notes

https://www.dnd5eapi.co

mvc auth

env.js

//NOTE check gregslist for this

localhost:3000 --> e

//NOTE -

make request to dnd api

in AxiosService.js

create new export const api = axios.create

//NOTE DO NOT REMOVE current one

//NOTE AxiosService.js --> SpellsController.js

//NOTE export class SpellsController.js {
    constructor {
        console.log('spells controller loaded');
    }

    async getSpells(){
        try {
            await spellsService.js
        } catch (error) {

        } console.error
    }
}

//NOTE SpellsController.js --> SpellsServices.js

//NOTE import { dndApi }
class SpellsService {

    async getSpells () {
        const res = await dndApi.get('api/spells')
        console.log('got spells')
    }
}

//NOTE export const spellsService = new SpellsService()

//NOTE SpellsServices.js --> SpellsController.js



//NOTE SpellsController.js -->AppState.js

move down @type {Object[]}
spells = []

AppState.js --> SpellsService.js

ADD

AppState.spells = res.data.results

console.log(res.data)


//NOTE SpellsService.js --SpellsController.js

function _drawSpells() {
    let spells = AppState.spells

    let template = ''

    spells.forEach(spell => {
        template += `
        <li>Spell</li>
        `
    })

    setHTML('spellList', template)
}

//NOTE -SpellsController --> index.html 

build out html

add spellList identifier

//NOTE index.html --SpellController.js

change <li>spell</li> to ${spell.name}

spells.forEach(spell => {
    template += `
    <li onclick="app.SpellsController.getSpellDetails>
})

async getSpellDetails(spellIndex)

//NOTE create Spell.js
export class Spell {
    constructor (data) {
        this.name = data.name

        //FIXME - change this into a string
        this.description = data.desc
        this.range = data.range
        this.duration = data.duration
        this.damage = data.damage ? data.damage.damage_type.name : 'Does no damage'
        this.level = data.level ||  0
        this.material = data.material || 'No material needed'
        this.ritual = data.ritual
        this.concentration = data.concentration
        this.castingTime = data.casting_time
        this.components = data.components || []
    }
}

let spellData = {

}

//NOTE Spell.js --> AppState.js
activeSpell = null
move down
import spell.js

//NOTE AppState.js --> SpellService.js

in async get spelldetails

AppState.activeSpell = newSpell

//NOTE SpellService.js --> SpellController.js

function _drawActiveSpell() {

    let spell = AppState.activeSpell
    console.log('active spell', spell);
}

add event listener

AppState.on('spells', _drawSpells)
AppState.on('activeSpell', _drawActiveSpell)

//NOTE index.html

write html for Details

move to Spell.js

get DetailsTemplate()

//NOTE SpellController.js

in _drawActiveSpell
(setHTML)

add string interpolation to DetailsTemplate

//NOTE to save

in Details template

add button "save to sandbox"

add onclick "app.SandboxSpellsController.js"

//NOTE add new controller SandboxSpellsController.js

export class SandboxSpellsController.js {
    constructor () {
        console.log('sandbox controller loaded');
    }

    async createSpell() {
try{
    await sandboxSpellsService.create
}
    }
}

//NOTE create SandboxSpellsService.js

class SandboxSpellsService {

    async createSpell() {
        const res = await api.post('api/spells')
        console.log()
    }
    
}

export const sandboxSpellsService = new SandboxSpellsService

//NOTE update router with SandboxSpellsController

//NOTE SandboxSpellsService

ADD to async create spell

const spellToSendToApi = AppState.activeSpell

const res = await api.post

//NOTE return to FIXME tag

this.description = data.desc.join('/n)

//NOTE index.html

add navlink my spells
#/mySpells

Router .js
add path '#/mySpells',
Controller: SandboxSpellsController.js
view: ''

//NOTE add DNDspellsView

export const DnDSpellsView 

put in html

//NOTE - 

in router 

add DnD spellsView

//NOTE sandboxspells controller

async getMySpells() {
    trycatch
}

//NOTE add event listenener to load spells

AppState.on()

//NOTE Appstate.js
mySpells = []

//NOTE = SandboxService.js

async getmySpells.js

ADD 
const builtSpells = res.data.map(spellPojo => new Spell (spellPojo))

//NOTE this changes them from object to array

AppState.myspells = builtSpells


//NOTE Spell.js

//NOTE this description = data.description || data.desc.join('\n')

//NOTE index html
change id to "mySpellDetails" "mySpellList"

//NOTE spell.js
add getMySpellListItemTemplate(){
    add li from SpellsController
    <li onclick="app.SandboxSpellsController.setActiveSpell('${this.id}')>

}

//NOTE SandboxSpellsController

in contructor

AppState.on('mySpells', _drawMySpells)

function _drawMySpells

remove set HTML from _drawMySpells

let mySpellListElem = document.getElementbyId('mySpellList')
if(!mySpellListElem){
    return
}
mySpellListElem.


//NOTE Spell.js
this.id = data.id || ''

//NOTE SandboxSpellsController.js

setActiveSpell(spellId) {
    const foundSpell = AppState.mySpells.find(spell => spell.id == spellId)

    if(!foundSpell) {
        throw new Error("INVALID ID")
    }

    AppState.activeSpell = found Spell

    console.log('active', ActiveSpell)
}

//NOTE SandboxSpellsController

add to contructor

AppState.on('active spell', _drawMyActiveSpell)

function _drawMyActiveSpell

//SECTION CHECKPOINT

create SandboxSpellsView.js

move index in here

export const SandboxSpellsView = /*html*/

//NOTE router

add view SandboxSpellsView

path #!SECTION

//NOTE SandboxSpellsController

//NOTE - checkpoint
"prepared" boolean
Spell.js
this.prepared = data.prepared || false

edit boolean

get MySpellListItemTemplate() {
    input onchange="app.SandboxSpellsController.toggleSpellPreparation('${this.id}')" type="checkbox" id="spellPreparation"
}


//NOTE SandboxSpellsController.js

async toggleSpellPreparation(spellId) {
    try{
        await sandBoxsSpellsService.toggleSpellPreparation(spellId)
    }
}

//NOTE SandboxSpellServices.js
 
 async toggleSpellPreparation(spellId) {

    const foundSpell = AppState.mySpells.find(spell => spell.id == spellId)



    const res = await api.put(`api.spells/${spellId}`)
    console.log('edited spell', res.data);
 }

 //NOTE create new object that has same properties as "prepared"

 { prepared: !foundSpell.prepared }

 replace const foundSpell with const foundSpellIndex

 const updatedSpell = newSpell(res.data)

 AppState.mySpells.splice(foundSpellIndex, 1, updatedSpell)

 //NOTE Spell.js

 get MySpellListItemTemplate(){
    <input {${this.prepared ? 'checked' : ''}>
 }

 //NOTE SandboxSpellsView COUNT OF SPELLS COUNT OF PREPARED SPELLS 

 add id "spell count"
 id "spell list"

 //NOTE SandboxSpellsController

 in _drawMySpells(){

setText('spellCount', mySpells.length)

setText('preparedSpellCount', mySpells.filter(spell => spell.prepared).length)

AppState.emit('mySpells')
 }

//SECTION WEEK 4 DAY 4 NOTES

















