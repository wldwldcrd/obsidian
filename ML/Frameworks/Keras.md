Определение модели: #research 
1. Sequental
	`from keras import models
	`from keras import layers
	`model = models.Sequential()
	`model.add(layers.Dense(32, activation='relu', input_shape=(784,)))
	`model.add(layers.Dense(10, activation='softmax'))
2. Функциональное API
	`input_tensor = layers.Input(shape=(784,))
	`x = layers.Dense(32, activation='relu')(input_tensor)
	`output_tensor = layers.Dense(10, activation='softmax')(x)
	`model = models.Model(inputs=input_tensor, outputs=output_tensor)
Настройка оптимизатора:
`from keras import optimizers
`model.compile(optimizer=optimizers.RMSprop(lr=0.001),
`loss='binary_crossentropy',
`metrics=['accuracy'])`
Использование нестандартных функций потерь и метрик:
`from keras import losses
`from keras import metrics
`model.compile(optimizer=optimizers.RMSprop(lr=0.001),
`loss=losses.binary_crossentropy,
`metrics=[metrics.binary_accuracy])
