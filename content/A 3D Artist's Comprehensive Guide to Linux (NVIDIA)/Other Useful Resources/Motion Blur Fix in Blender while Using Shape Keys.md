I have found often times that when animating with shape keys in [[Blender]], if I am stacking other effects or deformations on top of the shape key, it sometimes generates motion blur artifacts when rendering that are unacceptable.

My current and best method to eliminate this to:
1. Go to the `View Layer` properties tab, and under `Passes` -> `Data`, `ENABLE Vector` pass
2. In the `Compositor` editor, add a `Vector Blur` between the Render Layers.
	1. Input the `Image` output to the vector blur `Image` input, and the `Vector` output into the vector blur `speed` input.
	2. Drag the `Image` output of the Vector Blur into the `Group Output` or the `Viewer` node.

Generally, this has fixed the issues when I have experienced them.