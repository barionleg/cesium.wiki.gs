Ideas for ongoing visual quality and performance improvements.

## Performance Improvements

* Optimize picking by culling an off-center view frustum containing the picked pixel(s).

### 2D

* In 2D, render static content to an FBO.  Then overall dynamic content and composite lighting.

### Mobile

* Fallback shaders/materials for different slower GPUs, mobile GPUs in particular.
* Throttle frame rate to reduce power consumption.  See Chapter 23 in OpenGL Insights.
