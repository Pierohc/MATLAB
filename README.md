## Funciones por tramos: 
    dt = 0.1;
    t1= -10:dt:-1;
    t2= -0.9:dt:1;
    t3= 1.1:dt:5;
    t4= 5.1:dt:10;
    
    f1 = cos(2*t1);
    f2 = t2.^(2) - exp(-t2 + 1);
    f3 = cos(3*t3).*sin(2*t3);
    f4 = (2*t4)./(2*t4.^2);
    
    t = [t1,t2,t3,t4]; 
    f = [f1,f2,f3,f4]; 
    
    plot(t,f,"linewidth",1.5);
    xlabel("t"), ylabel("x(t)"), title("Gráfica de x(t)")
    grid minor;
    axis([-2,10,-6,1])

  ## ZEROS Y ONES:
    x2 = ones(size(t2));
    x3 = 2*ones(size(t3));

## Funcion Anónima (Heaviside):
    t_e = -2:0.001:2;
    x_e = @(t_e) 2*(heaviside(t_e+2)-heaviside(t_e+2)) + (t_e+1).*(heaviside(t_e+2) - heaviside(t_e+1)) + 1*(heaviside(t_e+1)-heaviside(t_e)) + 2*(heaviside(t_e) - heaviside(t_e-1)) + (-t_e+2).*(heaviside(t_e-1)-heaviside(t_e-2));
    
    plot(t_e,x_e(t_e),"LineWidth",1.5)
    grid on;
    axis([-2.5,2.5,-1.5,2.5])

## Delta de Dirac:
    t = -5:0.01:5;
    delta = @(t) t == 0;
    stem(t, delta(t),"LineWidth",1);

## Ecuaciones:

    syms D
    ecua = D^2 + 2*D;
    rpta = solve(ecua,D)  % equivale a iguales ecu a 0
    vpa(rpta,10) % forzamos a que las rptas simbólicas
      % se conviertan a rptas numéricas con 10 cifras de
      % exactitud

## Solve y Dsolve:
Solve se usa para ecuaciones algebraicas y dsolve para ecuaciones diferenciales. Como en Laplace el Y´´ y el Y´ ya tienen en si las condiciones iniciales, se usa solve. En cambio en ec. diferenciales usamos diff y evaluamos con cond, estamos trabajando más directamente con ecuaciones diferenciales y por eso se usa dsolve.

# En ecuaciones diferenciales solo se hace syms al t y a lo que hayaremos, al y(t)
![image](https://github.com/Pierohc/MATLAB/assets/133154904/039232ea-1daf-47e3-a551-7138c8437433)

    syms t y(t)
    x = cos(t) + t^3;
    dx = diff(x);
    dy2 = diff(y,2);
    dy = diff(y);
    ecu = (dy2 == 4*dy + 5*dx - 2*x);
    cond=[y(0)==0, dy(0)==1]
    ysol(t) = dsolve(ecu,cond)
    
    fplot(ysol, [-1,1])


