# asyncio_nd
Learning Asyncio 
<https://www.youtube.com/watch?v=h-EFkclgCc8>

В продолжение беседы о конкурентости и параллельности в Python, пришла пора посмотреть на модный молодежный asyncio

Асинхронное выполнение подходит для IO-bound задач, работает ровно 1 поток

Плюсы:
+ скорость и экономия времени, вместо x + y + z =  max(x, y, z)
+ управляемость
+ меньше потребление ресурсов (в сравнении с потоками)

Минусы:
 - "умирает" из-за одного блокирующего вызова (!)
- не безразмерный, нужно понимать, что корутины не бесплатные

важные принципы:
1) корутина работает как генератор
2) async - явный флаг, что данная функция является асинхронной (корутиной)
3) await - явный флаг, что в это месте функция встает на паузу и дает работать другим, пока ждет свои данные
4) event loop - цикл событий, механизм, который отвечает за планирование и запуск корутин. Можно представить как список/очередь, из которого в вечном цикле достаются и запускаются корутины

Частые ошибки:
- не использование await внутри корутины
- создание корутины, но использование ее, как функции
- использование внутри корутин синхронного(блокирующего) кода, в том числе IO
