答案是 `pattern:/"(\\.|[^"\\])*"/g`。

步骤如下：

- 首先匹配左双引号 `pattern:"`
- 接着如果有反斜杠 `pattern:\\`，则匹配其后跟随的任意字符。（技术上，我们必须在模式中用双反斜杠，因为它是一个特殊的字符，但实际上是一个反斜杠字符）
- 如果没有，则匹配除双引号（字符串的结束）和反斜杠（排除仅存在反斜杠的情况，反斜杠仅在和其后字符一起使用时有效）外的任意字符：`pattern:[^"\\]`
- ...继续匹配直到遇到反双引号

运行代码如下：

```js run
let reg = /"(\\.|[^"\\])*"/g;
let str = ' .. "test me" .. "Say \\"Hello\\"!" .. "\\\\ \\"" .. ';

alert( str.match(reg) ); // "test me","Say \"Hello\"!","\\ \""
```