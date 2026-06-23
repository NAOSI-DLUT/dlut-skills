# MATLAB 线代速查

- `det(A)`：行列式。
- `rank(A)`：秩。
- `inv(A)`：逆矩阵；实际求解方程通常用 `A\b`。
- `eig(A)`：特征值；`[V,D]=eig(A)` 同时给特征向量和对角矩阵。
- `eigs(A,k)`：部分特征值，适合大矩阵。
- `poly(A)`：特征多项式系数。
- `roots(p)`：多项式求根。
- `qr(A,0)`：经济型 QR 分解。
- `svd(A)`：奇异值分解。
- `norm(A)`：范数；常用于误差检查。
- `rref(A)`：行最简形。
- `lu(A)`、`chol(A)`：常见分解。

## 常见检查

- 正交矩阵：`norm(Q'*Q-eye(size(Q,2)))`。
- 重构误差：`norm(A-Q*R)` 或 `norm(A-V*D/V)`。
- 秩性质：比较 `rank(A)`, `rank(A')`, `rank(A'*A)` 时注意数值病态。
