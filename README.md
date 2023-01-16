# lab4_Ping-pong
# lab4
## Цель работы
Разработать и реализовать игру пинг-понг. Для отрисовки вида используется canvas. Игра завершается при достижении нужного счёта одним из игроков.

## Ход работы

### 1) Пользовательского интерфейса

![1](https://user-images.githubusercontent.com/116270845/212758452-d131b114-e838-44d8-936a-18ae95419b72.png)


### 2) Описание пользовательских сценариев работы
- Пользователь заходит на сайт и попадает на главную страницу. 

- У пользователя есть возможность сыграть в игру пинг-понг против компьютера. 

- Игра проходит из 5 партий, до трех побед. Кто первый выиграет три партии, каждая из которых до 11 очков, тот побеждает.

- Для того, чтобы играть, нужно попадать ракеткой в мячик. Если мячик пересекает вашу границу, а вы по нему не попадаете ракеткой, то очко присуждается сопернику и наоборот. 

- Мячик с каждым касанием ракетки ускоряется на 0,1с. Каждое новое очко ускорение сбрасывается до начального.

- В конце игры программа выдаст, кто победил, после чего можно перезагрузить сайт и сыграть повторно.
### 3) Описание алгоритмов

**1) Розыгрыш очка в партии:**

![2](https://user-images.githubusercontent.com/116270845/212758620-8b682511-eed7-4bf7-848a-0bbb5f0da860.png)


**2) Алгоритм опрделеления победы в партии:**

![3](https://user-images.githubusercontent.com/116270845/212758702-f68e6980-1988-4987-acdd-d88e471c6bd2.png)


**3) Алгоритм опрделеления победы в игре:**

![4](https://user-images.githubusercontent.com/116270845/212758765-ab4a6b45-d605-4f1b-8eaa-b507c70458ec.png)


### 4) Значимые фрагменты кода

Столкновение мяча с ракеткой: 
```sh
function touch(balls,player){ //столкновение с ракетой
    //текущее расположени ракетки и мяча
    player.top = player.y;
    player.bottom = player.y + player.height;
    player.left = player.x;
    player.right = player.x + player.width;

    balls.top = balls.y - balls.radius;
    balls.bottom = balls.y + balls.radius;
    balls.left = balls.x - balls.radius;
    balls.right = balls.x + balls.radius;

    return player.left < balls.right && player.top < balls.bottom && player.right > balls.left && player.bottom > balls.top;
}
```

Определение победителя:
```sh
function Rules(){ 
	if (user.score == 11) {
		user.score = 0;
		computer.score = 0;
		user.match += 1
	}
	else if (computer.score == 11) {
		user.score = 0;
		computer.score = 0;
		computer.match += 1
	}
    if (user.match < 3 && computer.match < 3){
        update();
        Draw();
    } else if (computer.match > user.match){
        alert("Win computer!");
    } else {
        alert("Win User!");
    }
}
```
## Вывод
В ходе выполнения лабораторной работы была игра пинг-понг с возможностью игры с компьютером.
