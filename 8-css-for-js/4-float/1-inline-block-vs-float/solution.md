Разница колоссальная. 

В первую очередь она в том, что `inline-block` продолжают участвовать в потоке, а `float` -- нет.

Чтобы её ощутить, достаточно задать себе следующие вопросы:

<ol>
<li>Что произойдёт, если контейнеру `UL` поставить рамку `border` -- в первом и во втором случае?</li>
<li>Что будет, если элементы `LI` различаются по размеру? Будут ли они корректно перенесены на новую строку в обоих случаях?</li>
<li>Как будут вести себя блоки, находящиеся под галереей?</ul>
</ol>

Попробуйте сами на них ответить.

Затем читайте дальше.


<dl>
<dt>Что будет, если контейнеру `UL` поставить рамку `border`?</dt>
<dd>Контейнер не выделяет пространство под `float`. А больше там ничего нет. В результате он просто сожмётся в одну линию сверху.

Попробуйте сами, добавьте рамку в [edit src="solution"]песочнице[/edit].

А в случае с `inline-block` всё будет хорошо, т.к. элементы остаются в потоке.
</dd>
<dt>Что будет, если элементы `LI` различаются по размеру? Будут ли они корректно перенесены на новую строку в обоих случаях?</dt>
<dd>При `float:left` элементы двигаются направо до тех пор, пока не наткнутся на границу внешнего блока (с учётом `padding`) или на другой `float`-элемент. 

Может получиться вот так:

<img src="gallery-float-diffsize.png">

Вы можете увидеть это, открыв демо-галерею в отдельном окне и изменяя его размер:

[demo src="gallery-float-diffsize"]

При использовании `inline-block` таких странностей не будет, блоки перенесутся корректно на новую строку. И, кроме того, можно выровнять элементы по высоте при помощи `li { vertical-align:middle }`: 

[iframe height=500 src="gallery-inline-block" link edit]
</dd>
<dt>Как будут вести себя блоки, находящиеся под галереей?</dt>
<dd>В случае с `float` нужно добавить дополнительную очистку с `clear`, чтобы поведение было идентично обычному блоку. 

Иначе блоки, находящиеся под галереей, вполне могут "заехать" по вертикали на территорию галереи.</dd>
</dl>