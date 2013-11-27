Particles systems are used for smoke, fire, explosion, sparks, clouds, dust, snow, rain, flowing water, etc.  Initially, we are are interested in smoke trails.

Initially simulate on the CPU and render with the [BillboardCollection](http://cesiumjs.org/Cesium/Build/Documentation/BillboardCollection.html).

Abstractions
* `ParticleSystem`
   * has an `Emitter`
      * has an `GenerationShape` - Interface for the shape of the emitter.  Implementations include:
         * Sphere with a `radius`
         * Circle in the `xy` plane with an `ejectionAngle` allowing cone-like emittance.
         * To grow/shrink the particle system, `radius`, `ejectionAngle`, etc. can vary over time.
      * has initial particle conditions for:
         * Acceleration range.  Range is always mean and maximum variance.
         * Velocity range.
         * Scale.
         * Material properties.
         * TODO: vary over time.
      * has initial conditions for
         * Particles per second.
         * Total number of particles - so we can allocate a vertex buffer once.
         * Start/stop time.  Stop after x number of particles, etc.
   * has many `Particle` objects, which each have:
      * `position`, `velocity`, and `acceleration`.
      * `life` - remaining life.
      * `scale`.  _Need a `collisionRadius` too?_
      * `texture` and `color`, including `alpha`.  _Need more general material?_
      * TODO: velocity for varying everything?  Per particle?  Global?
      * TODO: vary over time.
   * has many `Force` objects - an interface for forces applied to particles.  Implementations include:
      * Directional forces - wind, gravity, and drift (e.g., smoke drifts upward).
      * Friction - _Don't need this right away_.
      * TODO: vary over time, e.g., wind speed up or slow down.
   * has many `CollisionResponse` objects.  Implementations include:
      * `BouncePlane`, e.g., smoke from a launch vehicle interacting with the ground plane.
   * has many `ParticleKiller` objects.  Implementations include:
      * Life expires.
      * Intensity drops below threshold.
      * Positions goes below WGS84.  Positions goes outside of bounding volume, etc.
      * _TODO_: Could more general `ParticleManipulator` that can start changing the particle's `alpha` to fade out, etc.

Reading TODO
* [The Design of an API for Particle Systems](http://www.cs.unc.edu/techreports/00-007.pdf)
* [Hardware-based Simulation and Collision Detection for Large Particle Systems](http://www.cg.informatik.uni-siegen.de/data/Publications/2004/GH2004.pdf)

Still need to think about:
* Determine coarse bounding volume so it doesn't need to be updated each frame.
* Update/collide when culled?
* Time can go backwards!

## Ideas for Later

* More `GenerationShape` objects.
   * Rectangle in the `xy` plane with an `ejectionAngle`.
   * Cartographic extent with an `ejectionAngle`.
* Particle rotation and angular velocity.
* Particle mass.
* Particle system hierarchies – particle systems of particle systems.

Performance
* Generate a custom vertex shader to simulate on the GPU, and use custom rendering code for better performance.  Try to avoid generate approach that requires VTF and ping-ponging textures.
   * Alternatively, explore web workers.
* Number of particles created per frame varies based on the screen-space of the particle system.

Rendering
* Sort back-to-front for alpha blending.
* Draw lines for sparks and/or anti-aliasing.
* Particles casting shadows in general, and shadows onto other particles in particular.

## Resources

* For fun: perhaps [flocking](http://cis565-fall-2013.github.io/lectures/10-16-Simple-Simulation.pdf) with WebGL 2.0 transform feedback.
* [Physically Based Modeling: Principles and Practice](http://www.cs.cmu.edu/~baraff/sigcourse/)
* Procedural Methods chapter in Interactive Computer Graphics
* [Particle Systems  - A Technique  for Modeling  a  Class of Fuzzy Objects]( http://www.lri.fr/~mbl/ENS/IG2/devoir2/files/docs/fuzzyParticles.pdf)
* Dynamic Particle Systems (Page 120) in [Programming Vertex, Geometry, and Pixel Shaders](http://prelight.googlecode.com/files/Programming%20Vertex%20Geometry%20and%20Pixel%20Shaders.pdf)
* [The Ocean Spray in Your Face](http://www.lri.fr/~mbl/ENS/IG2/devoir2/files/docs/particles.pdf)
* [Building an Advanced Particle System](http://www.gamasutra.com/view/feature/131565/building_an_advanced_particle_.php)
* [Optimizing the rendering of a particle system](http://realtimecollisiondetection.net/blog/?p=91)
* Fire in the “Vulcan” Demo in [GPU Gems]( http://http.developer.nvidia.com/GPUGems/gpugems_ch06.html)
* [OpenGL ES Particle System Tutorial](http://www.raywenderlich.com/37600/opengl-es-particle-system-tutorial-part-1)
* Humus' Demos
   * [Particle system](http://www.humus.name/index.php?page=3D&ID=13)
   * [Shadowed particles](http://www.humus.name/index.php?page=3D&ID=15)
   * [Fire2](http://www.humus.name/index.php?page=3D&ID=48)
* [Flint particle system](http://flintparticles.org/)
* [Oak3D Particle Demo](http://www.oak3d.com/demo/Engine_Particle.html)
* [Generic Particle System](http://www.terathon.com/wiki/index.php/Generic_Particle_System) in the C4 Engine
* [sparks.js](https://github.com/zz85/sparks.js)
* [Creating Particles with Three.js](http://www.aerotwist.com/tutorials/creating-particles-with-three-js/)
* [Three.js Clouds](http://mrdoob.com/lab/javascript/webgl/clouds/)