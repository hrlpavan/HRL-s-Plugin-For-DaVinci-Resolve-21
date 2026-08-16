# AI Cinematic Haze: Lens-Centric 3D Metric Depth Specification

Architectural and Mathematical Design Specification for the **Lens-Centric 3D Metric Depth & Volumetric Scattering Pipeline** in DaVinci Resolve Studio.

---

## 1. Pinhole Optical Ray Euclidean Distance Formulation

Instead of uncalibrated 2D semantic masks, bounding boxes, or primitive oval cutoffs, depth is defined as continuous **metric Euclidean distance** from the virtual camera optical center:

$$\mathbf{P}(u, v) = Z_{\text{metric}}(u, v) \cdot \mathbf{K}^{-1} \begin{bmatrix} u \\ v \\ 1 \end{bmatrix}$$

Where $\mathbf{K}$ is the camera intrinsic matrix:
$$\mathbf{K} = \begin{bmatrix} f_x & 0 & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{bmatrix}$$

### Optical Ray Scaling Factor:
$$r(u, v) = \sqrt{1.0 + \left(\frac{u - c_x}{f_x}\right)^2 + \left(\frac{v - c_y}{f_y}\right)^2}$$

### Continuous Metric Inverse Depth (Z-Buffer):
$$d_{\text{metric}}(u, v) = d_{\text{affine}}(u, v) \cdot r(u, v)$$
$$Z_{\text{val}}(u, v) = \frac{1.0}{d_{\text{metric}}(u, v) + 10^{-5}}$$

---

## 2. 3D Subject & Camera Motion Kalman Tracking

To prevent focal plane jumping and depth map flicker during camera pans and subject movement, the system maintains a **temporal 3D Kalman Filter state**:

```
State Vector: x_t = [ Z_subject, V_z ]^T
Measurement:  z_t = mu_Z(Saliency)

Prediction:
  x̂_t = F * x̂_{t-1}
  P̂_t = F * P_{t-1} * F^T + Q

Update:
  K_t = P̂_t * H^T * (H * P̂_t * H^T + R_t)^{-1}
  x_t = x̂_t + K_t * (z_t - H * x̂_t)
  P_t = (I - K_t * H) * P̂_t
```
Where measurement noise $R_t \propto (1.0 - \text{Confidence})$, guaranteeing stable lock on dynamic subjects across video frames.

---

## 3. Continuous Z-Buffer Layer Segmentation

Depth is segmented strictly according to Euclidean physical camera plane distance:

1. **Foreground (Subject)**:
   - Range: Continuous gradient $Z \in [0.0, Z_{\text{near}}]$
   - Processing: Sub-pixel edge guided co-filtering without binary shape masking.

2. **Midground (Intermediary Objects & Props)**:
   - Range: Continuous smooth falloff $[Z_{\text{near}}, Z_{\text{far}}]$
   - Transition: 3D volumetric feathering with continuous gamma response.

3. **Background (Walls / Horizon / Atmosphere)**:
   - Range: Asymptotic gradient $[Z_{\text{far}}, 1.0] \to \infty$
   - Physics: Koschmieder optical transmission $T(Z) = \exp(-\beta_{\text{ext}} \cdot Z)$ and in-scattering.
