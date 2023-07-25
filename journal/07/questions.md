# Managing the Fullstack Application

1. Describe the two ways to bind Data in Vue?

> | ANSWER HERE |

2. The `SPA` acronym stands for what?

> | ANSWER HERE |

3. What are some of the advantages/uses of a `SPA` over a traditional one?

> | ANSWER HERE |

4. What does the `onMounted` method in Vue do?

> | ANSWER HERE |

5. What is the `v-model` attribute in Vue for, and when might you use it?

> | ANSWER HERE |

6. What is the package.json file used for?

> | ANSWER HERE |

7. Which Vue attributes(directives) could you use to conditionally render elements on a page?

> | ANSWER HERE |

8. What is the purpose of the `key` attribute when using `v-for` on an element?

> | ANSWER HERE |

9. What is the `<slot>` element and what is it used for?

> | ANSWER HERE |

<!--NOTE full stack application notes-->

creating photo album that multiple people can collab on

archived boolean on each album

archive boolean false -->true

album --> collaborator --> account --> account --> picture -->

express-vue

don't go into workspace

open top level folder, initialize folder

make first commit before entering workspace

//NOTE env folder, enter slack variables, change project name

close client folder, spin up project

//NOTE will need 2 sets of auth tokens for postman tests

//NOTE postman test--have to write code and run tests in the order of the tests

//SECTION create schema-- models--album.js

import { schema }

don't need id

export const AlbumSchema = new Schema({

title: {type: String, required: true, maxLength: 75, minLength: 3},

archived: {type: Boolean, default: false},

coverImg: {type: String, required: true, maxLength: 250, minLength: 3},

category: {type: String, enum: ['cats', 'dogs', 'games', 'gachamon', 'animals', 'misc'], required: true, default: 'misc'},

creatorId: {type: Schmea.Types.ObjectId, required: true, ref: 'Account'},

ADD VIRTUALS

AlbumSchema.virtual('creator', {
localField: 'creatorId',
foreignField: \_id,
justOne: true,
})

})

//NOTE Dbcontext.js

Albums = mongoose.model

//NOTE AlbumsController.js

//NOTE AlbumsServices.js

//NOTE AlbumsController.js

import BaseController

//NOTE CREATE FUNCTIONS IN POSTMAN ORDER

export class AlbumsController extends BaseController {
constructor(){
super('api/albums')
this.router

    .get('', this.getAlbums)
    .get('/:albumId', this.getAlbumById)

    .use(Auth0Provider.getAuthorizedUserInfo)
    .post('', this.createAlbum)
    .delete('/:albumId,')

}

async createAlbum(req, res, next){
try {
const albumData = req.body
albumData.creatorId = req.userInfo.id
const album = await AlbumsService.createAlbum(albumData).populate('creator', 'name picture')
//NOTE await newAlbum.populate('creator', 'name picture')
return res.send(album)
} catch (error){
next(error)
}
}

async getAlbums(req, res, next) {
try {
const albums
} catch(error)
} next(error)
}

async getAlbumById (req, res, next){
try {
const albumId = req.params.albumId
const album = await albumsService.getAlbumById
return res.send(album)
}catch(error)
next(error)
}

async archiveAlbum (req, res, next){
try {

}
}

//NOTE albumServices.js

class AlbumsService {

async createAlbum(albumData){
const newAlbum = await dbContext.Albums.create(albumData)
return newAlbum
}

async getAlbums(){
const albums = await dbContext.Albums.find().populate('creator', 'name picture')
return albums
}

async getAlbumById(albumId){
const album = await dbContext.Albums.findById(albumId).populate('creator', 'name picture')
if(!album){
throw new BadRequest(`Album at albumId: ${albumId} does not exist.`)
}
return album
}
}

async archiveAlbum(albumId){
const albumToArchive = await this.getAlbumById(albumId)

//NOTE .toString to prevent errors
if(albumToArchive.creatorId.toString() != userId) {
throw new Forbidden('You are not the creator of this album')
}

albumToArchive.archived = true
await albumToArchive.save()
return albumTOArchive
}

export const albumsService = new AlbumsService()

//SECTION front end full stack project

//NOTE HomePage.vue

async function getAlbums(){
try {
await albumsService.getAlbums()

}catch(error)
Pop.error(error.message)
}

onMounted(() => {

})

//NOTE AlbumsService.js

class AlbumsService {

getAlbums(){
const res = await api.get('api/albums')
logger.log('[GOT ALBUMS]', res.data)
}

export const albumsService = new AlbumsService()
}

//NOTE Album.js

export class Album {

constructor (data){

this.id = data.id
this.title = data.title
this.coverImg = data.coverImg
this.category = data.category
this.creatorId = data.creatorId
this.creator = data.creator
}

let data = {

}
}

//NOTE AppState.js

albums: [],

//NOTE AlbumsService.js

const albums = res.data.map(albumPojo => new Album(albumPojo))

AppState.albums = albums

//NOTE Homepage.vue

template

 <div>

{{ albums }}

</div>

</template>

//NOTE Homepage.vue

remove data dump of albums

format template

ALBUM COLLABORATIONS GO HERE

imgs can be saved in assets

//NOTE change background image

App.vue

body{
background-image: url('./assets/img/');
}

//NOTE HomePage.vue

<div v-for="album in albums" :key="album.id" class="col-md-3">
<div>
<img :src="album.coverImg" :alt="album.title" class="img-fluid">
<h2>{{ album.title }}</h2>

//NOTE AlbumCard.vue

abstract out AlbumCard, insert in here

//NOTE HomePage.vue

<AlbumCard :albumProp="album" />

//NOTE AlbumCard.vue

ANYTHING IN THe ALBUMCARD WILL NEED TO BE albumProp

<h2> {{albumProp.title}} </2

props: {
  albumProp: {tyle: Album, required: true }
}

setup(){
  function getRandomColor(){
    const colors = ['bg-primary', 'bg-success', 'bg-warning', 'bg-secondary', 'bg-info', 'bg-danger']
    const randomIndex = Math.floor(Math.random() * colors.length)
    return colors[randomIndex]
  }
}

//NOTE AlbumDetailsPage.vue

//NOTE router.js

path: '/albums/:albumId',
name: 'Album'
component

//NOTE AlbumCard.vue

<router-link :to="{ name: 'Album', params: {albumId: albumProp.id} }">

//NOTE AlbumDetailsPage.vue

setup(){
  const route = use route()
  
  function getAlbumById(){
    try {
      const albumId = rout.params.albumId
      await albumsService.getAlbumById(albumId)
    }
  }
}

//NOTE AlbumsService.js

async get AlbumById(albumId){
  const res = await api.get(`api/albums/${albumId}`)
  logger.log('[GOT ONE ALBUM]', res.data)
}

//NOTE AppState

albums: [],
activeAlbum: null,

//NOTE AlbumDetailsPage

return: 
computed(()
)

//NOTE Navbar.vue

<li>
button class
new album
</li>

//NOTE ModalComponent.vue

this will be used to create new album

//NOTE import ModalComponent to App.vue

this will prevent it from throwing an error

//NOTE AlbumForm.vue

fill out form

v for select

option selected value=""

option v-for="category in catefories"

sectup(){
  return{
    categories: ['cats', 'dogs']
  }
}



//NOTE ModalComponent.vue

<template>
#header
</template>

<template>
#footer
</template>

//NOTE AlbumForm.vue

make form editable

//NOTE changing the route

router.push({name: 'Album', params: {albumId: album.id }})

//NOTE navbar.vue

<li> button v-if="route.name == 'Album' class archive album </li>

const route = useRoute()
return {
  route,
  account: computed(()=> AppState.activeAlbum)
  async archiveAlbum(){
    try {
      const wantsToArchive = await Pop.confirm

      if(!wantsToArchive){
      return
      }

      const albumId = route.params.albumId

      await albumsService.archiveAlbum
    } catch
  } error
}

route.name

//NOTE AlbumsService.js

async archiveAlbum(){
  const res = await api.delete(`api/albums/${albumId}`)
  logger.log('deleted album', res.data);
}

//NOTE when page reloads it reloads onMounted

//NOTE AlbumDetailsPage.vue

watchEffect(() => {
  getAlbumById(route.params.albumId)
})

//SECTION day 2 backend

//NOTE create picture schema

pictureSchema

export const pictureSchema = new Schema

//NOTE DbContext.js

register PictureSchema.js

//NOTE create PictureConroller

//NOTE create PictureService

//NOTE Picturecontroller 

export class PicturesController extends BaseController

constructor(){
  super('api/pictures'){
    this.router

    .use(Auth0Provider.getAuthorizedUserInfo)
    .post('', this.createPicture)
  }

  async createPicture(req, res, next){
    const pictureData = req.body
    pictureData.creatorId = req.userInfo.id

    const picture = await picturesService.createPicture(pictureData)

    return res.send
  }
}

//NOTE PicturesService{

async createPicture(pictureData){
  const picture = await dbContext.Pictures.create(pictureData)
  await picture.populate('creator', 'name picture')
  return picture
}
}

//NOTE PicturesController.js

.get('/:albumId/pictures', this.getPicturesByAlbumId)

async getPicturesByAlbumId (req, res, next){
  try {
    const albumId = req.params.albumId
    const pictures = await picturesService.getPicturesByAlbumId(albumId)
    return res.send(pictures)
  } catch (error)
}

//NOTE PicturesService.js

async getPicturesByAlbumId(albumId){

}

//SECTION front end side

//NOTE need to land on AlbumDetailsPage.vue

async function getPicturesByAlbumId(albumId){
  try {
const albumId = route.params.albumId
await getPicturesByAlbumId.picturesService

  } catch (error){
    logger.error(error)

  }
}

//NOTE PicturesService

class PicturesService {

async getPicturesByAlbumId(albumId)
}

export const picturesService = new PicturesService()

//NOTE back to AlbumDetailsPage.vue
finish writing function

//NOTE picturesService

async getPicturesByAlbumId(albumId){
  const res = await api.get(`api/albums${albumId}/pictures`)
  logger.log('[GETTING PICTURES BY ALBUM ID]', res.data);
}

//NOTE in picturesService

watchEffect (() =>){
  getAlbumById(route.params.albumId)
}

//NOTE router.js

path:'/albums/:albumId'
beforeEnter: authSettled

//NOTE picture.js

create model

//NOTE AppState.js

pictures: [],

//NOTE PicturesService.js

AppState.pictures = res.data.map(d => new Picture(d))

//NOTE AlbumDetailsPage.vue

return {
  album: computed(() => AppState.activeAlbum),
  pictures: computed(() => AppState.pictures)
}

//NOTE App.vue

import ModalComponent

<template #header>
Create Picture </template>

<template #body> Create Picture </template>

</Modal Component>

//NOTE AlbumDetailsPage.vue

add button to target modal

//NOTE App.vue

two Modal Componenents

give each ids

//NOTE PictureForm.vue

const editable = ref ({})
const route = useRoute()
return {
  editable {

  }
}

add "v-model editable.img"

form @submit.event="createPicture()"

async CreatePicture( {
  add const formData = editable.value
  logger.log(formdata, 'form data object')
  formData.albumId = route.params.albumId
  await picturesService.createPicture(formData)

  editable.value = {}
  Modal.getOrCreateInstance('#createPictureInstance').hide()
})


//NOTE picturesService

async createPicture(formData){
  const res = await api.post('api/pictures', formData)
  logger.log('[CREATING PICTURE]', res.data);

}

//NOTE PictureForm.vue

v-model="editable.imgUrl"

make changes to modal

//NOTE PicturesService

in async CreatePicture
const newPicture = new Picture(res.data)
Appstate.pictures.unshift(newPicture)

//NOTE albumForm.vue

button to open the modal

button :disabled="album.archived"

//SECTION backend

//NOTE PicturesServices (in server)

async createPicture(pictureData){
  const album = await albumsService.getAlbumById(pictureData.albumId)

  if(album.archived == true){
    throw new Forbidden(`${album.title} has been archived. You cannot create a picture in an archived album.`)
  }
}

//NOTE Collaborator.js model

export const CollaboraterSchema = new Schema ({
  albumId
})

//NOTE DbContext

add Collaborators Schema

//NOTE CollaboratorsController

//NOTE CollaboratorsService

//NOTE CollaboratorsController

export class CollaboratorsController extends BaseController

this.router

.use(Auth0Provider,getAuthorizedUserInfo)
.post('', this.createCollab)

async createCollab(req, res, next){
  try {
    const collabData = req.body
    collab.accountId = req.userInfo.id
    const collab = await collaboratorsService.createCollab(collabData)
    return res.send()
  }catch(error){
    next(error)
  }
}

//NOTE CollaboraborsService

async createCollab(collabdata){
  const album = await albumsService.getAlbumById(collabData.albumId)

  if (album.archived == true )
}

//NOTE CollaboratorsController

async getCollaboratorsByAlbumId (req, res, next){

}

//NOTE collaborators service

async getCollaboratersByAlbumId(albumId){
  const collaborators = 
}

//NOTE Account controller

async getMyCollabAlbums

//NOTE collaborators service

async getMyCollabAlbums(accountId){

}

//NOTE CollaboratorController

async delete Collab(req, res, next)

//NOTE Collaborates Service

async deleteCollab(collabId, userId){
  const 
}
//SECTION front end again

//NOTE AlbumDetailPage.vue

async function getCollaboratorsByAlbumId(){

}

//NOTE CollaboratorsService

async getCollaboratorByAlbumId(albumId){
  const res = await api.get(`api/albums/${albumId}/collaborators`)
  logger.log('[getting collabs]', res.data)
}

//NOTE AlbumDetailsPage.vue 

watchEffecct

ADD getCollaboratersByAlbumId

//NOTE Collaborator (model)

create model

//NOTE AppState

albumCollabs: []
save to AppState

//NOTE CollaboraterService.js

async getCollaboratorByAlbumId(albumId){
}

//NOTE AlbumDetailsPage.vue

return {
  collaborators: computed

  async becomeCollaborator(){
    async try{

      logger.log('become collab')
      const activeAlbumId = route.params.albumId

      const collabData = {albumId: activeAlbumId}
      await collaboratorService.becomeCollaborater(collabData)
      AppState.activeAlbum.memberCount++
  }
}
}

add collaborators to template

button @click="becomeCollaborator"

button @click="removeCollaborator"

//NOTE collaboratorService

async become Collaborator(collabData){
  const res = await api.

  AppState.albumCollabs.push(new Collaborator(res.data))
}
 async removeCollaborator()

return{
  isCollaborator: computed(() => {
    return AppState.albumCollabs.find(c => c.accountId == AppState.account.id)
  })
}

//NOTE collaboratorService

async removeCollabotor(){
  try {
    logger.log('removing collab')

    const collaboratorToRemove = AppState.albumCollabs.find(c => c.acccount.Id == AppState.account.id)

    await collaboratorsService.removeCollaborator
  }
}
//NOTE AlbumCard.vue
under {{ albumProp.membercount }}

//NOTE AuthService.js
AuthService.on

await = collaboratorsService.getMyCollabAlbums()

//NOTE Collaborators Service

async getMyCollabAlbums(){
  try {
  const res = await api.get('account/collaborators')
  logger.log('[get my albums]', res.data)
    AppState.myCollabs = res.data.map 
  }
}

//NOTE collaborator model

add this.album = data.album

//NOTE HomePage.vue

<AlbumCard :albumProp="c.album" />
this is called "albumProp" because that is what we named it in ALBUMCARD

return {
  myCollabs: 
}

//NOTE AlbumCard change to "album" to Object

//NOTE HomePage.vue

setup(){
  const filterBy = ref('')
}

return {
  filterBy,
  albums: computed(() => {
    if(filterBy.value = ""){
      return AppState.albums
    } else {
      return AppState.albums.filter(a => a.category == filterBy.value)
    }
  }), 
}
