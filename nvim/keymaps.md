# 1 builtin

## 1 operators

1. `d c y v V`.
2. **`< > g~ gu gU`**.
3. **`zf !`**
   - zf -> create fold.
   - ! -> Filter though external program.

## 2 motions.

1. `hjkl wbe ge 0^$ gg G`.
2. `fFtT`.
3. `%{}`.
   - % -> `Matching character: '()', '{}', '[]'`.
   - **`{}`** -> `prev/next empty line`.

## 3 objects

1. `"'()<>[]{} wW sp`.
   - wWsp -a-> +后面连续空格.
2. `tbB`
   - b -> `a block from ( to ) (with braces)`
   - B -> `a block from { to } (with braces)`

## 4 windows

1. `svqhlkj`
2. `wox |_=`
   - w -> `rotate switch windows`
   - **o** -> `close other windows`
   - **x** -> `swap current window with next`
   - | -> `Max out the width`
   - \_ -> `Max out the height`
   - = -> `Equally high and wide`
3. `+-<>`

## 5 nav

1. **`[ [{(<]`** -> `prev {(<`
2. **`] [}>)]`** -> `next }>)`
3. `mM` -> `prev/next method start/end`
4. **`%`** -> `prev/next unmatched group`
5. **`HML`** -> `pager home/middle/last`

## 6 g

1. `fx`
   - f -> `Go to file under cursor(abs or relative)`
   - x -> `Open the file under cursor with system app`
2. **`iv`** -> `last insert/visual`
3. `n/N` -> `search and select`
4. `%tT`

## 7 z

1. **`oO cC aA`** -> `open/close/toggle [all] folds under cursor`
2. **`ivx`**
   - i -> `toggle folding`
   - v -> `show under cursor(all folds)`
   - x -> `update folds`
3. `rRmM` -> `open/close level/all folds`
4. `ztb` -> `center/top/bottom this line`
5. `seHL`
   - s -> 光标的位置作为行的开始
   - e -> 光标的位置作为行的结束
   - H -> 向左移动光标半页
   - L -> 向右移动光标半页
