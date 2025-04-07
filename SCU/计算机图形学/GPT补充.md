
### vertexAttribPointer()各个参数的具体含义
`gl.vertexAttribPointer()` 是 WebGL 中用于指定顶点属性数据格式和布局的关键函数，通常用于告诉 WebGL 如何解释顶点缓冲区中的数据。该函数的各个参数含义如下：
```javascript
gl.vertexAttribPointer(index, size, type, normalized, stride, offset);
```

1. **`index`**：
   - 类型：`GLuint`
   - 含义：指定要配置的顶点属性的索引。即着色器中定义的属性变量的位置，通常使用 `gl.getAttribLocation` 获取。
   - 示例：如果在顶点着色器中有一个 `attribute vec4 a_Position;`，你会通过 `gl.getAttribLocation(program, "a_Position")` 获得这个属性的位置索引，然后传给 `index` 参数。
2. **`size`**：
   - 类型：`GLint`
   - 含义：每个顶点属性的组成部分个数。可以是 1、2、3 或 4，表示每个顶点有多少个分量。例如，顶点坐标 `vec2` 对应 `size = 2`，颜色 `vec4` 对应 `size = 4`。
   - 示例：
     - 如果顶点是 2D 坐标 `(x, y)`，`size` 为 2；
     - 如果是 3D 坐标 `(x, y, z)`，`size` 为 3。
3. **`type`**：
   - 类型：`GLenum`
   - 含义：指定数据的类型。常见值有：
     - `gl.FLOAT`：浮点数，表示数据为 `32-bit` 浮点型（常用）。
     - `gl.UNSIGNED_BYTE`：无符号 8 位整数。
     - `gl.BYTE`：有符号 8 位整数。
     - `gl.UNSIGNED_SHORT`：无符号 16 位整数。
     - `gl.SHORT`：有符号 16 位整数。
   - 示例：通常顶点坐标使用浮点数，所以使用 `gl.FLOAT`。
4. **`normalized`**：
   - 类型：`GLboolean`
   - 含义：是否将整数型的数据归一化。该参数对浮点类型数据（如 `gl.FLOAT`）没有影响。
     - `true`：将数据映射到 `[0, 1]`（无符号类型）或 `[-1, 1]`（有符号类型）。
     - `false`：不进行归一化，使用原始数据。
   - 示例：对于颜色数据，使用无符号字节表示时，可以设置为 `true`，使颜色值被归一化到 `[0, 1]`。
5. **`stride`**：
   - 类型：`GLsizei`
   - 含义：==指定连续顶点属性之间的字节偏移量。==默认值为 0，表示属性是紧密排列的。如果顶点属性不连续，则需要手动指定步长。
     - 如果步长为 0，WebGL 自动计算属性之间的间隔。
     - 如果步长为非零值，意味着同一属性的两个值之间有额外的数据（比如多个顶点属性存储在同一个缓冲区中时使用）。
   - 示例：如果每个顶点包含 2 个 `float` 组成的坐标和 4 个 `float` 组成的颜色，则步长为 `(2 + 4) * 4 = 24` 字节。
6. **`offset`**：
   - 类型：`GLintptr`
   - 含义：顶点属性在缓冲区中的起始偏移量，单位为字节。如果属性在缓冲区的开头，设置为 0。如果不是从缓冲区的起始位置开始存储，需要设置正确的偏移值。
   - 示例：如果缓冲区中的数据首先存储了坐标，然后存储了颜色，颜色属性的偏移量可能就是 `(2 * 4)` 字节（即跳过前两个浮点数坐标）。
#### 示例说明：
假设你定义了一个顶点数据数组，包含 `2D` 坐标和颜色信息：
```javascript
var verticesColors = new Float32Array([
  // 顶点坐标 (x, y)       // 顶点颜色 (r, g, b, a)
   0.0,  0.5,               1.0, 0.0, 0.0, 1.0,  // 第一个顶点
  -0.5, -0.5,               0.0, 1.0, 0.0, 1.0,  // 第二个顶点
   0.5, -0.5,               0.0, 0.0, 1.0, 1.0   // 第三个顶点
]);
```
你想使用 `gl.vertexAttribPointer` 配置顶点位置（`a_Position`）和顶点颜色（`a_Color`）：

```javascript
// 假设我们已经创建了顶点缓冲区并绑定到 ARRAY_BUFFER
// 设置 a_Position 属性
var FSIZE = verticesColors.BYTES_PER_ELEMENT; // 一个浮点数的字节大小
gl.vertexAttribPointer(a_Position, 2, gl.FLOAT, false, FSIZE * 6, 0); 
// 2个浮点数为顶点坐标，每6个值（2个坐标+4个颜色）组成一个顶点，偏移量为0

// 设置 a_Color 属性
gl.vertexAttribPointer(a_Color, 4, gl.FLOAT, false, FSIZE * 6, FSIZE * 2);
// 4个浮点数为颜色，每6个值组成一个顶点，偏移量是2个坐标之后，即 FSIZE * 2
```
#### 总结：
- **`index`**：着色器属性变量的位置。
- **`size`**：顶点属性的分量个数。
- **`type`**：顶点属性的数据类型。
- **`normalized`**：是否归一化整数数据。
- **`stride`**：顶点属性之间的字节跨度。
- **`offset`**：数据在缓冲区中的偏移量。