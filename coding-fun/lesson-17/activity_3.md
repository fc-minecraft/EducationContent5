### @codeStart players set @s makecode 0
### @codeStop players set @s makecode 1

### @hideIteration true 
### @explicitHints 1



# Посадка свеклы!

## Шаг 1

Для тебя предоставлены две функции: **посадитьСемена** и **посадитьСекцию**. Создай новую команду ``||player: при команде чата||`` и вызови ``||functions: вызвать посадитьСекцию||`` внутри неё.


#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    plantSection()
})
```

```ghost
player.say(":)")
```

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
 * Код был изменен, чтобы не сажать семена, если под Агентом нет блока.
 */
function посадитьСемена () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}

/**
* Тебе нужно проверить, стоит ли Агент на лазуритовом блоке, чтобы повернуть направо, если на кварцевом — налево.
*/
```
## Шаг 2
Добавь оператор ``||logic: если||`` в команду ``||player: при команде чата||``. Внутри блока **истина** оператора ``||logic: если||`` добавь блок ``||logic: " " = " "||``. Если ``||agent: агент осматривает блок вниз||`` **равно (=)** ``||blocks: лазуритовому блоку||``, то агенту нужно ``||agent: повернуть направо||``, ``||agent: двигаться вперед||`` и ``||agent: повернуть направо||``.

#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    посадитьСекцию()
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    }

})
```

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
 * Код был изменен, чтобы не сажать семена, если под Агентом нет блока.
 */
function посадитьСемена () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}

/**
*  Тебе нужно проверить, стоит ли Агент на лазуритовом блоке, чтобы повернуть направо, если на кварцевом — налево.
*/
```

```ghost
player.say(":)")
```

## Шаг 3
Дважды нажми на символы **+** блока ``||logic: если||``. Нажми на **-** , чтобы удалить блок **иначе**. Добавь блок ``||logic: " " = " "||`` в **пустое** пространство блока ``||logic: иначе если||``. Если ``||agent: агент осматривает блок вниз||`` **равно (=)** ``||blocks: кварцевому блоку||``, то агенту нужно ``||agent: повернуть налево||``, ``||agent: двигаться вперед||`` и ``||agent: повернуть налево||``.

#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    посадитьСекцию()
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else if (agent.inspect(AgentInspection.Block, DOWN) == BLOCK_OF_QUARTZ) {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(LEFT_TURN)
    }

})
```

```template
/**
 * We are calling a function inside a function
 */
function посадитьСекцию () {
    for (let index = 0; index < 11; index++) {
        посадитьСемена()
    }
    agent.move(FORWARD, 1)
}
 /**
 * The code was modified to not place seeds if there's no block under the Agent.
 */
function посадитьСемена () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}

/**
* You need to check if the Agent is stepping on a lapis block turn right, if quartz turn left.
*/
```

```ghost
player.say(":)")
```

## Step 4
Наконец, добавь ещё один вызов ``||functions: посадитьСекцию||`` внутри команды ``||player: при команде чата||`` за пределами оператора ``||logic: если||``.

#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    посадитьСекцию()
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else if (agent.inspect(AgentInspection.Block, DOWN) == BLOCK_OF_QUARTZ) {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(LEFT_TURN)
    }
    посадитьСекцию()
})
```

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
 * Код был изменен, чтобы не сажать семена, если под Агентом нет блока.
 */
function посадитьСемена () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}

/**
* Тебе нужно проверить, на каком блоке стоит твой Агент. Если на лазуритовом блоке, повернуть направо, если на кварцевом — налево.
*/

/**
* Ты можешь нажать на кнопку + блока Если, чтобы добавить Иначе
*/

```

```ghost
player.onChat("turn", function () {
    посадитьСекцию()
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else if (agent.inspect(AgentInspection.Block, DOWN) == BLOCK_OF_QUARTZ) {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    }
    посадитьСекцию()
})
player.say(":)")
```

