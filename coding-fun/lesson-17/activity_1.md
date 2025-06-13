### @codeStart players set @s makecode 0
### @codeStop players set @s makecode 1

### @hideIteration true 
### @explicitHints 1


# Посади семена!

## Step 1
Сначала взаимодействуй с Агентом, чтобы открыть его инвентарь и дать ему семена. Затем создай команду ``||player: при команде чата||`` и добавь ``||agent: вскопать впереди||`` и ``||agent: посадить впереди||``.

```ghost
player.onChat("plantSeed", function () {
    agent.till(FORWARD)
    agent.place(FORWARD)
})
```
