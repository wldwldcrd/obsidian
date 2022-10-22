SGD с импульсом
Решает проблемы:
1. Невысокая скорость сходимости
2. Попадание в локальный минимум

`past_velocity = 0.
`momentum = 0.1 Постоянное значение импульса
`while loss > 0.01: Цикл оптимизации
	`w, loss, gradient = get_current_parameters()
	`velocity = past_velocity * momentum + learning_rate * gradient
	`w = w + momentum * velocity - learning_rate * gradient
	`past_velocity = velocity
	`update_parameter(w)`
В общем случае rmsprop наиболее подходящий по умолчанию.