# ODE
These codes are examples of solving ordinary differential equations using the finite difference method, the method of runge kutta of order 4, scipy's "odeint" function and some examples of symplectic integrator.
There is also an animation for the particle in the electromagnetic field, for the Lorenz attractor, for Fermi-Pasta-Ulam problem and for the tunnel effect through a barrier.
The "neōn katalogos" file (as the name might suggest) is a list containing several examples of implicit, explicit and symplectic ode-solving algorithms; all of them, for simplicity are applied to the harmonic oscillator.

We briefly present the various methods used(in the following t_k will indicate the k-th element of the vector that contains the quantity under examination): 
the former are Euler's methods, classical, implicit and semi-implicit (the latter symplectic)


<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;\begin{cases}&space;\frac{dy}{dt}=f(t,&space;y)\\&space;y(t_0)=y_0&space;\end{cases}&space;\\&space;\text{classical&space;euler&space;method:}\\&space;y_{k&plus;1}=y_k&plus;dtf(t_k,&space;y_k)&space;\\&space;\\&space;\text{implicit&space;euler&space;method:}\\&space;y_{k&plus;1}=y_k&plus;dtf(t_{k&plus;1},&space;y_{k&plus;1})\\&space;\\" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;\begin{cases}&space;\frac{dy}{dt}=f(t,&space;y)\\&space;y(t_0)=y_0&space;\end{cases}&space;\\&space;\text{classical&space;euler&space;method:}\\&space;y_{k&plus;1}=y_k&plus;dtf(t_k,&space;y_k)&space;\\&space;\\&space;\text{implicit&space;euler&space;method:}\\&space;y_{k&plus;1}=y_k&plus;dtf(t_{k&plus;1},&space;y_{k&plus;1})\\&space;\\" title="\\ \begin{cases} \frac{dy}{dt}=f(t, y)\\ y(t_0)=y_0 \end{cases} \\ \text{classical euler method:}\\ y_{k+1}=y_k+dtf(t_k, y_k) \\ \\ \text{implicit euler method:}\\ y_{k+1}=y_k+dtf(t_{k+1}, y_{k+1})\\ \\" /></a>



<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;\text{the&space;semi-implicit&space;euler&space;method&space;is&space;good}\\&space;\text{when&space;dealing&space;with&space;the&space;Hamilton's&space;equations}\\&space;\text{which&space;are&space;of&space;the&space;form:}\\&space;\\&space;\begin{cases}&space;\frac{dx}{dt}=f(t,&space;v)\\&space;\frac{dv}{dt}=g(t,&space;x)\\&space;\end{cases}&space;\\&space;\text{so&space;we&space;have:}\\&space;v_{k&plus;1}=v_k&plus;dtg(t_{k},&space;x_{k})\\&space;x_{k&plus;1}=x_k&plus;dtf(t_{k},&space;v_{k&plus;1})\\" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;\text{the&space;semi-implicit&space;euler&space;method&space;is&space;good}\\&space;\text{when&space;dealing&space;with&space;the&space;Hamilton's&space;equations}\\&space;\text{which&space;are&space;of&space;the&space;form:}\\&space;\\&space;\begin{cases}&space;\frac{dx}{dt}=f(t,&space;v)\\&space;\frac{dv}{dt}=g(t,&space;x)\\&space;\end{cases}&space;\\&space;\text{so&space;we&space;have:}\\&space;v_{k&plus;1}=v_k&plus;dtg(t_{k},&space;x_{k})\\&space;x_{k&plus;1}=x_k&plus;dtf(t_{k},&space;v_{k&plus;1})\\" title="\\ \text{the semi-implicit euler method is good}\\ \text{when dealing with the Hamilton's equations}\\ \text{which are of the form:}\\ \\ \begin{cases} \frac{dx}{dt}=f(t, v)\\ \frac{dv}{dt}=g(t, x)\\ \end{cases} \\ \text{so we have:}\\ v_{k+1}=v_k+dtg(t_{k}, x_{k})\\ x_{k+1}=x_k+dtf(t_{k}, v_{k+1})\\" /></a>


it is easy to verify the advantage of the latter method compared to the previous two as it is associated with a canonical transformation.
Another first order method and symplectic integrator is the midpoint method that we present in its implicit formulation:

<a href="https://www.codecogs.com/eqnedit.php?latex=y_{k&plus;1}=y_k&plus;dtf\Biggl(t_{k}&plus;\frac{dt}{2},\frac{1}{2}(y_k&space;&plus;&space;y_{k&plus;1})\Biggr)\\" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y_{k&plus;1}=y_k&plus;dtf\Biggl(t_{k}&plus;\frac{dt}{2},\frac{1}{2}(y_k&space;&plus;&space;y_{k&plus;1})\Biggr)\\" title="y_{k+1}=y_k+dtf\Biggl(t_{k}+\frac{dt}{2},\frac{1}{2}(y_k + y_{k+1})\Biggr)\\" /></a>


Another algorithm is verlet velocity integration, a symplectic method:

<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;x_{k&plus;1}=x_{k}&plus;v_{k}dt&space;&plus;a_{k}&space;\frac{dt^2}{2}\\&space;v_{k&plus;1}=v_{k}&plus;\frac{dt}{2}(a_{k}&plus;a_{k&plus;1})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;x_{k&plus;1}=x_{k}&plus;v_{k}dt&space;&plus;a_{k}&space;\frac{dt^2}{2}\\&space;v_{k&plus;1}=v_{k}&plus;\frac{dt}{2}(a_{k}&plus;a_{k&plus;1})" title="\\ x_{k+1}=x_{k}+v_{k}dt +a_{k} \frac{dt^2}{2}\\ v_{k+1}=v_{k}+\frac{dt}{2}(a_{k}+a_{k+1})" /></a>


It is interesting to show how it comes out of the stationary action principle:

<a href="https://www.codecogs.com/eqnedit.php?latex=S_{discr}=&space;\sum_{k=0}^N&space;\mathcal{L}_k&space;dt\\&space;\text{where:}\\&space;\\&space;\mathcal{L}=&space;\frac{m}{2}\frac{(x_{k&plus;1}-x_k)^2}{dt^2}&space;-&space;U(x_k)\\&space;\\&space;\text{so&space;we&space;obtain:}\\&space;\\&space;\frac{\partial&space;S_{discr}}{\partial&space;x_k}=0=&space;\frac{\partial}{\partial&space;x_k}\sum_{k=0}^N&space;\frac{m}{2}\frac{(x_{k&plus;1}-x_k)^2}{dt}&space;-&space;\frac{\partial&space;U(x_k)}{\partial&space;x_k}dt&space;\hspace{5&space;mm}&space;\forall&space;\hspace{1&space;mm}t_k" target="_blank"><img src="https://latex.codecogs.com/gif.latex?S_{discr}=&space;\sum_{k=0}^N&space;\mathcal{L}_k&space;dt\\&space;\text{where:}\\&space;\\&space;\mathcal{L}=&space;\frac{m}{2}\frac{(x_{k&plus;1}-x_k)^2}{dt^2}&space;-&space;U(x_k)\\&space;\\&space;\text{so&space;we&space;obtain:}\\&space;\\&space;\frac{\partial&space;S_{discr}}{\partial&space;x_k}=0=&space;\frac{\partial}{\partial&space;x_k}\sum_{k=0}^N&space;\frac{m}{2}\frac{(x_{k&plus;1}-x_k)^2}{dt}&space;-&space;\frac{\partial&space;U(x_k)}{\partial&space;x_k}dt&space;\hspace{5&space;mm}&space;\forall&space;\hspace{1&space;mm}t_k" title="S_{discr}= \sum_{k=0}^N \mathcal{L}_k dt\\ \text{where:}\\ \\ \mathcal{L}= \frac{m}{2}\frac{(x_{k+1}-x_k)^2}{dt^2} - U(x_k)\\ \\ \text{so we obtain:}\\ \\ \frac{\partial S_{discr}}{\partial x_k}=0= \frac{\partial}{\partial x_k}\sum_{k=0}^N \frac{m}{2}\frac{(x_{k+1}-x_k)^2}{dt} - \frac{\partial U(x_k)}{\partial x_k}dt \hspace{5 mm} \forall \hspace{1 mm}t_k" /></a>


<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;m&space;\frac{(x_k-x_{k-1})-(x_{k&plus;1}-x_{k})}{dt}-\frac{\partial&space;U(x_{k})}{\partial&space;x_{k}}&space;dt&space;=0\\&space;\\&space;\text{and&space;with&space;some&space;rehash:}\\&space;\\&space;x_{k&plus;1}=2x_{k}-x_{k-1}&plus;a_{k}dt^2\\&space;\text{where}\hspace{1mm}&space;a_{k}&space;\hspace{1mm}&space;\text{is&space;acceleration}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;m&space;\frac{(x_k-x_{k-1})-(x_{k&plus;1}-x_{k})}{dt}-\frac{\partial&space;U(x_{k})}{\partial&space;x_{k}}&space;dt&space;=0\\&space;\\&space;\text{and&space;with&space;some&space;rehash:}\\&space;\\&space;x_{k&plus;1}=2x_{k}-x_{k-1}&plus;a_{k}dt^2\\&space;\text{where}\hspace{1mm}&space;a_{k}&space;\hspace{1mm}&space;\text{is&space;acceleration}" title="\\ m \frac{(x_k-x_{k-1})-(x_{k+1}-x_{k})}{dt}-\frac{\partial U(x_{k})}{\partial x_{k}} dt =0\\ \\ \text{and with some rehash:}\\ \\ x_{k+1}=2x_{k}-x_{k-1}+a_{k}dt^2\\ \text{where}\hspace{1mm} a_{k} \hspace{1mm} \text{is acceleration}" /></a>



A method that could not miss the is :runge kutta of 4 th order:


<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;\begin{cases}&space;\dot{y}(t)=f(t,y(t))\\&space;y(t_0)=y_0&space;\end{cases}\\&space;y_{k&plus;1}&space;=&space;y_{k}&space;&plus;&space;\tfrac{h}{6}\left(k_1&space;&plus;&space;2k_2&space;&plus;&space;2k_3&space;&plus;&space;k_4&space;\right)\\&space;t_{k&plus;1}&space;=&space;t_k&space;&plus;&space;dt&space;\\&space;\text{where}&space;\hspace{2&space;mm}&space;k_1,&space;k_2,&space;k_3,&space;k_4&space;\hspace{2&space;mm}&space;\text{are:}&space;\\&space;k_1&space;=&space;f(t_k,&space;y_n)&space;\\&space;k_2&space;=&space;f(t_k&space;&plus;&space;\tfrac{dt}{2},&space;y_n&space;&plus;&space;\tfrac{1}{2}&space;k_1&space;dt)&space;\\&space;k_3&space;=&space;f(t_k&space;&plus;&space;\tfrac{dt}{2},&space;y_n&space;&plus;&space;\tfrac{1}{2}&space;k_2&space;dt)&space;\\&space;k_4&space;=&space;f(t_k&space;&plus;&space;dt,&space;y_n&space;&plus;&space;k_3&space;dt)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;\begin{cases}&space;\dot{y}(t)=f(t,y(t))\\&space;y(t_0)=y_0&space;\end{cases}\\&space;y_{k&plus;1}&space;=&space;y_{k}&space;&plus;&space;\tfrac{h}{6}\left(k_1&space;&plus;&space;2k_2&space;&plus;&space;2k_3&space;&plus;&space;k_4&space;\right)\\&space;t_{k&plus;1}&space;=&space;t_k&space;&plus;&space;dt&space;\\&space;\text{where}&space;\hspace{2&space;mm}&space;k_1,&space;k_2,&space;k_3,&space;k_4&space;\hspace{2&space;mm}&space;\text{are:}&space;\\&space;k_1&space;=&space;f(t_k,&space;y_n)&space;\\&space;k_2&space;=&space;f(t_k&space;&plus;&space;\tfrac{dt}{2},&space;y_n&space;&plus;&space;\tfrac{1}{2}&space;k_1&space;dt)&space;\\&space;k_3&space;=&space;f(t_k&space;&plus;&space;\tfrac{dt}{2},&space;y_n&space;&plus;&space;\tfrac{1}{2}&space;k_2&space;dt)&space;\\&space;k_4&space;=&space;f(t_k&space;&plus;&space;dt,&space;y_n&space;&plus;&space;k_3&space;dt)" title="\\ \begin{cases} \dot{y}(t)=f(t,y(t))\\ y(t_0)=y_0 \end{cases}\\ y_{k+1} = y_{k} + \tfrac{h}{6}\left(k_1 + 2k_2 + 2k_3 + k_4 \right)\\ t_{k+1} = t_k + dt \\ \text{where} \hspace{2 mm} k_1, k_2, k_3, k_4 \hspace{2 mm} \text{are:} \\ k_1 = f(t_k, y_n) \\ k_2 = f(t_k + \tfrac{dt}{2}, y_n + \tfrac{1}{2} k_1 dt) \\ k_3 = f(t_k + \tfrac{dt}{2}, y_n + \tfrac{1}{2} k_2 dt) \\ k_4 = f(t_k + dt, y_n + k_3 dt)" /></a>

 


If we wanted a symplectic integrator of higher order we can use the ruth method (3 or 4):

<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;v_{k&plus;1}=v_{k}&plus;d_{i}a(x_{k})dt\\&space;x_{k&plus;1}=x_{k}&plus;c_{i}v_{k&plus;1}dt\\" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;v_{k&plus;1}=v_{k}&plus;d_{i}a(x_{k})dt\\&space;x_{k&plus;1}=x_{k}&plus;c_{i}v_{k&plus;1}dt\\" title="\\ v_{k+1}=v_{k}+d_{i}a(x_{k})dt\\ x_{k+1}=x_{k}+c_{i}v_{k+1}dt\\" /></a>


the value of the coefficients d_i and c_i are in the code



