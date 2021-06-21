# Detection of collision between two polygons

## Idea:

Let two polygons A and B, for each point P of the polygon A, there is a polygon D such that the presence of P in D implies a collision of A and B.

This means that the problem of a collision between two polygons, no matter how complex, can be transformed into a probleme of point in a polygon.

## Steps:

### Generate the polygon D

We want to generate a polygon which is composed of a "sum" of various polygons:
- B
- inverses of A where P coincides with each point of B
- "link polygon" for translation between two points of B

#### Generate "link polygon"

To generate these poygons, one can process by following two certains vectorial path at each point of B:

Let R be the vector which link E and F, two points of B joined. Let theta_min be the angle between R and the x axis, and theta_max be theta_max + pi (the other "direction")

One path will follow the same path as the inverse of A but at each point, a theta_i, corresponding to the angle of the vector which links the point and the next one, will be calculated. If theta_i is between theta_min and theta_max, one continue the path, if not, one add R to the path, and continue the path. If the path has switched (added R), if theta_i is outside the range between theta_min and theta_max, one continue the path and continue to follow this condition until the next "switch". If not one switch again, and obey to the starting condition.

The other will be the same, but with R inversed, as theta_min and theta_max.

### Make the sum

The best way I found is to just check if the point is in one of these polygons.

### Checks point in polygon

We can use [this method](http://alienryderflex.com/polygon/) to check the presence of the point in the polygon.

## Implementation

One can find a javascript implementation of this method inside this repo. Others implementations will maybe appear.

## Pro & Cons

This method is faster at execution time if the polygon is already compiled. It is pretty slow if everything is calculated at execution time.

## License

ChocolateWare License (see LICENSE file for more)

## Bugs/Help

Do not hesitate to communicate if you have found a bug, an issue with this method, if you see a possible optimization, or if you aldready seen that before in a better implemented way, it really interests me.
