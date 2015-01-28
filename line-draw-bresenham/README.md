
```javascript
function lineToBresenham( ax, ay, bx, by )
		{
			for( var i = 0; i < arguments.length; i++ )
				arguments[i] = parseInt( arguments[i] );

			var dx = Math.abs( bx - ax ),
				dy = Math.abs( by - ay ),
				m, e, x, y, di, dt, t;

			var buf = [];

			if( dx > dy )
			{
				di = ax < bx ? +1 : -1;
				dt = ay < by ? +1 : -1;
				t = bx + di;
				m = dy / dx;
				e = 0;

				for( x = ax, y = ay; x != t; x += di )
				{
					buf.push( x );
					buf.push( y );

					e += dy;

					if( ( e << 1 ) > dx )
					{
						y = y + dt;
						e -= dx;
					}
				}
			}
			else
			{
				di = ay < by ? +1 : -1;
				dt = ax < bx ? +1 : -1;
				t = by + di;
				m = dx / dy;
				e = 0;

				for( x = ax, y = ay; y != t; y += di )
				{
					buf.push( x );
					buf.push( y );

					e += dx;

					if( ( e << 1 ) > dy )
					{
						x = x + dt;
						e -= dy;
					}
				}
			}

			return buf;
		};
```
