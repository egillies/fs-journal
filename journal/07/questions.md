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
  category: {type: String, enum: ['cats', 'dogs', 'games', 'gachamon', 'misc'], required: true, default: 'misc'},
  creatorId: {type: Schmea.Types.ObjectId, required: true, ref: 'Account'}
})

//NOTE Dbcontext.js

Albums = mongoose.model

//NOTE AlbumsController.js

//NOTE AlbumsServices.js

//NOTE AlbumsController.js

import BaseController

CREATE FUNCTIONS IN POSTMAN ORDER 

export class AlbumsController extends BaseController {
  constructor(){
    super('api/albums')
    this.router
    .use(Auth0Provider.getAuthorizedUserInfo)
    .post('', this.createAlbum)
  }

  async createAlbum(req, res, next){
    try {
      const albumData = req.body
      albumData.creatorId = req.userInfo.id
      const album = await AlbumsService.createAlbum(albumData)
    } catch (error){
      next(error)
    } 
  }
}

//NOTE albumServices.js

class AlbumsService {
  async createAlbum(albumData){
    const newAlbum = await dbContext.Albums.create(albumData)
    return newAlbum
  }

}

export const albumsService = new AlbumsService()
