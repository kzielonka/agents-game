# Agents game

It is implementation of agents game prepared for Droids on Rorids Web Team architectural showcase.
This implementation is one which I have called mudualr-CQRS.
It will be done in JavaScript Nest.js with some simple NoSQL Database, probably Redis.

# Planned endpoints
## POST /api/games
Request:
```
{
  name: "WGM game",
}
```
Response:
```
{
  gameId: "game-id",
  joinCode: "abcd1234",
}
```


### POST /api/games/:id/join
Request:
```
{
  joinCode: "abcd1234"
}
```
Response (sccess):
status: 204
Response (failure):
status: 400
```
{
  type: "http://example.com/invalid-code"
}
```

### GET /api/games/:id
Response (game not started yet):
```
{
  state: "waiting-for-start",
  yourRole: "unknown-until-games-is-not-started",
  players: [
    { id: "player-1-id", name: "Borsuk" },
    { id: "player-2-id", name: "Beatka" },
  ],
  images: [],
}
```
Response (game started - civilan):
```
{
  state: "started",
  yarRole: "civilan",
  players: [
    { id: "player-1-id", name: "Borsuk" },
    { id: "player-2-id", name: "Beatka" },
  ],
  images: [{ url: "...", selected: false }, ...]
}
```
Response (game started - agent):
```
{
  state: "started",
  yarRole: "agent",
  players: [
    { id: "player-1-id", name: "Borsuk" },
    { id: "player-2-id", name: "Beatka" },
  ],
  images: [{ url: "...", selected: false }, ...]
}
```
