# FiveM Simon Says -minigame

I've implemented an old JQuery exercise from school to FiveM. The JQuery used in this mini game is from this [tutorial](https://www.danpurdy.co.uk/tutorial/simon-says-game-in-jquery-tutorial/).

## How to use

This resource is exposing a single client event handler which you can trigger from your other resources. The exposed client event takes 3 parameters:


```
TriggerEvent('theheka:startSimonGame', targetLvl, speed, outputEvent)
```

`targetLvl` - the level that the player has to reach to be successfully passed the game. 

`speed` - Defaults to `0.5` if nil value is given. Allowed values are:
```
0.25 - Insane
0.5 - Hard  [DEFAULT]
1 - Normal
2 - Easy
```

`outputEvent` - a client event name that will be triggered when the game has been finished. 


### Example:
```
# Client

RegisterCommand("simonsays", function(source, args, rawCommand)
  TriggerEvent('theheka:startSimonGame', 5, 0.5, 'theheka:simonResult')
end, false)

AddEventHandler('theheka:simonResult', function (success)
  print(success)
end)
```
The following snippet will register a command `/simonsays`. This command will trigger an event that will start the simon says -mini game. Target level is set to 5 and the speed is set to `0.5`. After every game a client event `theheka:simonResult` will be triggered and boolean value returned. If player reaches target level (5) `true` value will be returned otherwise the value is `false`.

Link to demo: [GIF](https://i.gyazo.com/053b3cac5cca223e55e741b9c419b63d.mp4)

## Install
Download repository and copy-paste `./simon_minigame` to your `resources/` -directory. Make sure to start/ensure simon_minigame in your server.cfg -file
