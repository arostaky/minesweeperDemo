# minesweeperdemo

> A Vue.js project

Current Features:

* When a cell with no adjacent mines is revealed, all adjacent squares will be revealed (and repeat)
* Ability to 'flag' a cell with a question mark or red flag
* Alert when game is over
* Ability to select the game parameters: number of rows, columns, and mines

Missing Features:

* Persistence. Not to lose the game if browser is closed
* Time tracking
* Ability to start a new game and preserve/resume the old ones
* Ability to support multiple users/accounts
* Design and implement an API for the game
* Nice user experience

I started this project with a couple of features for the main screen, I used the logic from 'npm minesweeper' for the game, the click event won't work on the tiles yet. This is an WIP project.


## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
