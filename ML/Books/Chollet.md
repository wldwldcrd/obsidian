Репозиторий: www.manning.com/books/deep-learning-with-python
Алгоритмы[[NVIDIA]]
* Вероятностное моделирование
	* Наивный Байесовский метод?
* Kernel methods?
	* Support Vector Machine (SVM) - классификация поиском хороших решающих границ. Отображение в пространство большей размерности, где можно разделить гиперплоскостью. Оптимизация - максимизация зазора(от точек до границы).
	* Функция ядра - незатратная вычислительная операция, отображающая любые 2 точки из исходного пространства и вычисляет расстояние между ними в целевом, полностью минуя явное вычисление нового представления. ФЯ обычно определяются вручную, а не извлекаются из данных.
* Decision trees, Random Forest, Gradient Boosting
	* RF - почти всегда оптимальны для задач поверхностного машинного обучения.
	* GB - аналог RF, но итеративно обучает новые модели для устранения слабых мест предыдущих. Один из лучших алгоритмов для задач, не связанных с распознаванием.
		* Библиотека XGBoost
* Neural Networks / Deep Learning
	* Автоматическое конструирование признаков.
	* Аналогия - сложная последовательность простых геометрических операций. Комок из красного и синего листов бумаги, которые надо выпрямить для простого разделения классов по координатам.
	* Нельзя заменить слоями поверхностных моделей, т.к. они жадные, а в DL оптимизация происходит одновременно по всем слоям
	* Все операции NN дифференцируемы - позволяет оптимизировать веса на основе градиента
		* W1 = W0 - step * gradient(f)(W0)
	* Компоненты
		* Функция активации
		* Схема инициализации весов
		* Схема оптимизации / Оптимизатор - способ использования градиента потерь для изменения параметра
			* Adam
			* SGD #research 
				* [[Optimizers]]
				* Adagrad
				* RMSProp
		* Функция потерь - минимизируемая величина
			* Categorical Crossentropy
		* Метрики для мониторинга
			* Accuracy
# 4
ML:
1. Supervised
	1. Classification
	2. Regression
	3. Генерация последовательностей — по заданной картинке предсказать заголовок, который ее описывает. Иногда генерацию последовательностей можно сформулировать как серию задач классификации (таких, как повторяющее предсказание следующего слова в последовательности).
	4. Прогнозирование дерева синтаксиса — по имеющемуся предложению требуется спрогнозировать его разложение в дерево синтаксиса.
	5. Распознавание объектов
	6. Сегментирование изображений — построить пиксельную маску для конкретного объекта.
2. Unsupervised - поиск закономерностей, часто используется в предобработке
	1. Понижение размерности
	2. Кластеризация
3. Самоконтролируемое обучение - предсказание
4. Reinforcement
	1. 
