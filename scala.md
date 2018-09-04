# scala相关
## 隐式
### 1.隐式参数
定义一个函数calcTax，获取两个变量其中一个隐式变量
def calcTax(amount: Float)(implicit rate: Float): Float = amount * rate
如何使用：
implicit val te1=1f
calcTax(2f)
