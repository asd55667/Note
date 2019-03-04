### Eager execution

```
import tensorflow.contrib.eager as tfe
tfe.enable_eager_execution()
```
与placeholder冲突

启用Eager execution 可以在tf中使用for loop, 支持Iterable object


### tf.map_fn
跟lambda 函数类似
map_fn(fn, elems, dtype)


### tf.variable_scope, tf.name_scope
variable_scope创建新的scope, 变量包括tf.get_variable, tf.Variable
name_scope创建scope,若scope已存在则创建subscope, 变量包括仅包括tf.Variable


### tf.nn.moments
计算当前张量的均值与方差
```
mean, variance = tf.nn.moments(x, axes, name, keepdims)
```

### tf.python.training.moving_averages.assign_moving_averages
计算变量的滑动平均
```
moving_averages.assign_moving_averages(variable, value, decay, name)
```

### tf.cond
```
tf.cond(pred, true_fn, false_fn,name)
```
true_fn与false_fn的输出类型相同,拥有一样的非0值, 返回输出张量的列表,
true_fn与false_fn都会在判断中执行,并按true,false的顺序执行, 其中非张量数据流不受流程控制, 只对张量有效

