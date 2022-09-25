# HAVOK and reservoir computing for chaotic dynamics forecasting

<p align="center"><b>Group 2202</b> // Francesco Pio Barone, Gianmarco Nagaro Quiroz, Daniele Ninni, Lorenzo Valentini<br>
<b>Referee</b> // Prof. Jeff Byers, Naval Research Laboratory, Washington (<a href="https://www.linkedin.com/in/jeff-byers-8458969/">LinkedIn</a>)
</p>

This is our final project for *Laboratory of Computational Physics (Module B)*. In this work, we review two dynamical systems analysis techniques and explore whether it is possible to use them for **chaotic dynamics forecasting**.

The first technique is the **Hankel Alternative View Of Koopman** (HAVOK) analysis, based on a [paper](https://www.nature.com/articles/s41467-017-00030-8) by Steven L. Brunton et al, 2017. At first, we develop the framework to achieve the same results shown in the paper. Then, we discuss some features of the new coordinate space.

The second technique is **reservoir computing**. Reservoir computing is an excellent machine learning tool for analyzing dynamical systems in a data driven fashion. The reservoir computing algorithm uses randomly sampled matrices for defining an underlying recurrent neural network which has a pool of interconnected neurons (which make the reservoir), an input layer feeding the observed data to the network, and an output layer with weights assigned to the network states. Recently, theoretical results demonstrated the equivalence between reservoir computing and Nonlinear Vector AutoRegression (NVAR). NVAR has the advantage of being computationally much less demanding and providing interpretable results. In this work, we used NVAR in order to make predictions on the behavior of the Lorenz attractor.

In this review, we probe the two techniques above to characterize the accuracy of the dynamics reconstruction and the prediction capabilities. Our results are benchmarked on a Lorenz attractor system. Eventually, we provide a demo which uses HAVOK to issue a trigger that prevents the Lorenz attractor from switching lobes. To achieve this, we train a **reinforcement learning** model to interact with the Lorenz system.

<br>

## HAVOK sentinel reinforced model

The following demo implements a trigger for chaotic dynamics control. The acting model is a Deep Deterministic Policy Gradient built in [Keras](https://keras.io/examples/rl/ddpg_pendulum/) whereas the sentinel model is a thresholded HAVOK coordinate. In other words, when the coordinate computed through the HAVOK analysis (on a moving window) exceeds a given threshold, the actor model is triggered to execute an action that prevents the Lorenz attractor from switching lobes.

<p align="center">
<a href="https://youtu.be/KdFz_q_qo3w" target="_blank">
  <img src="https://i3.ytimg.com/vi/KdFz_q_qo3w/maxresdefault.jpg" alt="Watch the video" width="440" border="30"/>
  <br>
  </a>
  click to open on YouTube
</p>

<br>

## Usage of rhavok

**rhavok** is a small library we use to collect all the common routines required by this work. You can install the library in *development mode* running the following command from the current directory:
```bash
pip install -e ./lib/
```
Then, the library will by available on your system through the usual *import* fashion:
```python
import rhavok
```
You may find some documentation on it, provided as Jupyter notebooks (`doc_*.ipynb`) inside the `lib` folder.

<br>

## Workflow summary

### HAVOK analysis

![workflow_havok](./img/workflow_havok.svg)

### Reservoir computing

![workflow_reservoir](./img/Gauthier_fig1.webp)

Picture from [10.1038/s41467-021-25801-2](https://doi.org/10.1038/s41467-021-25801-2).

***

## Bibliography

- Chaos as an intermittently forced linear system [10.1038/s41467-017-00030-8](https://www.nature.com/articles/s41467-017-00030-8) [YouTube](https://youtu.be/XHsYx1kpTXg)
- Next generation reservoir computing [10.1038/s41467-021-25801-2](https://www.nature.com/articles/s41467-021-25801-2/)
- Introduction to Next Generation Reservoir Computing [YouTube](https://youtu.be/wbH4En-k5Gs)
- GitHub/reservoirpy [Next Generation Reservoir Computing](https://github.com/reservoirpy/reservoirpy/blob/master/examples/Next%20Generation%20Reservoir%20Computing/NG-RC_Gauthier_et_al_2021.ipynb)

***

<h5 align="center">Laboratory of Computational Physics (Module B)<br>University of Padua, A.Y. 2021/22</h5>

<p align="center">
  <img src="https://user-images.githubusercontent.com/62724611/166108149-7629a341-bbca-4a3e-8195-67f469a0cc08.png" alt="" height="70"/>
</p>