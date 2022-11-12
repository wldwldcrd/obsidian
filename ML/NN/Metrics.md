## Data
Separate data to 3 datasets:
1) trainig -  for weights
2) validation - for hyperparams
3) testing - for final test
Notes:
* shuffle
* do not shuffle timeseries
* datasets must not be overlayed
## Separation methods
### Hold-out validation
* проверка с простым расщеплением выборки
`num_validation_samples = 10000
`np.random.shuffle(data)
`validation_data = data[:num_validation_samples]
`data = data[num_validation_samples:]
`training_data = data[:]
* обучение модели на тренировочных данных, оценка на проверочных
`model = get_model()
`model.train(training_data)
`validation_score = model.evaluate(validation_data)
* В этой точке можно выполнить корректировку модели,
повторно обучить ее, оценить, повторить корректировку.
* После настройки гиперпараметров желательно выполнить обучение модели на всех данных, не включённых в контрольный набор
`model = get_model()
`model.train(np.concatenate([training_data,validation_data]))
`test_score = model.evaluate(test_data)
* Недостаток: при малом объёме данных в наборах может быть недостаточно образцов. Видно, если при перемешивании перед разбиением наборов, оценки качества моделей сильно разнятся.
### K-fold validation
* перекрёстная проверка по K блокам
`k = 4
`num_validation_samples = len(data) // k
`np.random.shuffle(data)

`validation_scores = []
`for fold in range(k):
	`validation_data = data[num_validation_samples * fold: num_validation_samples * (fold + 1)]
	`training_data = data[:num_validation_samples * fold] + data[num_validation_samples * (fold + 1):]
	`model = get_model()
	`model.train(training_data)
	`validation_score = model.evaluate(validation_data)
	`validation_scores.append(validation_score)
Обучение на всех данных, не вошедших в контрольный набор
	`validation_score = np.average(validation_scores)
Общая оценка по k блокам
	`model = get_model()
	`model.train(data)
	`test_score = model.evaluate(test_data)

### Iterated K-fold validation with shuffling
* итерационная проверка по K блокам с перемешиванием - перемешивание данных перед каждым разбиением на K блоков
* для относительно небольших наборов данных

MAE - mean absolute error
* model.compile(optimizer='rmsprop', loss='mse', metrics=['mae'])  #research 

* K-fold cross-validation for small datasets
* 