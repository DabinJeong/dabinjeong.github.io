---
title: "[Imaging physics] How the world becomes an image"
date: 2026-10-28
summary: "On the three modes by which the physics of light-matter interaction turns a three-dimensional world into a two-dimensional image (surface, transmission, cross-section) and the inverse problem."
tags:
  - imaging
  - neural-rendering
  - essay
math: true
show_breadcrumb: false
---

{{< langswitch >}}

The obvious fact that everything we see with our eyes, and everything a camera records, arises from the interaction between light and matter is something I keep coming back to. The object exists on its own, yet what we meet is always the object as revealed through light as a medium. Light meets matter, is absorbed, reflected, occluded, and only then takes shape for us. Thinking it through, I almost wonder whether the object only becomes a meaningful presence at the very moment of observation.

> **When I called out his name,
> he came to me
> and became a flower.**
>
> Kim Chun-su, "Flower"

<figure class="dj-essay-figure">
  <img src="/images/crochet-flowers.jpg" alt="Handmade crochet flowers at a market stall">
  <figcaption>A bit of a tangent, but &mdash; turns out you can make flowers out of yarn, too!</figcaption>
</figure>

## How the world becomes an image

When a real object reveals itself to us as an image, when, in the poem's words, "he comes to me," the form is not transmitted as it is. It only arrives after the physical process of interaction between light and matter. Sometimes as light reflected off a surface, sometimes as a signal that has passed through a body, sometimes as a slice through space.

**Surface imaging.** Mostly in the visible spectrum. An ordinary photograph is the canonical case. Light reflects off an object's surface and reaches us, and for an opaque object only the frontmost surface is recorded. The essence of this mode is therefore *occlusion*: the object in front hides the object behind, and what is revealed depends on the direction we look from. In graphics, we model such scenes with *volume rendering*, approximating surfaces as semi-transparent media and accumulating contributions along a ray, with Gaussian Splatting [1] and NeRF [2] as the canonical examples. The compositing goes front-to-back, with the opacity in front progressively attenuating the contributions behind. The final per-pixel RGB value, the rendered intensity $I$, is written as:

$$
I = \sum_{i} c_i\, \alpha_i \prod_{j < i}(1 - \alpha_j)
$$

The factor $\prod_{j < i}(1 - \alpha_j)$ is just transmittance written out. $c_i$ is the color of each element and $\alpha_i \in [0, 1]$ its opacity. Because the order of the media, their depth, changes the result, depth sorting is essential.

**Transmission / projection imaging.** X-ray and CBCT (Cone-Beam Computed Tomography) belong here. The light we deal with has a much shorter wavelength and much higher photon energy; rather than being stopped by matter, it passes through it. The value a single detector pixel records is an integral of the attenuation along the entire path the ray has traveled: a line integral. The attenuation itself is multiplicative (the Beer–Lambert law), but as soon as we take a logarithm it becomes additive, and the whole thing collapses neatly into a line integral.

$$
-\ln\!\left(\frac{I_{\text{out}}}{I_{\text{in}}}\right) = \int_{0}^{L} \mu(x(l))\, dl
$$

$I_{\text{in}}$ and $I_{\text{out}}$ are the incident and transmitted intensities, $x(l)$ is the ray's path, and $\mu(x)$ is the linear attenuation coefficient at position $x$ along the ray. There is no "frontmost surface" here; every depth along the path is simply summed into a single value. And because addition does not care about order, the depth sorting that mattered so much for surface imaging is unnecessary here. No occlusion, no order.

**Cross-sectional / tomographic (slice) imaging.** MRI is the representative case. Strictly speaking, what we are dealing with here is not light at all but a magnetic-resonance signal. From the geometric point of view, however, in that an observation collapses three-dimensional space into two dimensions, it fits the same frame. Each value in the 2D image is not something built up along a path; it is determined by a *local* signal on a plane through 3D space. In theory the slice has zero thickness; in practice it is a local integral over a thin slab of finite thickness.

$$
I(u, v) = \int_{z_0 - \Delta/2}^{z_0 + \Delta/2} f(u, v, z)\, dz \;\xrightarrow[\Delta \to 0]{}\; f(u, v, z_0)
$$

Here $f(u, v, z)$ is the signal distribution defined at a position $(u, v, z)$ in 3D space, with $(u, v)$ the in-plane coordinates and $z$ the depth perpendicular to the slice. $z_0$ is the center of the slice we are imaging and $\Delta$ its thickness. No path integral, no occlusion, no direction-dependent variation. One point in space corresponds directly to one value, the most direct of the three relations.

## From ideas to appearances

Even when we are looking at the same three-dimensional world, the information we end up holding is entirely different depending on which physical interaction we observe through. One image carries surface visibility; another, the accumulated attenuation along a path; another, the signal distribution on a particular slice. What we see is never the object itself, but always a representation of the object produced through a particular observational physics. Plato's forms naturally come to mind. The three-dimensional object we would like to recover exists intact, on its own. We could call it the realm of forms. What we actually get hold of, however, are only the shadows that have come down to two dimensions through a specific physics: the realm of appearances. Imaging physics, then, is the rule that governs the projection from the forms to the appearances, and the three categories above are branches of that rule, split by whether the projection is reflection, transmission, or cross-section.

Seen this way, the inverse problem of recovering a 3D object from a 2D image is the task of climbing back from these incomplete shadows to the form. Because observations are always partial and incomplete, we rebuild the object into a whole only by calling it by the name of a prior. Implicit Neural Representation [2] is one such attempt to hold the form as a continuous function, and how tightly a network's small set of weights can compress a vast body of observations (the compression ratio [3]) might be one measure of how closely that representation has caught the structure beyond the appearances.

---

### References

[1] Kerbl, Bernhard, et al. "3D Gaussian Splatting for Real-Time Radiance Field Rendering." *ACM Transactions on Graphics* 42.4 (2023): 139-1.

[2] Mildenhall, Ben, et al. "NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis." *Communications of the ACM* 65.1 (2021): 99-106.

[3] Strümpler, Yannick, et al. "Implicit Neural Representations for Image Compression." *European Conference on Computer Vision*. Cham: Springer Nature Switzerland, 2022.
