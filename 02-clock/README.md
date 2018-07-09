# 02 - Clock

## Questions

- If I wanted to add a shadow that comes from a fixed point of light how would I add it? It seems like the best way would be to duplicate the hands markup, change to black, blur, and offset. On trying this only the first instance of hands gets grabbed because I'm using `querySelector` which just returns the first matching selector. `querySelectorAll` seems like the best solution, but I'd have to iterate over the array, and I'm not certain that this direction is performant.

## Enhancements

- Added a little extender to the second hand to mimic design of real watch faces
- Added date/day/month dial to watch face
