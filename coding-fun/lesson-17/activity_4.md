### @codeStart players set @s makecode 0
### @codeStop players set @s makecode 1

### @hideIteration true 
### @explicitHints 1


# Свекла!

## Шаг 1
Тебе предоставлены три функции: ``||functions: посадитьСемена||``, ``||functions: посадитьСекцию||`` и ``||functions: проверитьПоворот||``. Создай код, который засадит все поле 11 на 11 блоков.



```template
/**
 * Мы вызываем функцию внутри функции
 */
function посадитьСекцию () {
    for (let index = 0; index < 11; index++) {
        посадитьСемена()
    }
    agent.move(FORWARD, 1)
}
 /**
 * Код был изменён, чтобы не сажать семена, если под Агентом нет блока.
 */
function посадитьСемена () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}
function проверитьПоворот () {
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(LEFT_TURN)
    }
}

```


```ghost
player.onChat("plant", function () {
    while (agent.inspect(AgentInspection.Block, DOWN) != GOLD_BLOCK) {
        посадитьСекцию()
        проверитьПоворот()
    }
    if (agent.detect(AgentDetection.Block, FORWARD)) {
	
    }

})

function проверитьПоворот () {
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(LEFT_TURN)
    }
}

```
