# LaTEX

## Что такое LaTEX?
LaTEX представляет собой инструмент для создания профессиональных документов.
Этот инструмент используется повсеместно для создания научных документов, написания книг,
а также многих других форм публикаций. Он позволяет не только создавать красиво оформленные документы,
но также дает пользователям возможность очень быстро реализовывать такие сложные элементы печатного набора,
как математические выражения, таблицы, ссылки и библиографии, получая согласованную разметку по всем разделам.

## Создание простого документа
```sh
\documentclass{article} 

\begin{document}
Первый документ

\end{document}
```

Первая строка объявляет тип документа, называемый классом. 
Класс определяет общее представление документа.
Для разных типов документов требуются разные классы.

**\documentclass{article}** создает документ класса "article".После этого мы пишем содержание документа, 
заключенное в теги **\begin{document}** и **\end{document}**, представляющие его тело. 
Внутри тела документа можно писать текст и при желании вносить в него изменения.

## Классы документов LaTEX
### Стандартные классы документа:
* *Article* - класс для подготовки научных статей, презентаций, коротких сообщений, программной документации и тп.
* *Report* - поддерживает главы и может использоваться для небольших книг, диссертаций и т.п.
* *Book* - класс для подготовки книг
* *Beamer* - класс для создания презентаций.(Для простых слайдов существует менее функциональный класс *slides*)
 
 ## Дополнительные параметры класса
 Каждый класс поддерживает ряд дополнительных необязательных параметров:
 ```sh
 documentclass[опции]{класс-документа}
  ```
 ### Основные опции:
 * *a4paper, letterpaper, a5paper, b5paper, executivepaper, legalpaper* - размер страницы, по умолчанию равен *letterpaper*
 * *titlepage, notitlepage* - указывает создавать или нет титульную страницу.
 * *10pt, 11pt, 12pt* - размер основного шрифта, по умолчанию размер равен *10pt*.
 * *onecolumn, twocolumn* - пределяет форматирование текста в одну или две колонки.
 
## Дополнительные возможности форматирования документа
Дополнительные возможности форматирования документа добавляются с помощью пакетов командой:
```sh
\usepackage[опции]{пакет}
  ```
Существует сотни пакетов и привести описание их всех практически невозможно.
Пакеты помогают работать с разными языками, математическими формулами, таблицами, изображениями и тд.
```sh
%Russian-specific packages
\usepackage[T2A]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}
```

```sh
%Mathematical tools package
\usepackage{mathtools}
```

```sh
%Table package
\usepackage[table]{xcolor}
```
## Работа с таблицами
### Основные средства создания таблиц
Среда **tabular** - это самый простой способ создать таблицу в LaTeX и не требует каких-либо других пакетов.
```sh
\begin{tabular}{c c c}                             Пример простой таблицы:
    1 & 2 & 3 \\                                           1 2 3
    4 & 5 & 6 \\                                           4 5 6
    7 & 8 & 9 \\                                           7 8 9
\end{tabular}
```

Параметр **{c c c}** в примере называется **спецификацией таблицы** и сообщает LaTeX, сколько столбцов есть и как они должны быть отформатированы.

#### Возможные значения параметра:
| Символ | Что означает |
| ------ | ------------ |
| c | Выравнивание по центру|
| l | Выравнивание по левому краю|
| r | Выравнивание по правому краю|
| p {'width'} | Столбец с определенной шириной|

Клетки разделены символом **&**. Строка заканчивается двумя обратными косыми чертами.
Горизонтальные линии можно вставить с помощью команды **\hline**. Разделение столбцов можно добавить при помощи вертикальной черты в параметре, например **{|c|c|c|}**.

Таблицу с заголовками столбцов, охватывающую несколько столбцов, можно создать с помощью команды **\multicolumn{cols}{pos}{text}**.
```sh
\begin{center}
\begin{tabular}{|c|c|c|c|}
\hline
&\multicolumn{3}{|c|}{TITLE}\\
\cline{2-4}
SMTH & SMTH & SMTH & SMTH\\
\hline
SMTH& 11 & 21 & 13\\
SMTH& 21 & 31 &41\\
\hline
\end{tabular}
\end{center}
\end{document}
```

![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/table.png)


Команда **\multicolumn** имеет три обязательных аргумента: первый аргумент указывает количество столбцов, по которым распространяется заголовок; второй аргумент указывает положение заголовка **(l,c,r)** ; а третий аргумент - текст заголовка. Команда **\cline{2-4}** указывает начальный столбец (здесь, 2) и конечный столбец (здесь, 4), над которым должна быть нарисована строка.


### Раскрашивание таблиц 
Существует несколько способов окраски таблиц:
* *Раскрашивание строк*
* *Раскрашивание столбцов*
* *Раскрашивание линий*
* *Раскрашивание ячеек*

#### Раскрашивание строк
Для окраски строк используется команда **\rowcolor**, a также пакет **\usepackage[table]{xcolor}**

```sh
\usepackage[table]{xcolor}

\begin{tabular}{ | c | c | c | }
  \rowcolor{green}
  A & B & C \\
  \rowcolor{red}
  D & E & F \\
  G & H & I \\
  \rowcolor{blue}
  J & K & L
 \end{tabular}
```
![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/rowColor.png)

### Рвскрашивание столбцов
Если мы хотим окрашивать столбцы вместо строк, мы можем сделать это с помощью команды > **{\columncolor {< color >}}** в точке перед установкой параметров выравнивания. 
 
 ```sh
\usepackage[table]{xcolor}

\begin{tabular}{cc >{\columncolor{green!20}}c}
    A & B & C \\
    D & E & F \\
    G & H & I \\
\end{tabular}
```
![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/columnColor.png)

### Раскрашивание границ таблицы
Для раскрашивания линий, которые ограничивают нашу таблицу используется команда **\arrayrulecolor**.

```sh
\usepackage[table]{xcolor}
\arrayrulecolor{blue}

\begin{tabular}{ | l | l | l | }
  \hline
  A & B & C \\
  \hline
  D & E & F\\
  \hline
  G & H & I \\
  \hline
\end{tabular}
```
![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/lineColor.png)


### Раскрашивание ячеек
Для добавления цвета только в одну ячейку используется команда **\cellcolor {< color >}**, которую необходимо поместить в ячейку.

```sh
\usepackage[table]{xcolor}

\begin{tabular}{|c|c|}
    \hline
    \cellcolor{purple!30}A & \cellcolor{pink!60}B \\
    \hline
    \cellcolor{red!40}C & \cellcolor{orange!50}D \\
    \hline
\end{tabular}
```
![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/cellColor.png)


## Работа со списками
Простой список задается окружением **{itemize}**. Каждый элемент списка задается командой **\item** Текст.
```sh
begin{itemize}
	\item The first item 
	\item The second item
	\item The third item
\end{itemize}
```
![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/unmarkedList.png)

Кроме маркированного списка, можно формировать списки, элементы которых пронумерованы. Нумерация производится автоматически. Для этого служит окружение **{enumerate}**. Элементы нумерованного списка могут быть также вложенными, причем допускается до 5 уровней вложенности.
```sh
\begin{enumerate}
	\item The first item
	\begin{enumerate}
		\item Nested item 1
		\item Nested item 2
		\begin{enumerate}
		\item Nested item 1
		\item Nested item 2
	\end{enumerate}\begin{enumerate}
		\item Nested item 1
		\item Nested item 2
		\begin{enumerate}
		\item Nested item 1
		\item Nested item 2
	\end{enumerate}
	\end{enumerate}
	\end{enumerate}
		\item The second item
		\item The third etc \ldots
\end{enumerate}
```
![](https://github.com/MorozovaMilena/Latex_practice/blob/main/ImagesForMdFile/nestedItem.png)

### Работа с математическими формулами
Для работы со сложными формулами в Латехе существует пакет **\usepackage{mathtools}**.
Математических символов в Латехе огромное количество, для некоторых существуют специальные команды, а к другим можно получить доступ прямо с клавиатуры.
Большинство математических символов Латеха можно найти тут : [https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols]()

#### Реализация формул в латехе
* Формулы в тексте идут в **$ formula $** и они меньше по размеру, чем все остальные.
* Формулы, выделенные из текста отдельной строкой и по центру, идут в **$$ formula $$** , с нумерацией, задающейся вручную - **$$ formula \eqno( number ) $$** (тут номер будет стоять справа, для выравнивая по левой стороне используется **\leqno** ).
* Для выравния формул в нужном месте используется под-окружение **split** . Автоматически оно ставит один общий номер на весь набор строк.
```sh
\begin{equation}
  \begin{split}
    formula & 1 \\                                   Выравнивание в данном случае идет по символу &.
    formula & 2
  \end{split}
\end{equation}
```
* Для выравнивания формул по столбикам используется окружение align.
```sh
\begin{equation}
  \begin{align}
   formula & 1    &   formula & 2 \notag \\
   formula & 3    &   formula & 4
\end{align}

\end{equation}
```
### Примеры

