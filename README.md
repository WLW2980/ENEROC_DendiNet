# ENEROC_DendiNet
This is the brief introduction of De-Noise De-stationary Inception Network. ENEROC preserves the copyright of HPPC test data. The comprehensive details encompassing the model and associated data will not be made available publicly, as they are safeguarded by the company's confidentiality protocols. However, acedemic and reasonable request will be considered under the premise of Company's permission. 


Our novel transformer based netwrok achieves SOTA on Panasonic dataset for all range ambient temperature(-20deg -10deg, 0deg, 10deg,25deg) in which we use  US06 and HWFT as testing dataset.
## Highlights
1.The model mainly consistsof an FFT filter, a De-stationary module, and an Inception module to handel the nosie.  
2.we relaxed strict linear assumpution proposed in https://arxiv.org/abs/2205.14415, and then the self-attention block is re-designed. The attention score is developed as follows :
$$Softmax(\frac{QK^T}{\sqrt{d_K}})=Softmax[\frac{Q^{'} K^{'T} +(Q^{'} B_{k}-\textbf{1}(A_{Q}^{T}-\mu_{x}^{T}B_{Q}^{T})B_{k}+XB_{Q}^{T}B_{k})X^{T}+(XB_{Q}^{T}-\textbf{1}(A_{Q}^{T}-\mu_{x}^{T}B_{Q}^{T}))K^{'T}}{\sqrt{d_K}}]$$
where $A_{Q},B_{Q},A_{K},B_{K}$ are novel quantity we proposed which requires the computaion of Jacobian(J) and its derivative For example, $A$ is defined as $A_{K}:=-\Sigma_{b=1}^{D}J_{f}^{ab}(\mu_{x})(\mu_{x})_b$, the remaining quantities is same as in the paper.
3. we employe the weighted summation of denoised signal from De-stationary module and noise from inception module : i.e,  $ (1-w) \cdot X^{\text{ns}} + w \cdot X^{\text{incep}}$
## Main results (Complete results are presented in each notebook):
### Perfomance for -20deg -10deg, 0deg, 10deg,
<img width="471" alt="image" src="https://github.com/WLW2980/ENEROC_DendiNet/assets/129783512/a70fd45d-8c13-4d12-be04-27bb99ea80e3"> \
1.-10deg \
<img width="593" alt="image" src="https://github.com/WLW2980/ENEROC_DendiNet/assets/129783512/09c105bb-48e4-4754-b615-4e32554fc0e9"> 
2.0deg \
<img width="572" alt="image" src="https://github.com/WLW2980/ENEROC_DendiNet/assets/129783512/47a34711-93d5-42c8-ad4b-e9847623d1e6"> 
3.25deg \
<img width="617" alt="image" src="https://github.com/WLW2980/ENEROC_DendiNet/assets/129783512/280fb988-bdc0-4623-ac48-c04cbfb105a4">







