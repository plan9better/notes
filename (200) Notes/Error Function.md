Function that returns the error value, calculating it based on the output given and the output wanted.

Python example:
```python
    def get_error(self, model_prediction: NDArray[np.float64], ground_truth: NDArray[np.float64]) -> float:

        errors = []
        for idx,_ in enumerate(model_prediction):
            errors.append(np.square(model_prediction[idx] - ground_truth[idx]))
        errors.sort()
        return round(np.mean(errors), 5)
        # model_prediction is an Nx1 NumPy array
        # ground_truth
```