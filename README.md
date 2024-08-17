# Convex_Hull
A convex hull is the smallest convex shape that can enclose a set of
points in a plane or higher-dimensional space. It can be imagined of
like stretching a rubber band around a group of points; when
released, the band will snap into the tightest possible shape that
encloses all the points. This shape is the convex hull. In 2D, it is like
the boundary of the smallest polygon that can contain all the points,
with no indentations. The project deals with the implementation of
convex hull by Jarvis March algorithm through digital circuits. The
initial process of solving the algorithm is to find out the leftmost
point of given set of x and y coordinates. The next step involves
working with three variables namely current_index(a), next(b), and
c(counter). Basically in the first operation we start the algorithm with
current_index set to the leftmost point we found initially and the
next and c(counter) are in their default states. Then we have to check
the slope of the points with respect to the next(b) by iterating c
variable to rest of points in the array. The most steepest slope point is
constantly updated in the next variable. For checking this slope there
is usually a formula derived (b.y - a.y) * (c.x - b.x) - (b.x - a.x) * (c.y -
b.y). Whenever this term is negative we just update the next(b) with
the value of c. At the end of the array we put values of next(b) in
current_index and restart the iteration. This is repeated for few
cycles to be precise n cycles in worst case where n is the size of
arrays. From this approach I drew parallelism and designed the circuit
by taking 3 set of registers . In one cycle I calculated the x(min) and in
the other cycle the y(min). Then from third cycle the convex hull is
being calculated. I have designed an orientation checker block which
just calculates the result is positive or negative from above
mentioned formula and generates signal nugg and pugg. Also if thereis case that your counter z is not equal to zero and a and b are still
same then also it gives negative OR’ed with nugg to give signal nn.
I have designed a counter with three signals x,y,z. The input is coming
from ROM file where data is stored in form of [z,1,x,y,2,x2,y2…..].
Where z is total points and 1,2 represent first,second ….numbers. So
the counter runs and gives address to ROM which in turn gives me
the value back. Also for the hold time prevention I have first given the
value of b to a and held the data of b till first 3 new clock cycles and
then latched the value of c into b for safe latching.
For calculation of leftmost point initially I have loaded 1 so that
whatever is the first point in rom gets stored and then through mux
and comparator whenever the next point is small just edit the value
of flip flop which is storing my data finally.
