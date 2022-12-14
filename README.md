# homework6

##1. Что за единица измерения - `fr`?
`fr` - (от. fractional unit) так называемая единица гибкости, которая обозначает часть свободного пространства. Их используют, чтобы не высчитывать ширину элемента самостоятельно, а делигировать расчеты "машине".

##2. Как можно задать грид с 5 колонками шириной по 20%? Минимум 2 способа.
  display: grid;
  grid-template-columns: repeat(5, 20%); 
  grid-template-columns: repeat(5, 1fr); 
  grid-template-columns: 20% 20% 20% 20% 20%;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;

##3. Самостоятельно разберитесь, что такое `auto-fill` и `auto-fit` ?
`auto-fill` и `auto-fit` используются (вместе с функцией repeat()) как значения при указании ширины колонок в CSS Grid. И `auto-fill`, и `auto-fit` заполняют контейнер колонками заданной ширины, при чем таким количеством колонок, сколько поместится в контейнер. Отличие между ними в том, что происходит со свободным пространством, которое может образоваться, если размер контейнера не кратен размеру колонки. Так:
- `auto-fill` - оставляет это свободное пространство (пробел) в конце;
- `auto-fit` - распределяет оставшееся пространство между созданными колонками.

##4. Как сделать такую табличку? Параметры: первая колонка шириной 100 пикселей, вторая 30%. Первая строчка высотой 200 пикселей, вторая строчка 100 пикселей.

  display: grid;
  grid-template-columns: 100px 30% 1fr; 
  grid-template-rows: 200px 100px;
  gap: 10px;
    
##5. Как сделать такое выравнивание в грид-контейнере? 
  justify-content: space-between;
    
##6. Что такое и как задается *grid area*?
grid area - это простанство внутри  grid-контейнера, включающая одну и более grid-ячеек. Оно задается четырьмя параметрами, а grid-area - это сокращенным свойство, чтобы описать в одну строку grid-row-start, grid-column-start, grid-row-end и grid-column-end

##7. Приведите пример использования `grid-template-areas` (не копированием из этого урока 😉)
  display: grid;
  grid-template-rows: 70px 350px 200px 150px 100px;
  grid-template-areas: 
  "hd hd hd hd hd hd hd hd"
  "sb sb sec sec sec sec sec sec"
  "sb sb art1 art1 art1 art2 art2 art2"
  "n1 n1 n2 n2 n3 n3 n4 n4"
  "ft ft ft ft ft ft ft ft";

##8. Каким свойством можно задать такое поведение элементов?
Полагаю, для этой цели подойдет grid-template-columns: repeat(auto-fit, minmax(Х, 1fr));
Где вместо Х надо задать минимальный размер колонки, достигнув которого начнется перестроение.
    
##9. Самостоятельно разберитесь, как работают именованные линии? Есть ли какие-то рекомендованные правила наименований? Если да, то какие?

Можно выделить следующие рекомендации именования линий:
- использовать [], если именуется линия при описании трека в grid-template(-columns, -rows);
- задавая имя, нельзя использовать span;
- чтобы назвать начальные и конечные линии лучше использовать приставки -start и -end соответственно;
- одной линии можно присвоить несколько имен. Чтобы их задать, все имена перечисляют через пробел в [].

p.s. Очень странно, когда после задания, сформулированного через "самостоятельно разберитесь..." стоит вопрос. Может стоит поправить)

##10. Как проще всего задать 12 одинаковых по ширине колонок?
grid-template-columns: repeat(12, 1fr);