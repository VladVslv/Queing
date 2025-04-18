# Васильев Владислав БПИ217

# Решение задачи №1

### а
Обозначения:
- $L$ — среднее число посетителей,
- $\lambda$ — средняя интенсивность потока входа (2 посетителя в минуту),
- $W$ — среднее время пребывания посетителя (12 минут).

Формула Литтла:
$L = \lambda \cdot W$ => $L = 2 \cdot 12 = 24$

Ответ: 24 человека

### б
Обозначения:
- $\lambda = 1/12$ — интенсивность выхода (т.к. среднее пребывание 12 минут),
- $t = 60$ — время, за которое необходимо выйти (60 минут).

Если время пребывания посетителей в зале распределено экспоненциально, а посетители покидают зал независимо друг от друга, то вероятность того, что один посетитель покинет зал в течение некоторого времени, определяется как:

$P(T \leq t) = 1 - e^{-\lambda t}$ => $P(T \leq 60) = 1 - e^{-(1/12) \cdot 60} = 1 - e^{-5}$

$P(\text{5 посетителей покинут за 60 минут}) = [P(T \leq 60)]^5 = \left(1 - e^{-5}\right)^5 \approx 0.9626 $

Ответ: 0.9626

# Решение задачи №2
Производящая функция для вероятностей числа заявок в системе задается формулой:
$G(z) = (0.4z + 0.6)^8 = \sum_{k=0}^{8} \binom{8}{k} (0.4z)^k (0.6)^{8-k}$

Доля времени, когда в системе есть очередь, равна сумме вероятностей, когда в системе более 2 заявок:
$P(\text{очередь}) = \sum_{n=3}^{8} P(n) = \sum_{n=3}^{8} \binom{8}{n} (0.4)^n (0.6)^{8-n}$

Вычисления:

$P(3) = \binom{8}{3} (0.4)^3 (0.6)^5 = 56 \cdot 0.064 \cdot 0.07776 \approx 0.2787$

$P(4) = \binom{8}{4} (0.4)^4 (0.6)^4 = 70 \cdot 0.0256 \cdot 0.1296 \approx 0.2322$

$P(5) = \binom{8}{5} (0.4)^5 (0.6)^3 = 56 \cdot 0.01024 \cdot 0.216 \approx 0.1238$

$P(6) = \binom{8}{6} (0.4)^6 (0.6)^2 = 28 \cdot 0.004096 \cdot 0.36 \approx 0.0410$

$P(7) = \binom{8}{7} (0.4)^7 (0.6)^1 = 8 \cdot 0.0016384 \cdot 0.6 \approx 0.00786$

$P(8) = \binom{8}{8} (0.4)^8 (0.6)^0 = 1 \cdot 0.00065536 \cdot 1 \approx 0.000655$

$P(\text{очередь}) \approx 0.2787 + 0.2322 + 0.1238 + 0.0410 + 0.00786 + 0.000655 \approx 0.6842$

Ответ: 0.6842


# Решение задачи №3

Обозначения:
- $\lambda = 1/5$ — интенсивность прибытия,
- $\mu$ - эквивалентная интенсивность обслуживания
- $\rho$ - коэффициент загрузки системы
- $L = 5$ - среднее время пребывания,
- $N = 3$ — количесвто квартир

Система описывается моделью Эрланга, так как туристы, которых не удаётся заселить, уезжают

$\mu = \frac{1}{L} = \frac{1}{5} \, \text{дней}^{-1}$

$\rho = \frac{\lambda}{\mu} = \lambda \cdot L = 0.2 \cdot 5 = 1$

### а

Вероятность отказа $B(N, \rho)$ даётся формулой:
$B(N, \rho) = \frac{\frac{\rho^N}{N!}}{\sum_{k=0}^{N} \frac{\rho^k}{k!}}$

$B(3, 1) = \frac{\frac{1^3}{3!}}{\frac{1^0}{0!} + \frac{1^1}{1!} + \frac{1^2}{2!} + \frac{1^3}{3!}} = \frac{\frac{1}{6}}{1 + 1 + \frac{1}{2} + \frac{1}{6}} = \frac{\frac{1}{6}}{\frac{8}{3}} = \frac{1}{16/3} \approx 0.0625$

Ответ: 0.0625

### б

Вероятность того, что все три квартиры пустуют, можно выразить через вероятность, что нет туристов в системе:

$P_0 = \frac{1}{\sum_{k=0}^{N} \frac{\rho^k}{k!}} = \frac{1}{\frac{8}{3}} = \frac{3}{8} = 0.375$

Ответ: 0.375

### в

По формуле Литтла:

$\text{среднее число занятых квартир} = \lambda \cdot L = 1$

Ответ: 1 квартира

# Решение задачи №4

Обозначения:
- $\mu = 1/40$ — интенсивность выхода из гнезда (так как среднее время в гнезде 40 минут),
- $\lambda = 1/40$ — интенсивность прилета в гнездо (так как среднее время вне гнезда 40 минут).
- $N = 5$ — количесвто сорок,
- $M = 3$ — количество гнезд

Коэффициент загрузки гнезд — это доля времени, в течение которого гнезда заняты. Он рассчитывается как отношение суммы времени, когда гнезда заняты, к общему доступному времени всех гнезд.

С учетом того, что у нас в системе интенсивность прихода равна интенсивности ухода, то:

$\rho = \frac{\lambda \cdot N}{M \cdot (\lambda + \mu)} = \frac{5 \cdot \frac{1}{40}}{3 \cdot (\frac{1}{40} + \frac{1}{40})} = \frac{5/40}{3 \cdot 1/20} = \frac{5}{6} \approx 0.8333$

Ответ: 0.8333

