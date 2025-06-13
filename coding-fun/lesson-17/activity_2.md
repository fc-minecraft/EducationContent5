### @codeStart players set @s makecode 0
### @codeStop players set @s makecode 1

### @hideIteration true 
### @explicitHints 1


# Посадка!

## Шаг 1
Мы создали для тебя функцию **plantSeed**. Это просто код, который ты использовал для предыдущего задания. Теперь перетащи команду ``||player: при команде чата||`` в рабочую область и назови её **запуск**. Добавь цикл ``||loops: повтор||``, затем нажми на раздел **Расширенные** и выбери **Функции**, и перетащи функцию ``||function: вызвать plantSeed||`` в свой цикл. Посчитай, сколько раз Агенту нужно повторить функцию **посадитьСемя**.

### ~ tutorialHint
Функции находятся в разделе **Расширенные**. Также хорошей практикой является оставлять заметки о написанном коде, как мы оставили для тебя о функциях.


```template
/**
 * Функция позволяет легко повторно использовать код.
 */
function plantSeed () {
    agent.till(FORWARD)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}
```

```ghost
player.onChat("plantSection", function () {
    for (let index = 0; index < 11; index++) {
        plantSeed()
    }
    agent.move(FORWARD, 1)
})
```
