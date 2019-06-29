# Ludo API

API for a game of Ludo

## How to use

### Library

You need the following package to use this API.

`npm install @aspnet/signalr@next`

### Connecting

The API is live on `ludo.azurewebsites.net`

Connect on subpath `/game`

### Events

#### Lobbies

- invoke `lobby:create` with `lobbyName` to create a new lobby
- invoke `lobby:join` with `lobbyName` to join a created lobby
- invoke `lobby:leave` to leave your currently joined lobby
- invoke `lobby:get-players` with `lobbyName` to get a event back called `lobby-players` with the players in said lobby

When you're in a lobby you can get events for said lobby

- on `lobby:player-join` it returns the user identifier for the player that joined
- on `lobby:player-leave` it returns the user identifier for the player that left
- on `lobby:players` (has to be invoked via `lobby:get-players`) it returns a list of player's details

#### Game

- invoke `game:start` as admin (those who created the lobby) to start the game
- invoke `game:roll-die` to roll your dice if it's your turn
- invoke `game:advance` with `pieceIndex` to move the piece

When you're in a started game you can get events for that game

- on `game:started` the game has started
- on `game:die-roll` a player has rolled the dice, it returns the player who rolled the die and the amount it rolled
- on `game:advanced` a player has advanced his piece, it returns the player who advanced his piece and the index of said piece
- on `game:next-turn` the next player or turn starts, it returns the player whose turn it is and the turn type (roll or advance)