# scala相关
## 1隐式
### 1.1隐式参数
定义一个函数calcTax，隐式变量：rate，普通变量：amount 
def calcTax(amount: Float)(implicit rate: Float): Float = amount * rate  
如何使用：  
implicit val te1=1f  
calcTax(2f)

### 1.2隐式转换类型
使用场景，比如我们期望获取类型X，但是参数类型是Y。这时候scala会在当前作用域范围类查找包含implicit的转换函数，从类型Y转换成X。  
val i: Int = 3.5 //直接报错  
正确使用方式：  
implicit def double2Int(d: Double) = d.toInt  
val i: Int = 3.5 //程序正常 

### 1.3隐式调用函数
如下这里会将AminalType隐式转化成SwingType，并调用SwingTypewantLearned  
class SwingType{  
  def  wantLearned(sw : String) = println("兔子已经学会了"+sw)  
}  
object swimming{  
  implicit def learningType(s : AminalType) = new SwingType  
}  
class AminalType  
object AminalType extends  App{  
  import com.mobin.scala.Scalaimplicit.swimming._  
  val rabbit = new AminalType  
    rabbit.wantLearned("breaststroke")         //蛙泳  
}

### 2 implicitly与ClassTag



