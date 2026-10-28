---
title: "[Imaging physics] 내가 그의 이름을 불러주었을 때, 그는 나에게로 와서 꽃이 되었다."
date: 2026-10-28
summary: "빛과 물체의 상호작용으로부터 2차원 이미지가 만들어지는 세 가지 결 — surface, transmission, cross-section — 과 그 역문제에 대하여."
tags:
  - imaging
  - neural-rendering
  - essay
math: true
show_breadcrumb: false
---

우리가 눈으로 보고, 카메라로 담아내는 모든 것이 실은 빛과 물체 사이의 상호작용으로부터 비롯된다는 당연한 사실이 새삼스럽게도 흥미롭습니다. 대상은 그 자체로 존재하지만, 우리가 마주하는 것은 어디까지나 빛을 매개로 드러난 대상의 모습입니다. 빛이 물체와 만나 흡수되고, 반사되고, 가려지는 과정을 거쳐 비로소 하나의 형상으로 우리에게 드러난다는 것을 생각하다 보면, 어쩌면 대상은 우리가 관측하는 순간에야 비로소 하나의 의미 있는 존재가 되는지도 모르겠습니다.

> **내가 그의 이름을 불러주었을 때
> 그는 나에게로 와서
> 꽃이 되었다.**
>
> — 김춘수, 「꽃」

## How the World Becomes an Image

실재하는 대상이 하나의 이미지로 우리에게 드러날 때, 즉 '그가 나에게로 올 때', 그 모습은 있는 그대로 전해지지 않습니다. 빛과 물질 사이의 상호작용이라는 물리적 과정을 거쳐 비로소 우리에게 도달하죠. 어떤 때는 표면에서 반사된 빛으로, 어떤 때는 내부를 통과한 신호로, 또 어떤 때는 공간의 한 단면으로 우리 앞에 나타납니다.

**Surface imaging.** 주로 가시광선 영역을 다룹니다. 일반 카메라로 찍은 이미지가 대표적이죠. 빛은 물체의 표면(surface)에서 반사(reflect)되어 우리에게 도달하고, 불투명한 물체에서는 가장 앞에 놓인 표면만이 기록됩니다. 그래서 이 방식의 본질은 가림(occlusion)에 있습니다. 앞의 물체가 뒤의 물체를 가리고, 어느 방향에서 보느냐에 따라 드러나는 면이 달라집니다. 이런 장면을 그래픽스로 모델링할 때는, 표면을 반투명한 매질(medium)로 근사해 광선 경로를 따라 기여를 쌓아 올리는 볼륨 렌더링(volume rendering)을 씁니다. Gaussian Splatting [1]과 NeRF [2]가 대표적이죠. 이때 기여의 누적(compositioning)은 앞에서 뒤로 순서대로 이루어지고, 앞쪽의 불투명도가 뒤쪽의 기여를 점점 감쇠시키죠. 최종적으로 2D 이미지에서 표현되는 최종 픽셀의 RGB vector, 즉 렌더링 된 픽셀 값(rendered intensity) $I$는 다음과 같이 표현됩니다.

$$
I = \sum_{i} c_i \alpha_i \prod_{j < i}(1 - \alpha_j)
$$

$\prod_{j < i}(1 - \alpha_j)$ 항이 바로 투과율(transmittance)을 수식으로 옮긴 것입니다. $c_i$는 각 요소의 색상(color), $\alpha_i \in [0, 1]$는 불투명도(opacity)를 의미합니다. 여기서는 매질이 놓인 순서, 즉 깊이가 결과를 바꾸기 때문에 정렬(depth sorting)이 반드시 필요합니다.

**Transmission / projection imaging.** X-ray와 CBCT(Cone-Beam Computed Tomography)가 여기에 속합니다. 여기에서 다루는 빛은 파장이 훨씬 짧고 광자 에너지가 높아 물체에 막혀 멈추는 대신 물체를 통과합니다. 검출기의 한 픽셀이 담는 값은, 광선이 지나온 경로 전체에 걸친 감쇠(attenuation)를 적분한 값, 곧 선적분(line integral)입니다. 감쇠 자체는 곱셈적으로 일어나지만(Beer–Lambert law), 로그를 취하는 순간 덧셈이 되고, 그래서 선적분으로 깔끔하게 정리됩니다.

$$
-\ln\!\left(\frac{I_{\text{out}}}{I_{\text{in}}}\right) = \int_{0}^{L} \mu(x(l))\, dl
$$

$I_{\text{in}}, I_{\text{out}}$는 각각 물체에 입사하는 빛과 투과한 빛의 세기이며, $x(l)$은 광선의 경로, $\mu(x)$는 광선에서의 위치 $x$에서의 선형 감쇠 계수(linear attenuation coefficient)입니다. 여기엔 가장 앞 표면이라는 개념이 없습니다. 경로 위의 모든 깊이가 하나의 값으로 더해질 뿐이죠. 그리고 더하기는 순서를 따지지 않으니, 앞서 surface imaging에서 그토록 중요했던 정렬이 여기서는 필요하지 않습니다. 가림도 없고, 순서도 없습니다.

**Cross-sectional / tomographic (slice) imaging.** MRI가 대표적입니다. 엄밀히 말하면, 여기서는 빛이 아니라 자기공명 신호지만요. 관측이 3차원 공간을 2차원으로 옮긴다는 기하학적 관점에서는 같은 틀로 볼 수 있습니다. 이 방식에서 2차원 영상의 각 값은 경로를 따라 쌓인 것이 아니라, 3차원 공간의 한 평면에서의 국소 신호로 결정됩니다. 이론적으로는 두께가 0인 단면이고, 실제로는 유한한 두께를 가진 얇은 층(slab)에 대한 국소 적분입니다.

$$
I(u, v) = \int_{z_0 - \Delta/2}^{z_0 + \Delta/2} f(u, v, z)\, dz \;\xrightarrow[\Delta \to 0]{}\; f(u, v, z_0)
$$

여기서 $f(u, v, z)$는 3차원 공간의 위치 $(u, v, z)$에서 정의된 신호 분포로, $(u, v)$는 단면 내 좌표, $z$는 단면에 수직인 깊이 방향의 좌표입니다. $z_0$는 관측하고자 하는 단면의 중심 위치이며, $\Delta$는 단면의 두께를 나타냅니다. 경로 적분도, 가림도, 보는 방향에 따른 변화도 없습니다. 공간의 한 지점이 곧 하나의 값으로 대응하는, 가장 직접적인 관계입니다.

## From Ideas to Appearances

같은 3차원 세계를 바라보더라도, 우리가 어떤 물리적 상호작용을 통해 관측하느냐에 따라 손에 쥐는 정보는 전혀 달라집니다. 어떤 영상은 표면의 가시성을, 어떤 영상은 경로 전체의 누적 감쇠를, 또 다른 영상은 특정 단면의 신호 분포를 담아냅니다. 우리가 보는 것은 대상 자체가 아니라, 언제나 특정한 관측 물리를 거쳐 만들어진 대상의 표현입니다. 자연스럽게 플라톤의 이데아가 떠오릅니다. 복원하고자 하는 3차원 대상은 그 자체로 온전히 존재합니다. 이데아계라고 해도 좋겠죠. 그런데 우리가 실제로 손에 쥐는 것은 그 대상이 특정한 물리를 거쳐 2차원으로 내려온 그림자들뿐입니다. 현상계인 셈입니다. Imaging physics란 결국 이데아에서 현상으로 내려오는 투영의 규칙이고, 앞의 세 범주는 그 규칙이 반사냐, 투과냐, 단면이냐에 따라 갈라진 것입니다.

그렇게 보면 2D 이미지로부터 3D object를 복원하는 역문제는, 이 불완전한 그림자들로부터 이데아를 거슬러 올라가는 일입니다. 관측은 언제나 부분적이고 불완전하기에, 우리는 대상에 사전지식(prior)이라는 이름을 불러줌으로써 비로소 그것을 하나의 온전한 형상으로 다시 세웁니다. Implicit Neural Representation [2]은 그 이데아를 연속적인 함수의 모습으로 담아두려는 시도이고, 네트워크의 작은 가중치가 방대한 관측을 얼마나 압축해 품어내는가(compression ratio) [3]는, 그 표현이 현상 너머의 구조를 얼마나 본질에 가깝게 붙잡았는지를 가늠하는 하나의 척도가 되지 않을까 싶습니다.

---

### References

[1] Kerbl, Bernhard, et al. "3D Gaussian Splatting for Real-Time Radiance Field Rendering." *ACM Transactions on Graphics* 42.4 (2023): 139-1.

[2] Mildenhall, Ben, et al. "NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis." *Communications of the ACM* 65.1 (2021): 99–106.

[3] Strümpler, Yannick, et al. "Implicit Neural Representations for Image Compression." *European Conference on Computer Vision*. Cham: Springer Nature Switzerland, 2022.
