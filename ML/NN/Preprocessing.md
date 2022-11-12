* Norm (based on train_data)
`mean = train_data.mean(axis=0)
`train_data -= mean
`std = train_data.std(axis=0)
`train_data /= std
`test_data -= mean
`test_data /= std
