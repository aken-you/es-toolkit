# zipObjectDeep

::: info
出于兼容性原因，此函数仅在 `es-toolkit/compat` 中提供。它可能具有替代的原生 JavaScript API，或者尚未完全优化。

从 `es-toolkit/compat` 导入时，它的行为与 lodash 完全一致，并提供相同的功能，详情请见 [这里](../../../compatibility.md)。

:::

给定路径和值的数组，创建一个深层嵌套的对象。

此函数接受两个数组：一个包含属性路径的数组，另一个包含相应值的数组。它返回一个新对象，其中第一个数组的路径用作键路径来设置值，并将第二个数组中的对应元素作为值。路径可以是点分隔的字符串或属性名称的数组。如果 `keys` 数组比 `values` 数组长，剩余的键的值将为 `undefined`。

## 签名

```typescript
function zipObjectDeep<P extends PropertyKey, V>(keys: ArrayLike<P | P[]>, values: ArrayLike<V>): { [K in P]: V };
```

### 参数

- `keys` (`ArrayLike<P | P[]>`): 属性名称的数组。
- `values` (`ArrayLike<V>`): 与属性名称对应的值的数组。

### 返回值

(`{ [K in P]: V }`): 由给定的属性名称和值组成的新对象。

## 示例

```typescript
import { zipObjectDeep } from 'es-toolkit/compat';

const paths = ['a.b.c', 'd.e.f'];
const values = [1, 2];
const result = zipObjectDeep(paths, values);
// 结果将是 { a: { b: { c: 1 } }, d: { e: { f: 2 } } }

const paths = [
  ['a', 'b', 'c'],
  ['d', 'e', 'f'],
];
const values = [1, 2];
const result = zipObjectDeep(paths, values);
// 结果将是 { a: { b: { c: 1 } }, d: { e: { f: 2 } } }

const paths = ['a.b[0].c', 'a.b[1].d'];
const values = [1, 2];
const result = zipObjectDeep(paths, values);
// 结果将是 { 'a': { 'b': [{ 'c': 1 }, { 'd': 2 }] } }
```

## 性能对比

|                   | [包大小](../../../bundle-size.md) | [性能](../../../performance.md) |
| ----------------- | --------------------------------- | ------------------------------- |
| es-toolkit/compat | 938 字节 (小 88%)                 | 1,102,767 次 (慢 25%)           |
| lodash-es         | 7,338 字节                        | 1,476,660 次                    |
