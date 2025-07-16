### @codeStart players set @s makecode 0
### @codeStop players set @s makecode 1

### @hideIteration true 
### @explicitHints 1


# Посади семена!

## Step 1
Сначала открой инвентарь Агента и дай ему семена. Затем используй команду ``||player: при команде чата||`` и добавь ``||agent: вскопать впереди||`` и ``||agent: посадить впереди||``.

```ghost
player.onChat("посадить", function () {
    agent.till(FORWARD)
    agent.place(FORWARD)
})
```
