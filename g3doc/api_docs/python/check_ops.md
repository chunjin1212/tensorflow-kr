<! -이 파일은 생성 된 기계입니다 : 편집하지 마십시오! ->

# Asserts 및 boolean 검사
[TOC]

# Asserts 및 boolean 검사

- - -

### `tf.assert_negative(x, data=None, summarize=None, name=None)` {#assert_negative}

`x <0`가 가지고 있는 요소의 조건을 assert 하세요.

조작에 종속성을 추가하는 예 :

```python
with tf.control_dependencies([tf.assert_negative(x)]):
  output = tf.reduce_sum(x)
```

확인중인 텐서에 의존성을 추가하는 예 :

```python
x = tf.with_dependencies([tf.assert_negative(x)], x)
```

부정은 `x`의 모든 원소`x [i]`에 대해`x [i] <0`을 의미합니다.
`x`가 비어 있으면 이것은 약간 부족하지만 만족됩니다.

##### 객체:


* <b>`x` </ b> : 숫자 형`Tensor`.
* <b>`data` </ b> : 조건이 거짓이면 텐서 (tenors)가 출력됩니다. 기본값은
    에러 메시지와`x`의 처음 몇개의 엔트리입니다.
* <b>`summarize` </ b> : 각 텐서의 많은 엔트리를 인쇄하십시오.
* <b>`name` </ b> :이 작업의 이름입니다 (선택 사항). 기본값은 "assert_negative"입니다.

##### 반환값:

`x`가 모두 음수가 아닌 한`InvalidArgumentError`를 발생시킵니다.


- - -

### `tf.assert_positive(x, data=None, summarize=None, name=None)` {#assert_positive}

Assert the condition `x > 0` holds element-wise.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_positive(x)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_positive(x)], x)
```

Positive means, for every element `x[i]` of `x`, we have `x[i] > 0`.
If `x` is empty this is trivially satisfied.

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "assert_positive".

##### Returns:

  Op raising `InvalidArgumentError` unless `x` is all positive.


- - -

### `tf.assert_proper_iterable(values)` {#assert_proper_iterable}

Static assert that values is a "proper" iterable.

`Ops` that expect iterables of `Tensor` can call this to validate input.
Useful since `Tensor`, `ndarray`, byte/text type are all iterables themselves.

##### Args:


*  <b>`values`</b>: Object to be checked.

##### Raises:


*  <b>`TypeError`</b>: If `values` is not iterable or is one of
    `Tensor`, `SparseTensor`, `np.array`, `tf.compat.bytes_or_text_types`.


- - -

### `tf.assert_non_negative(x, data=None, summarize=None, name=None)` {#assert_non_negative}

Assert the condition `x >= 0` holds element-wise.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_non_negative(x)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_non_negative(x)], x)
```

Non-negative means, for every element `x[i]` of `x`, we have `x[i] >= 0`.
If `x` is empty this is trivially satisfied.

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).
    Defaults to "assert_non_negative".

##### Returns:

  Op raising `InvalidArgumentError` unless `x` is all non-negative.


- - -

### `tf.assert_non_positive(x, data=None, summarize=None, name=None)` {#assert_non_positive}

Assert the condition `x <= 0` holds element-wise.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_non_positive(x)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_non_positive(x)], x)
```

Non-positive means, for every element `x[i]` of `x`, we have `x[i] <= 0`.
If `x` is empty this is trivially satisfied.

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).
    Defaults to "assert_non_positive".

##### Returns:

  Op raising `InvalidArgumentError` unless `x` is all non-positive.


- - -

### `tf.assert_equal(x, y, data=None, summarize=None, name=None)` {#assert_equal}

Assert the condition `x == y` holds element-wise.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_equal(x, y)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_equal(x, y)], x)
```

This condition holds if for every pair of (possibly broadcast) elements
`x[i]`, `y[i]`, we have `x[i] == y[i]`.
If both `x` and `y` are empty, this is trivially satisfied.

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`y`</b>: Numeric `Tensor`, same dtype as and broadcastable to `x`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`, `y`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "assert_equal".

##### Returns:

  Op that raises `InvalidArgumentError` if `x == y` is False.


- - -

### `tf.assert_integer(x, data=None, summarize=None, name=None)` {#assert_integer}

Assert that `x` is of integer dtype.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_integer(x)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_integer(x)], x)
```

##### Args:


*  <b>`x`</b>: `Tensor` whose basetype is integer and is not quantized.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "assert_integer".

##### Returns:

  Op that raises `InvalidArgumentError` if `x == y` is False.


- - -

### `tf.assert_less(x, y, data=None, summarize=None, name=None)` {#assert_less}

Assert the condition `x < y` holds element-wise.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_less(x, y)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_less(x, y)], x)
```

This condition holds if for every pair of (possibly broadcast) elements
`x[i]`, `y[i]`, we have `x[i] < y[i]`.
If both `x` and `y` are empty, this is trivially satisfied.

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`y`</b>: Numeric `Tensor`, same dtype as and broadcastable to `x`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`, `y`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "assert_less".

##### Returns:

  Op that raises `InvalidArgumentError` if `x < y` is False.


- - -

### `tf.assert_less_equal(x, y, data=None, summarize=None, name=None)` {#assert_less_equal}

Assert the condition `x <= y` holds element-wise.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_less_equal(x, y)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_less_equal(x, y)], x)
```

This condition holds if for every pair of (possibly broadcast) elements
`x[i]`, `y[i]`, we have `x[i] <= y[i]`.
If both `x` and `y` are empty, this is trivially satisfied.

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`y`</b>: Numeric `Tensor`, same dtype as and broadcastable to `x`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`, `y`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "assert_less_equal"

##### Returns:

  Op that raises `InvalidArgumentError` if `x <= y` is False.


- - -

### `tf.assert_rank(x, rank, data=None, summarize=None, name=None)` {#assert_rank}

Assert `x` has rank equal to `rank`.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_rank(x, 2)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_rank(x, 2)], x)
```

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`rank`</b>: Scalar integer `Tensor`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "assert_rank".

##### Returns:

  Op raising `InvalidArgumentError` unless `x` has specified rank.

##### Raises:


*  <b>`ValueError`</b>: If static checks determine `x` has wrong rank.


- - -

### `tf.assert_rank_at_least(x, rank, data=None, summarize=None, name=None)` {#assert_rank_at_least}

Assert `x` has rank equal to `rank` or higher.

Example of adding a dependency to an operation:

```python
with tf.control_dependencies([tf.assert_rank_at_least(x, 2)]):
  output = tf.reduce_sum(x)
```

Example of adding dependency to the tensor being checked:

```python
x = tf.with_dependencies([tf.assert_rank_at_least(x, 2)], x)
```

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`rank`</b>: Scalar `Tensor`.
*  <b>`data`</b>: The tensors to print out if the condition is False.  Defaults to
    error message and first few entries of `x`.
*  <b>`summarize`</b>: Print this many entries of each tensor.
*  <b>`name`</b>: A name for this operation (optional).
    Defaults to "assert_rank_at_least".

##### Returns:

  Op raising `InvalidArgumentError` unless `x` has specified rank or higher.

##### Raises:


*  <b>`ValueError`</b>: If static checks determine `x` has wrong rank.


- - -

### `tf.assert_type(tensor, tf_type)` {#assert_type}

Asserts that the given `Tensor` is of the specified type.

##### Args:


*  <b>`tensor`</b>: A tensorflow `Tensor`.
*  <b>`tf_type`</b>: A tensorflow type (dtypes.float32, tf.int64, dtypes.bool, etc).

##### Raises:


*  <b>`ValueError`</b>: If the tensors data type doesn't match tf_type.


- - -

### `tf.is_non_decreasing(x, name=None)` {#is_non_decreasing}

Returns `True` if `x` is non-decreasing.

Elements of `x` are compared in row-major order.  The tensor `[x[0],...]`
is non-decreasing if for every adjacent pair we have `x[i] <= x[i+1]`.
If `x` has less than two elements, it is trivially non-decreasing.

See also:  `is_strictly_increasing`

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`name`</b>: A name for this operation (optional).  Defaults to "is_non_decreasing"

##### Returns:

  Boolean `Tensor`, equal to `True` iff `x` is non-decreasing.

##### Raises:


*  <b>`TypeError`</b>: if `x` is not a numeric tensor.


- - -

### `tf.is_numeric_tensor(tensor)` {#is_numeric_tensor}




- - -

### `tf.is_strictly_increasing(x, name=None)` {#is_strictly_increasing}

Returns `True` if `x` is strictly increasing.

Elements of `x` are compared in row-major order.  The tensor `[x[0],...]`
is strictly increasing if for every adjacent pair we have `x[i] < x[i+1]`.
If `x` has less than two elements, it is trivially strictly increasing.

See also:  `is_non_decreasing`

##### Args:


*  <b>`x`</b>: Numeric `Tensor`.
*  <b>`name`</b>: A name for this operation (optional).
    Defaults to "is_strictly_increasing"

##### Returns:

  Boolean `Tensor`, equal to `True` iff `x` is strictly increasing.

##### Raises:


*  <b>`TypeError`</b>: if `x` is not a numeric tensor.


