# chart.js

## 各領域のサイズ取得
  - chart.boxesで各領域を取得できる  
    各領域については、[core.layout.js](https://github.com/chartjs/Chart.js/blob/master/src/core/core.layouts.js) のコメントを参照すると良い
<pre>
	// Essentially we now have any number of boxes on each of the 4 sides.
	// Our canvas looks like the following.
	// The areas L1 and L2 are the left axes. R1 is the right axis, T1 is the top axis and
	// B1 is the bottom axis
	// There are also 4 quadrant-like locations (left to right instead of clockwise) reserved for chart overlays
	// These locations are single-box locations only, when trying to register a chartArea location that is already taken,
	// an error will be thrown.
	//
	// |----------------------------------------------------|
	// |                  T1 (Full Width)                   |
	// |----------------------------------------------------|
	// |    |    |                 T2                  |    |
	// |    |----|-------------------------------------|----|
	// |    |    | C1 |                           | C2 |    |
	// |    |    |----|                           |----|    |
	// |    |    |                                     |    |
	// | L1 | L2 |           ChartArea (C0)            | R1 |
	// |    |    |                                     |    |
	// |    |    |----|                           |----|    |
	// |    |    | C3 |                           | C4 |    |
	// |    |----|-------------------------------------|----|
	// |    |    |                 B1                  |    |
	// |----------------------------------------------------|
	// |                  B2 (Full Width)                   |
	// |----------------------------------------------------|
	//
	// What we do to find the best sizing, we do the following
	// 1. Determine the minimum size of the chart area.
	// 2. Split the remaining width equally between each vertical axis
	// 3. Split the remaining height equally between each horizontal axis
	// 4. Give each layout the maximum size it can be. The layout will return it's minimum size
	// 5. Adjust the sizes of each axis based on it's minimum reported size.
	// 6. Refit each axis
	// 7. Position each axis in the final location
	// 8. Tell the chart the final location of the chart area
	// 9. Tell any axes that overlay the chart area the positions of the chart area
</pre>
