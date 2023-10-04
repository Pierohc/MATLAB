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



