### @codeStart players set @s makecode 0
### @codeStop players set @s makecode 1

### @hideIteration true 
### @explicitHints 1



# Посадка свеклы!

## Шаг 1

Для тебя предоставлены две функции: **посадитьСемя** и **посадитьСекцию**. Создай новую команду ``||player: при команде чата||`` и вызови ``||functions: вызвать plantSection||`` внутри неё. Добавь оператор ``||logic: если||``, который проверяет, ``||agent: если агент осматривает блок вниз||``.
Если блок внизу — это ``||blocks: лазурит||``, то агенту нужно ``||agent: повернуть направо||``, ``||agent: двигаться вперед||`` и ``||agent: повернуть направо||``.
``||logic: Иначе||``, если ``||agent: агент осматривает блок вниз||`` и это ``||blocks: кварцевый блок||``, то агенту нужно ``||agent: повернуть налево||``, ``||agent: двигаться вперед||`` и ``||agent: повернуть налево||``.
Наконец, вызови ``||functions: plantSection||``.

#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    plantSection()
})
```

```template
/**
 * Мы вызываем функцию внутри функции
 */
function plantSection () {
    for (let index = 0; index < 11; index++) {
        plantSeed()
    }
    agent.move(FORWARD, 1)
}
 /**
 * Код был изменен, чтобы не сажать семена, если под Агентом нет блока.
 */
function plantSeed () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    if (agent.detect(AgentDetection.Block, DOWN)) {
        agent.place(DOWN)
    }
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
    plantSection()
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
function plantSection () {
    for (let index = 0; index < 11; index++) {
        plantSeed()
    }
    agent.move(FORWARD, 1)
}
 /**
 * Код был изменен, чтобы не сажать семена, если под Агентом нет блока.
 */
function plantSeed () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    if (agent.detect(AgentDetection.Block, DOWN)) {
        agent.place(DOWN)
    }
}

/**
*  Тебе нужно проверить, стоит ли Агент на лазуритовом блоке, чтобы повернуть направо, если на кварцевом — налево.
*/
```

## Шаг 3
Дважды нажми на символы **+** блока ``||logic: если||``. Нажми на **-** , чтобы удалить блок **иначе**. Добавь блок ``||logic: " " = " "||`` в **пустое** пространство блока ``||logic: иначе если||``. Если ``||agent: агент осматривает блок вниз||`` **равно (=)** ``||blocks: кварцевому блоку||``, то агенту нужно ``||agent: повернуть налево||``, ``||agent: двигаться вперед||`` и ``||agent: повернуть налево||``.

#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    plantSection()
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
function plantSection () {
    for (let index = 0; index < 11; index++) {
        plantSeed()
    }
    agent.move(FORWARD, 1)
}
 /**
 * The code was modified to not place seeds if there's no block under the Agent.
 */
function plantSeed () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    if (agent.detect(AgentDetection.Block, DOWN)) {
        agent.place(DOWN)
    }
}

/**
* You need to check if the Agent is stepping on a lapis block turn right, if quartz turn left.
*/
```

## Step 4
Наконец, добавь ещё один вызов ``||functions: plantSection||`` внутри команды ``||player: при команде чата||`` за пределами оператора ``||logic: если||``.

#### ~ tutorialhint
``` blocks
player.onChat("run", function () {
    plantSection()
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else if (agent.inspect(AgentInspection.Block, DOWN) == BLOCK_OF_QUARTZ) {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(LEFT_TURN)
    }
    plantSection()
})
```

```template
/**
 * Мы вызываем функцию внутри функции
 */
function plantSection () {
    for (let index = 0; index < 11; index++) {
        plantSeed()
    }
    agent.move(FORWARD, 1)
}
 /**
 * Код был изменен, чтобы не сажать семена, если под Агентом нет блока.
 */
function plantSeed () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    if (agent.detect(AgentDetection.Block, DOWN)) {
        agent.place(DOWN)
    }
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
    plantSection()
    if (agent.inspect(AgentInspection.Block, DOWN) == LAPIS_LAZULI_BLOCK) {
        agent.turn(RIGHT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    } else if (agent.inspect(AgentInspection.Block, DOWN) == BLOCK_OF_QUARTZ) {
        agent.turn(LEFT_TURN)
        agent.move(FORWARD, 1)
        agent.turn(RIGHT_TURN)
    }
    plantSection()
})
```

