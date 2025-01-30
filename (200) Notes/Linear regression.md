![[linear-regression.png]]
Assumes that the relationship between data and expected output is linear ( can be expressed as $f(x) = ax + b$, no $\cos, \sin, x^n$ ).
More commonly, can be expresed as a function that takes `n` number of arguments (vector / matrix) and returns the product of that times some weights:

Python example:
```python
    def get_model_prediction(self, X: NDArray[np.float64], weights: NDArray[np.float64]) -> NDArray[np.float64]:
        return np.round(np.matmul(X, weights), 5)
        # X is an Nx3 NumPy array
        # weights is a 3x1 NumPy array
```
