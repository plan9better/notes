In ML gradient descent i used to approximate the minimum of the [[error function]]. By decrementing the X (guess) by the product of it's derivative and $\alpha$ (learning rate usually 0.01 / 0.1). 
![[gradient-descen.png]]
So if your error function is $x^2$ then the derivative is $x \times 2$ so every iteration you would do:
- start with a guess: e.g. 5
- get the 