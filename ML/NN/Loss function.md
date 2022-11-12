* May be a dedicated LF for every NN output. But there is only one scalar value for GD, so you should use mean value
## Best Practices
### Choosing LF
1. Бинарная классификация - бинарная перекрёстная энтропия. Последний слой - Dense с одним нейроном и sigmoid = вероятность.
2. Классификация - многозначная перекрёстная энтропия
	1. Кодировать метки с применением метода кодирования категорий (так-же известного как прямое кодирование) и использовать функцию потерь categorical_crossentropy
	2. Кодировать метки как целые числа и использовать функцию потерь sparse_categorical_crossentropy
3. Регрессия - СКО
	1. do not use an activation function (linear layer)
	2. вместо точности используется MAE
	3. Use [[Preprocessing]] Norm
	4. 
4. Обучение на последовательности - ассоциативная временная классификация (Connectionist Temporal Classification, CTC)