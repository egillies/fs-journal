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
  foreignField: _id,
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
