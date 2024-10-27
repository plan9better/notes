In ML gradient descent i used to approximate the minimum of the [[Error function]] (or loss function) . By decrementing the `X` (guess) by the product of it's derivative and $\alpha$ (learning rate usually 0.01 / 0.1). 
![[gradient-descen.png]]
So if your error function is $x^2$ then the derivative is $x \times 2$ so every iteration you would do:
- start with a guess: e.g. `guess = 5`
- `guess -= derivative(guess) * learing_rate (or alpha)`

in Python for $f_e(x) = x^2$:

```python
class Solution:
    def get_minimizer(self, iterations: int, learning_rate: float, init: int) -> float:

        guess = init
        for i in range(iterations):
            guess -= (2 * guess) * learning_rate

        return round(guess, 5)
```