---
layout: post
title: TensorFlow
category: AI
tags: [AI, tensorflow]
---



# TensorFlow

```python
import tensorflow as tf

# Variable
## Constant
hello = tf.constant('Hello, TensorFlow!')
a = tf.constant(4)
b = tf.constant(2)
## Placeholder
x = tf.placeholder(tf.float32, [2, 3])
## Variable
y = tf.Variable([[0.1, 0.2], [0.3, 0.4], [0.5, 0.6]])

# Operator
c = tf.add(a, b)
z = tf.matmul(x, y)

# Input
x_data = [[1, 2, 3], [4, 5, 6]]

# Run
sess = tf.Session()
sess.run(tf.global_variables_initializer())
print(sess.run(hello))
print(sess.run([a, b, c]))
print(sess.run(z, feed_dict={x: x_data}))
sess.close()
```

