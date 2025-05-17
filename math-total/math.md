
# 数学分析
## 函数
## 极限与连续
### 1. 数列极限  
#### 定义（ε-N语言）  
对任意$\epsilon > 0$，存在正整数$N$，当$n > N$时，有：  
$$|a_n - A| < \epsilon$$  
则称数列$\{a_n\}$收敛于$A$，记为$\lim_{n \to \infty} a_n = A$  

#### 性质  
- **唯一性**：若极限存在则唯一  
- **保号性**：若$\lim_{n \to \infty} a_n = A > 0$，则存在$N$，当$n > N$时$a_n > 0$  
- **有界性**：若$\lim_{n \to \infty} a_n = A$，则数列$\{a_n\}$有界。  
**证明**：  
由极限定义，取$\epsilon = 1$，存在$N$，当$n > N$时，$|a_n - A| < 1$，即$|a_n| < |A| + 1$。  
对$n \leq N$，取$M = \max\{|a_1|, |a_2|, \dots, |a_N|\}$，则对任意$n$，$|a_n| \leq \max\{M, |A| + 1\}$，故$\{a_n\}$有界。  

---

- **夹逼定理**：若$a_n \leq b_n \leq c_n$且$\lim a_n = \lim c_n = L$，则$\lim b_n = L$  

---

### 2. 函数极限  
#### 定义（ε-δ语言）  
对任意$\epsilon > 0$，存在$\delta > 0$，当$0 < |x - x_0| < \delta$时，有：  
$$|f(x) - A| < \epsilon$$  
记为$\lim_{x \to x_0} f(x) = A$  

#### 单侧极限  
- **右极限**：$\lim_{x \to x_0^+} f(x) = A$  
- **左极限**：$\lim_{x \to x_0^-} f(x) = A$  
*极限存在的充要条件：左右极限存在且相等*  

#### 重要极限  
$$ \lim_{x \to 0} \frac{\sin x}{x} = 1 $$  
$$ \lim_{x \to \infty} \left(1+\frac{1}{x}\right)^x = e $$  

---

### 3. 连续性与间断点  
#### 连续定义  
若$\lim_{x \to x_0} f(x) = f(x_0)$，则$f(x)$在$x_0$处连续  

#### 间断点分类  
| 类型       | 特征                          | 示例                    |
|------------|-------------------------------|-------------------------|
| 可去间断点 | $\lim f(x)$存在但不等于$f(x_0)$ | $f(x)=\frac{\sin x}{x}$在$x=0$处 |
| 跳跃间断点 | 左右极限存在但不相等           | 分段函数在连接点处      |
| 无穷间断点 | 极限趋向于无穷大               | $f(x)=\frac{1}{x}$在$x=0$处 |
| 振荡间断点 | 极限不存在且振荡               | $f(x)=\sin\frac{1}{x}$在$x=0$处 |

---

### 4. 闭区间上连续函数性质  
1. **有界性定理**：若$f(x) \in C[a,b]$，则$f(x)$在$[a,b]$上有界  
2. **最值定理**：存在$\xi_1,\xi_2 \in [a,b]$，使得：  
   $$f(\xi_1) \leq f(x) \leq f(\xi_2),\ \forall x \in [a,b]$$  
3. **介值定理**：对任意$c$介于$f(a)$与$f(b)$之间，存在$\xi \in (a,b)$使得$f(\xi)=c$  

### 5. 推论  
1. **推论1**：若数列$\{a_n\}$收敛，则$\{a_n\}$必有界。  
 **解释**：收敛数列的有界性是极限存在的重要性质，常用于证明极限不存在（若数列无界，则极限不存在）。  

2. **推论2**：若数列$\{a_n\}$的奇数列$\{a_{2n-1}\}$和偶数列$\{a_{2n}\}$均收敛于同一数$A$，则$\{a_n\}$收敛于$A$。  
**证明**：  
设$\lim_{n \to \infty} a_{2n-1} = A$，$\lim_{n \to \infty} a_{2n} = A$。  
对任意$\epsilon > 0$，存在$N_1$，当$n > N_1$时，$|a_{2n-1} - A| < \epsilon$；  
存在$N_2$，当$n > N_2$时，$|a_{2n} - A| < \epsilon$。  
取$N = \max\{2N_1 - 1, 2N_2\}$，则当$n > N$时，$|a_n - A| < \epsilon$，故$\lim_{n \to \infty} a_n = A$。

### 扩展 几个基本定理  


#### 1.区间套定理  
**定义**：一个闭区间序列$\{[a_n, b_n]\}$称为区间套，如果满足：  
1. $[a_{n+1}, b_{n+1}] \subseteq [a_n, b_n],\ n=1,2,\dots$  
2. $\lim_{n \to \infty} (b_n - a_n) = 0$  

**定理1（区间套定理）**：对任意区间套$\{[a_n, b_n]\}$，存在唯一一点$\xi$属于所有区间。  
**证明**：  
- 由条件1知$\{a_n\}$单调递增且有上界$b_1$，$\{b_n\}$单调递减且有下界$a_1$，故$\lim a_n$和$\lim b_n$均存在。  
- 由条件1知$\lim a_n = \lim b_n = \xi$，且$a_n \leq \xi \leq b_n$，故$\xi$属于所有区间。  
- 唯一性：若存在$\xi'$也满足$a_n \leq \xi' \leq b_n$，则$|\xi' - \xi| \leq b_n - a_n$，由条件2知$\xi' = \xi$。  

---

#### 2. 致密性定理  
**定理2（致密性定理）**：有界数列必有收敛的子数列。  
**证明**：  
- 设$\{x_n\}$为有界数列，存在$a, b$使得$a \leq x_n \leq b$。  
- 将区间$[a, b]$等分为两个子区间，至少有一个子区间包含$\{x_n\}$的无穷多项，记为$[a_1, b_1]$。  
- 重复上述过程，得到区间套$\{[a_n, b_n]\}$，且每个$[a_n, b_n]$包含$\{x_n\}$的无穷多项。  
- 由区间套定理，存在$\xi \in [a_n, b_n]$，且$\lim a_n = \lim b_n = \xi$。  
- 从$\{x_n\}$中选取子数列$\{x_{n_k}\}$，使得$x_{n_k} \in [a_k, b_k]$，则$\lim x_{n_k} = \xi$。  

---

#### 3. 完备性定理（柯西收敛原理）  
**定理3（完备性定理）**：数列$\{x_n\}$收敛的充要条件是：对任意$\epsilon > 0$，存在$N$，当$n, m > N$时，$|x_n - x_m| < \epsilon$。  
**证明**：  
- **必要性**：若$\{x_n\}$收敛于$a$，则对任意$\epsilon > 0$，存在$N$，当$n, m > N$时，$|x_n - a| < \frac{\epsilon}{2}$，$|x_m - a| < \frac{\epsilon}{2}$，故$|x_n - x_m| < \epsilon$。  
- **充分性**：  
  1. 证明$\{x_n\}$有界：取$\epsilon = 1$，存在$N$，当$n, m > N$时，$|x_n - x_m| < 1$，故$\{x_n\}$有界。  
  2. 由致密性定理，$\{x_n\}$有收敛子数列$\{x_{n_k}\}$，设$\lim x_{n_k} = a$。  
  3. 对任意$\epsilon > 0$，存在$K$，当$k > K$时，$|x_{n_k} - a| < \frac{\epsilon}{2}$；同时存在$N$，当$n, m > N$时，$|x_n - x_m| < \frac{\epsilon}{2}$。  
  4. 取$k$使得$n_k > N$，则当$n > N$时，$|x_n - a| \leq |x_n - x_{n_k}| + |x_{n_k} - a| < \epsilon$，故$\lim x_n = a$。  

---

#### 4. 有限覆盖定理  
**定理4（有限覆盖定理）**：设开区间集合$E$覆盖闭区间$[a, b]$，则可以从$E$中选出有限个开区间覆盖$[a, b]$。  
**证明**：  
- 反证法：假设$[a, b]$不能被$E$中任何有限个区间覆盖。  
- 将$[a, b]$等分为两个闭子区间，至少有一个不能被$E$中有限个区间覆盖，记为$[a_1, b_1]$。  
- 重复上述过程，得到区间套$\{[a_n, b_n]\}$，且每个$[a_n, b_n]$不能被$E$中有限个区间覆盖。  
- 由区间套定理，存在$\xi \in [a_n, b_n]$，且$\lim a_n = \lim b_n = \xi$。  
- 由于$E$覆盖$[a, b]$，存在开区间$(\alpha, \beta) \in E$使得$\xi \in (\alpha, \beta)$。  
- 取$\epsilon = \min\{\xi - \alpha, \beta - \xi\}$，存在$N$，当$n > N$时，$[a_n, b_n] \subseteq (\alpha, \beta)$，与假设矛盾。  

---

#### 5. 康托尔定理（一致连续性定理）  
**定理5（康托尔定理）**：闭区间上的连续函数必一致连续。  
**证明**：  
- 设$f(x) \in C[a, b]$，对任意$\epsilon > 0$，对每个$x \in [a, b]$，存在$\delta_x > 0$，当$|x' - x| < 2\delta_x$时，$|f(x') - f(x)| < \frac{\epsilon}{2}$。  
- 构造开区间$\Delta_x = (x - \delta_x, x + \delta_x)$，则$\{\Delta_x\}$覆盖$[a, b]$。  
- 由有限覆盖定理，存在有限个$\Delta_{x_1}, \Delta_{x_2}, \dots, \Delta_{x_k}$覆盖$[a, b]$。  
- 取$\delta = \min\{\delta_{x_1}, \delta_{x_2}, \dots, \delta_{x_k}\}$，则对任意$x', x'' \in [a, b]$，若$|x' - x''| < \delta$，存在$\Delta_{x_i}$使得$x' \in \Delta_{x_i}$，故$|x' - x_i| < \delta_{x_i}$，$|x'' - x_i| < 2\delta_{x_i}$，从而$|f(x') - f(x'')| < \epsilon$。  


## 导数与微分
### 1. 导数的定义与几何意义  
**定义**：  
函数$f(x)$在点$x_0$处的导数定义为：  
$$ f'(x_0) = \lim_{\Delta x \to 0} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} $$  
若极限存在，则称$f(x)$在$x_0$处可导。  

**几何意义**：  
导数$f'(x_0)$表示曲线$y = f(x)$在点$(x_0, f(x_0))$处切线的斜率。  

---

### 2. 基本求导公式  
1. **常数函数**：$(C)' = 0$  
2. **幂函数**：$(x^n)' = n x^{n-1}$  
3. **指数函数**：$(e^x)' = e^x$，$(a^x)' = a^x \ln a$  
4. **对数函数**：$(\ln x)' = \frac{1}{x}$，$(\log_a x)' = \frac{1}{x \ln a}$  
5. **三角函数**：  
   - $(\sin x)' = \cos x$  
   - $(\cos x)' = -\sin x$  
   - $(\tan x)' = \sec^2 x$  
6. **反三角函数**：  
   - $(\arcsin x)' = \frac{1}{\sqrt{1 - x^2}}$  
   - $(\arctan x)' = \frac{1}{1 + x^2}$  

---

### 3. 求导法则  
1. **和差法则**：$(u \pm v)' = u' \pm v'$  
2. **积法则**：$(uv)' = u'v + uv'$  
3. **商法则**：$\left(\frac{u}{v}\right)' = \frac{u'v - uv'}{v^2}$  
4. **链式法则**：若$y = f(u)$，$u = g(x)$，则$\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}$  

---

### 4. 高阶导数  
函数$f(x)$的$n$阶导数记为$f^{(n)}(x)$，定义为：  
$$ f^{(n)}(x) = \frac{d^n f}{dx^n} $$  
**常用高阶导数**：  
1. $(e^x)^{(n)} = e^x$  
2. $(\sin x)^{(n)} = \sin\left(x + \frac{n\pi}{2}\right)$  
3. $(\cos x)^{(n)} = \cos\left(x + \frac{n\pi}{2}\right)$  

---

### 5. 微分的定义与性质  
**定义**：  
函数$f(x)$在点$x_0$处的微分定义为：  
$$ df = f'(x_0) dx $$  
其中$dx$为自变量的增量。  

**性质**：  
1. **线性性**：$d(u \pm v) = du \pm dv$  
2. **乘积微分**：$d(uv) = u dv + v du$ 

## 微分中值定理与导数的应用

### 1. 微分中值定理  
#### 罗尔定理  
若函数$f(x)$满足：  
1. 在闭区间$[a, b]$上连续；  
2. 在开区间$(a, b)$内可导；  
3. $f(a) = f(b)$，  
则存在$\xi \in (a, b)$，使得$f'(\xi) = 0$。  

#### 拉格朗日中值定理  
若函数$f(x)$满足：  
1. 在闭区间$[a, b]$上连续；  
2. 在开区间$(a, b)$内可导，  
则存在$\xi \in (a, b)$，使得：  
$$ f'(\xi) = \frac{f(b) - f(a)}{b - a} $$  

#### 柯西中值定理  
若函数$f(x)$和$g(x)$满足：  
1. 在闭区间$[a, b]$上连续；  
2. 在开区间$(a, b)$内可导；  
3. $g'(x) \neq 0$，$\forall x \in (a, b)$，  
则存在$\xi \in (a, b)$，使得：  
$$ \frac{f'(\xi)}{g'(\xi)} = \frac{f(b) - f(a)}{g(b) - g(a)} $$  

---

### 2. 泰勒公式  
**泰勒公式**：若函数$f(x)$在$x_0$处$n$阶可导，则：  
$$ f(x) = f(x_0) + f'(x_0)(x - x_0) + \frac{f''(x_0)}{2!}(x - x_0)^2 + \cdots + \frac{f^{(n)}(x_0)}{n!}(x - x_0)^n + R_n(x) $$  
其中，余项$R_n(x)$为：  
$$ R_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x - x_0)^{n+1} $$  

**麦克劳林公式**：当$x_0 = 0$时，泰勒公式简化为：  
$$ f(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \cdots + \frac{f^{(n)}(0)}{n!}x^n + R_n(x) $$  

---

### 3. 洛必达法则  
若$\lim_{x \to a} f(x) = \lim_{x \to a} g(x) = 0$或$\pm \infty$，且$\lim_{x \to a} \frac{f'(x)}{g'(x)}$存在或为$\pm \infty$，则：  
$$ \lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)} $$  

---

### 4. 函数的单调性与极值  
#### 单调性  
若$f'(x) > 0$，$\forall x \in (a, b)$，则$f(x)$在$(a, b)$上单调递增；  
若$f'(x) < 0$，$\forall x \in (a, b)$，则$f(x)$在$(a, b)$上单调递减。  

#### 极值  
若$f(x)$在$x_0$处可导，且$f'(x_0) = 0$，则：  
1. 若$f'(x)$在$x_0$左侧为正，右侧为负，则$f(x_0)$为极大值；  
2. 若$f'(x)$在$x_0$左侧为负，右侧为正，则$f(x_0)$为极小值。  

---

### 5. 函数的凹凸性与拐点  
#### 凹凸性  
若$f''(x) > 0$，$\forall x \in (a, b)$，则$f(x)$在$(a, b)$上为凹函数；  
若$f''(x) < 0$，$\forall x \in (a, b)$，则$f(x)$在$(a, b)$上为凸函数。  

#### 拐点  
若$f''(x_0) = 0$，且$f''(x)$在$x_0$两侧符号相反，则$(x_0, f(x_0))$为拐点。  

---

### 6. 达布定理  
**达布定理**：若函数$f(x)$在闭区间$[a, b]$上可导，则$f'(x)$在$[a, b]$上具有介值性。  
即：若$f'(a) \neq f'(b)$，且$k$介于$f'(a)$与$f'(b)$之间，则存在$\xi \in (a, b)$，使得$f'(\xi) = k$。  

---

### 7. 曲率  
**曲率定义**：曲线$y = f(x)$在点$(x, y)$处的曲率$\kappa$定义为：  
$$ \kappa = \frac{|f''(x)|}{\left(1 + f'(x)^2\right)^{3/2}} $$  

**曲率半径**：曲率半径$R$为曲率的倒数，即：  
$$ R = \frac{1}{\kappa} $$  

**曲率中心**：曲率中心$(a, b)$的坐标为：  
$$ a = x - \frac{f'(x)\left(1 + f'(x)^2\right)}{f''(x)} $$  
$$ b = y + \frac{1 + f'(x)^2}{f''(x)} $$ 

## 不定积分
### 基本积分公式  
#### 基本形式  
1. **幂函数**：  
   $$\int x^n dx = \frac{x^{n+1}}{n+1} + C \quad (n \neq -1)$$  
   $$\int \frac{1}{x} dx = \ln|x| + C$$  

2. **指数函数**：  
   $$\int e^x dx = e^x + C$$  
   $$\int a^x dx = \frac{a^x}{\ln a} + C$$  

3. **三角函数**：  
   $$\int \sin x dx = -\cos x + C$$  
   $$\int \cos x dx = \sin x + C$$  
   $$\int \tan x dx = -\ln|\cos x| + C$$  
   $$\int \sec^2 x dx = \tan x + C$$  
   $$\int \csc^2 x dx = -\cot x + C$$  
   $$\int \sec x \tan x dx = \sec x + C$$  

4. **反比例与根式**：  
   $$\int \frac{1}{\sqrt{a^2 - x^2}} dx = \arcsin \frac{x}{a} + C$$  
   $$\int \frac{1}{a^2 + x^2} dx = \frac{1}{a} \arctan \frac{x}{a} + C$$  

---

#### 扩展形式  
1. **双曲函数**：  
   $$\int \sinh x dx = \cosh x + C$$  
   $$\int \cosh x dx = \sinh x + C$$  

2. **有理分式**：  
   $$\int \frac{1}{x^2 - a^2} dx = \frac{1}{2a} \ln\left|\frac{x - a}{x + a}\right| + C$$  
   $$\int \frac{1}{\sqrt{x^2 \pm a^2}} dx = \ln\left|x + \sqrt{x^2 \pm a^2}\right| + C$$  

---

### 积分技巧  
#### 基础方法  
1. **凑微分法**：  
   $$\int f(g(x))g'(x) dx = \int f(u) du \quad (u = g(x))$$  
   *例：$\int xe^{x^2} dx = \frac{1}{2}e^{x^2} + C$*  

2. **分部积分法**：  
   $$\int u dv = uv - \int v du$$  
   *优先顺序（反三角函数 > 对数函数 > 幂函数 > 指数函数 > 三角函数）*  

---

#### 特殊形式处理  
1. **三角代换**：  
   - $\sqrt{a^2 - x^2}$ → 令$x = a \sin t$  
   - $\sqrt{a^2 + x^2}$ → 令$x = a \tan t$  
   - $\sqrt{x^2 - a^2}$ → 令$x = a \sec t$  

2. **倒代换**：  
   对$\int R(x, \sqrt{ax + b}) dx$，令$t = \sqrt{ax + b}$  

3. **分式分解**：  
   将有理函数$\frac{P(x)}{Q(x)}$分解为部分分式，适用于$Q(x)$可因式分解的情形  

4. **配对积分法**：  
   对$\int e^{ax} \sin bx dx$或$\int e^{ax} \cos bx dx$，通过两次分部积分建立方程求解  

---

### 3. 特殊积分类型  
1. **含绝对值函数**：  
   $$\int |x - a| dx = \frac{1}{2}(x - a)|x - a| + C$$  

2. **分段函数积分**：  
   分段讨论积分区间，保证积分连续性  

3. **递推公式**：  
   *例：$\int \sin^n x dx = -\frac{\sin^{n-1}x \cos x}{n} + \frac{n-1}{n} \int \sin^{n-2}x dx$*  

---

### 4. 积分表补充公式  
1. **高阶三角积分**：  
   $$\int \sec x dx = \ln|\sec x + \tan x| + C$$  
   $$\int \csc x dx = \ln|\csc x - \cot x| + C$$  

2. **多项式组合**：  
   $$\int \frac{P(x)}{(x - a)^n} dx$$ 
   通过多项式除法分解  

3. **指数与三角混合**：  
   $$\int e^{ax} \cos bx dx = \frac{e^{ax}(a \cos bx + b \sin bx)}{a^2 + b^2} + C$$

## 定积分  
### 1. 定积分定义与性质  
**定义**：  
若函数$f(x)$在$[a,b]$上可积，则定积分：  
$$ \int_{a}^{b} f(x) dx = \lim_{\lambda \to 0} \sum_{i=1}^{n} f(\xi_i) \Delta x_i $$  
其中$\lambda = \max\{\Delta x_i\}$，$\Delta x_i = x_i - x_{i-1}$  

**基本性质**：  
1. **线性性**：$\int_{a}^{b} [\alpha f(x) + \beta g(x)] dx = \alpha \int_{a}^{b} f(x) dx + \beta \int_{a}^{b} g(x) dx$  
2. **区间可加性**：$\int_{a}^{b} f(x) dx = \int_{a}^{c} f(x) dx + \int_{c}^{b} f(x) dx$  
3. **奇偶对称性**：  
   - 若$f(x)$为奇函数，则$\int_{-a}^{a} f(x) dx = 0$  
   - 若$f(x)$为偶函数，则$\int_{-a}^{a} f(x) dx = 2\int_{0}^{a} f(x) dx$  

---

### 2. 定积分计算  
1. **牛顿-莱布尼茨公式**：  
   $$ \int_{a}^{b} f(x) dx = F(b) - F(a) $$  
   其中$F(x)$为$f(x)$的原函数  

2. **换元法**：  
   令$x = \varphi(t)$，则：  
   $$ \int_{a}^{b} f(x) dx = \int_{\alpha}^{\beta} f(\varphi(t)) \varphi'(t) dt $$  
   需注意换元后积分上下限对应  

3. **分部积分法**：  
   $$ \int_{a}^{b} u dv = [uv]_{a}^{b} - \int_{a}^{b} v du $$  

---

### 3. 特殊积分处理  
1. **含参变量积分**：  
   $$ \frac{d}{d\alpha} \int_{a(\alpha)}^{b(\alpha)} f(x, \alpha) dx = f(b,\alpha)b' - f(a,\alpha)a' + \int_{a}^{b} \frac{\partial f}{\partial \alpha} dx $$  

2. **反常积分**：  
   - **无穷区间**：$\int_{a}^{+\infty} f(x) dx = \lim_{b \to +\infty} \int_{a}^{b} f(x) dx$  
   - **无界函数**：$\int_{a}^{b} f(x) dx = \lim_{\epsilon \to 0^+} \int_{a+\epsilon}^{b} f(x) dx$  

---

### 4. 定积分应用  
1. **几何应用**：  
   - 面积：$S = \int_{a}^{b} |f(x) - g(x)| dx$  
   - 体积（旋转体）：$V = \pi \int_{a}^{b} [f(x)]^2 dx$  
   - 弧长：$L = \int_{a}^{b} \sqrt{1 + [f'(x)]^2} dx$  

2. **物理应用**：  
   - 质心坐标：$\bar{x} = \frac{1}{S} \int_{a}^{b} x f(x) dx$  
   - 变力做功：$W = \int_{a}^{b} F(x) dx$  

---
---
## 微分方程  
### 1. 一阶微分方程  
1. **可分离变量方程**：  
   $$ \frac{dy}{dx} = f(x)g(y) \implies \int \frac{dy}{g(y)} = \int f(x) dx $$  

2. **齐次方程**：  
   $$ \frac{dy}{dx} = f\left(\frac{y}{x}\right) \implies 令\ u = \frac{y}{x} $$  

3. **一阶线性方程**：  
   $$ y' + P(x)y = Q(x) \implies y = e^{-\int P dx} \left( \int Q e^{\int P dx} dx + C \right) $$  

4. **恰当方程**：  
   $$ M(x,y)dx + N(x,y)dy = 0 \quad \text{满足} \ \frac{\partial M}{\partial y} = \frac{\partial N}{\partial x} $$  
   解为势函数$\varphi(x,y) = C$  

---

### 2. 高阶微分方程  
1. **线性齐次方程**：  
   $$ y^{(n)} + a_1(x)y^{(n-1)} + \dots + a_n(x)y = 0 $$  
   - **叠加原理**：解的线性组合仍为解  
   - **通解**：$y = C_1 y_1 + C_2 y_2 + \dots + C_n y_n$  

2. **常系数线性方程**：  
   特征方程：$r^n + a_1 r^{n-1} + \dots + a_n = 0$  
   - **单实根**$r$：对应项$e^{rx}$  
   - **重根**$r$（k重）：对应项$(C_1 + C_2 x + \dots + C_k x^{k-1})e^{rx}$  
   - **共轭复根**$\alpha \pm \beta i$：对应项$e^{\alpha x}(C_1 \cos \beta x + C_2 \sin \beta x)$  

3. **非齐次方程特解**：  
   - **待定系数法**：根据自由项形式猜测特解（如多项式、指数、三角函数组合）  
   - **变参数法**：利用齐次解构造特解：$y_p = \sum_{i=1}^n C_i(x) y_i(x)$  

---

### 3. 微分方程组  
**线性常系数方程组**：  
$$ \begin{cases} 
\frac{dx}{dt} = a_{11}x + a_{12}y \\ 
\frac{dy}{dt} = a_{21}x + a_{22}y 
\end{cases} $$  
解法：  
1. 求系数矩阵特征值$\lambda_1, \lambda_2$  
2. 根据特征值类型（实/复，单/重根）构造通解  

---

### 4. 特殊方程类型  
1. **伯努利方程**：  
   $$ y' + P(x)y = Q(x)y^n \quad (n \neq 0,1) $$  
   令$z = y^{1-n}$转化为线性方程  

2. **欧拉方程**：  
   $$ x^n y^{(n)} + a_1 x^{n-1} y^{(n-1)} + \dots + a_n y = 0 $$  
   令$t = \ln x$转化为常系数方程  

---

### 5. 解的存在唯一性定理  
**皮卡定理**：若$f(x,y)$及$\frac{\partial f}{\partial y}$在区域$D$内连续，则初值问题：  
$$ y' = f(x,y), \quad y(x_0) = y_0 $$  
在$x_0$某邻域内存在唯一解




---






