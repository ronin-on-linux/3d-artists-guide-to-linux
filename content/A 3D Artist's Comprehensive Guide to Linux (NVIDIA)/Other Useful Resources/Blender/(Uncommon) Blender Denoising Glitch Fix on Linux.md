This is NOT a consistent problem, but occasionally in some versions of [[Blender]], I have been getting weird circular or splotchy artifacts on Linux when my renders are denoised, using both Optix and OpenImageDenoiser.

After some experimentation, the fix is relatively easy.

Under the render settings, in the denoiser drop downs, there is a section labeled `Passes`. It should have options for `Albedo`, `Albedo and Normals` and `None`.

Select `Passes` -> Set it to `None`

I am unsure why this fixes it, but I figured it out by using the denoising compositing node, which I only used the image input instead of the albedo pass and it worked, so I tried settings the passes to none and re-rendered it. Comparing the denoiser node to the passes set to none now matched and no longer had the visual artifacts.