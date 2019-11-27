# InstanceNorm 反向梯度推导
$$
\begin{aligned}
设 \quad x\in\R^{m*H}, &对InstanceNorm:\\

{\mu}_j&=\frac{1}{H}\sum_{h=1}^{H}x_j(h)\quad\quad

{\sigma}_j^2=\frac{1}{H}\sum_{h=1}^{H}\left[x_j(h)-{\mu}_j\right]^2 \quad(j=1,2,3,...,m)\\\\

\hat{x_j}&=\frac{x_j-\mu_j}{\sqrt{{\sigma}_j^2+{\varepsilon}}}\quad\quad

y_j={\gamma}\hat{x_j}+{\beta}\\\\

\frac{\partial\hat{x_j}}{\partial{\sigma}_j^2}&=-\frac{\hat{x_h}}{2({\sigma}_j^2+{\varepsilon})}\quad\quad

\frac{\partial\hat{x_j}}{\partial{\mu}_j}=-\frac{1}{\sqrt{{\sigma}_j^2+{\varepsilon}}}\\\\

\frac{\partial L}{\partial{\sigma}_j^2}&=\sum_{h=1}^{H}\frac{\partial L}{\partial \hat{x_j}(h)}\frac{\partial \hat{x_j}(h)}{\partial {\sigma}_j^2}\\\\

&=\sum_{h=1}^{H}{\gamma}\frac{\partial L}{\partial y_j(h)}\left(-\frac{\hat{x_j}(h)}{2({\sigma}_j^2+{\varepsilon})}\right)\\\\

&=-\frac{\gamma}{2({\sigma}_j^2+{\varepsilon})}\sum_{h=1}^{H}\hat{x_j}(h)\frac{\partial L}{\partial y_j(h)}\\\\

&=-\frac{\gamma}{2({\sigma}_j^2+{\varepsilon})}(\hat{x_j})^T\frac{\partial L}{\partial y_j}\\\\

\frac{\partial L}{\partial {\mu}_j}&=\sum_{h=1}^{H}\frac{\partial L}{\partial\hat{x_j}(h)}\frac{\partial\hat{x_j}(h)}{\partial\mu_j}\\\\

&=\sum_{h=1}^{H}\gamma\frac{\partial L}{\partial y_j(h)}\left(-\frac{1}{\sqrt{\sigma_j^2+\varepsilon}}\right)\\\\

&=-\frac{\gamma}{\sqrt{\sigma_j^2+\varepsilon}}\sum_{h=1}^{H}\frac{\partial L}{\partial y_j(h)}\\\\

\frac{\partial \sigma_j^2}{\partial x_j(h)}&=\frac{2[x_j(h)-\mu_j]}{H}\quad\quad
\frac{\partial \mu_j}{\partial x_j(h)}=\frac{1}{H}\quad\quad
\frac{\partial \hat{x_j}(h)}{\partial x_j(h)}=\frac{1}{\sqrt{\sigma_j^2+\varepsilon}}\\\\

\frac{\partial L}{\partial x_j(h)}&=\frac{\partial L}{\partial \hat{x_j}(h)}\frac{\partial\hat{x_j}(h)}{\partial x_j(h)}+\frac{\partial L}{\partial \sigma_j^2}\frac{\partial \sigma_j^2}{\partial x_j(h)}+\frac{\partial L}{\partial \mu_j}\frac{\partial \mu_j}{\partial x_j(h)}\\\\

&=\frac{\gamma}{\sqrt{\sigma_j^2+\varepsilon}}\frac{\partial L}{\partial y_j(h)}-\frac{\gamma}{\sqrt{\sigma_j^2+\varepsilon}}\frac{\hat{x_j}^T\frac{\partial L}{\partial y_j}}{H}\hat{x_j}(h)-\frac{\gamma}{\sqrt{\sigma_j^2+\varepsilon}}\frac{1}{H}\sum_{h=1}^{H}\frac{\partial L}{\partial y_j(h)}\\\\

&=\frac{\gamma}{\sqrt{\sigma_j^2+\varepsilon}}\left[\frac{\partial L}{\partial y_j(h)}-\frac{1}{H}\hat{x_j}^T\frac{\partial L}{\partial y_j}\hat{x_j}(h)-\frac{1}{H}\sum_{h=1}^{H}\frac{\partial L}{\partial y_j(h)}\right]\\\\

\left(\hat{x_j}=\frac{y_j-\beta}{\gamma}\right)&\Rightarrow\frac{\gamma}{\sqrt{\sigma_j^2+\varepsilon}}\left[\frac{\partial L}{\partial y_j(h)}-\frac{1}{H}\left(\frac{y_j-\beta}{\gamma}\right)^T\frac{\partial L}{\partial y_j}\left(\frac{y_j(h)-\beta}{\gamma}\right)-\frac{1}{H}\sum_{h=1}^{H}\frac{\partial L}{\partial y_j(h)}\right]\\\\

\frac{\partial L}{\partial x_j}&=\frac{\gamma}{\sqrt{\sigma^2+\varepsilon}}\left[\frac{\partial L}{\partial y_j}-\frac{1}{H}\left(\frac{y_j-\beta}{\gamma}\right)^T\frac{\partial L}{\partial y_j}\left(\frac{y_j-\beta}{\gamma}\right)\right]-\frac{\gamma}{H\sqrt{\sigma_j^2+\varepsilon}}\sum_{k=1}^{H}\frac{\partial L}{\partial y_j(k)}

\end{aligned}
$$


