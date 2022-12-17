# Basic
https://habr.com/ru/company/ods/blog/328372/
## (PR) - Precision, Recall, F-мера - классификация
* FP - ошибки I рода, FN - ошибки II рода
* *$precision = \frac{TP}{TP+FP}$ - точность - доля правильных положительных прогнозов - способность отличать класс от других
* *$recall = \frac{TP}{TP+FN}$* - полнота - доля найденных объектов положительного класса - способность обнаруживать класс
* Не зависят от соотношения классов
Обычно задача - баланс этих метрик. Способы их объединения (для оптимизации по гиперпараметру, н-р. GridSearchCV):
*   F-мера *$\large \ F_\beta = (1 + \beta^2) \cdot \frac{precision \cdot recall}{(\beta^2 \cdot precision) + recall}$*,
	* $\beta$ - вес точности в метрике
* sklearn - metrics.classification_report
#research Несбалансированные классы (http://contrib.scikit-learn.org/imbalanced-learn/)
## AUC-ROC, AUC-PR - выбор порога классификации
* AUC-ROC (или ROC AUC) — площадь (Area Under Curve) под кривой ошибок (Receiver Operating Characteristic curve )
* Данная кривая представляет из себя линию от (0,0) до (1,1) в координатах True Positive Rate (TPR) и False Positive Rate (FPR):
	* *$\large TPR = \frac{TP}{TP + FN}$ - полнота
	* $\large FPR = \frac{FP}{FP + TN}$ - доля объектов из negative класса, предсказанная неверно
* #ToDo https://alexanderdyakonov.wordpress.com/2015/10/09/%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%BA%D0%B8-%D0%BF%D1%80%D0%BE-auc-roc/
## Logistic Loss
* *$\large logloss = - \frac{1}{l} \cdot \sum_{i=1}^l (y_i \cdot log(\hat y_i) + (1 - y_i) \cdot log(1 - \hat y_i))$
* 







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