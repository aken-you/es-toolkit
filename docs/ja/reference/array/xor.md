# xor

2つの配列間の対称差集合を計算します。対称差集合は、2つの配列のいずれかに含まれるが、両方には含まれない要素の集合です。

## インターフェース

```typescript
function xor<T>(arr1: T[], arr2: T[]): T[];
```

### パラメータ

- `arr1` (`T[]`): 1つ目の配列です。
- `arr2` (`T[]`): 2つ目の配列です。

### 戻り値

(`T[]`): `arr1`または`arr2`に含まれるが、両方の配列の共通部分には含まれない要素を含む配列です。

## 例

```typescript
// [1, 2, 5, 6]を返します。
xor([1, 2, 3, 4], [3, 4, 5, 6]);

// ['a', 'c']を返します。
xor(['a', 'b'], ['b', 'c']);
```