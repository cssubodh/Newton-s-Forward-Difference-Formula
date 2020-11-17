# Newton's forward interpolation
   Summary of Steps• 
   Step 1: Develop a general Taylor series expansion for f(x) about x0    
   .• Step 2: Express the various order forward differences at x0 in terms of  and itsderivatives evaluated at f(x).
   This will allow us to express the actual derivatives eval-uated at x0 in terms of forward differences.• 
   Step 3: Using the general Taylor series expansion developed in Step 1,
   sequentiallysubstitute in for the derivatives evaluated at x0 in terms of forward differences (i.e.substitute in the expressions developed in Step 2).

CODE:
%Newton’s Forward Difference Formula MATLAB Program
x = [0 2 4 7 10 12]; % inputting values of x
fx = [20 20 12 7 6 6]; % inputting values of y
dt = zeros(6,10); % function
for i = 1 : 6
dt(i,1) = x(i);% for loop
dt(i,2) = fx(i); % calling function
end
n = 5; % number of iterations
for j = 3 : 10
for i = 1 : n
dt(i,j) = dt(i+1,j-1) - dt(i,j-1)
end
n = n - 1;
end
h = x(2) - x(1) % finding the value of h
xp = 1.5; % defining the value of xp
for i = 1 : 5
q=(xp - x(i))/h; % calculating number of intervals
if (q &gt; 0 &amp;&amp; q &lt; 1)
p = q;
endif
end
p
l = xp-(p*h)
for i = 1: 5
if(l == x(i))
r = i;

endif
end % calculating different value of y
f0 = fx(r);
f01 = dt(r,3);
f02 = dt(r,(3+1));
f03 = dt((r),(3+2));
f04 = dt((r),(3+3));
% using the forward interpolation formula
xp = 1.5
fp = (f0)+((p*f01)+(p*(p-1)*f02)/(2)) + ((p*(p-1)*(p-2)*f03)/(6))+((p*(p-1)*(p-2)*(p-3)*f04)/(24))
plot(x,fx)
xf = []
yf = []
sz = size(x)(2)
for i = 1 : sz
if (x(i) &lt; xp)
xf = [xf x(i)]
yf = [yf fx(i)]
else
xf = [xf xp]
yf = [yf fp]
break
end
end
xf = [xf x(i:sz)]
yf = [yf fx(i:sz)]
figure;
plot(xf,yf)
