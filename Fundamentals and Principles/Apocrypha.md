# Apocrypha

## Digital Logic
### Basic Gates

| Gate | Description | Diagram |
| ---- | ----------- | ------- |
| AND | The output is high only when both inputs A and B are high. The AND operation will be signified by $AB$ Other notations for it are $A \wedge B$ and $A \cap B$, called the intersection of $A$ and $B$.[^1] | ![](https://i.imgur.com/LHreZIp.png) |
| OR | The output is high when either or both of inputs A or B is high. This is logically different from the exclusive OR. The OR operation will be signified by $A+B$. Other notations for it are $A \vee B$ and $A \cup B$, called the union of $A$ and $B$.[^1] | ![](https://i.imgur.com/xfakuWp.png) |
| XOR | The output is high when either of inputs A or B is high, but not if both A and B are high.[^1] | ![](https://i.imgur.com/W3GXc8T.png) |
| NAND | The output is high when either of inputs A or B is high, or if neither is high. In other words, it is normally high, going low only if both A and B are high.[^1][^2] | ![](https://i.imgur.com/FuVMA8P.png) |
| NOR | The output is high only when neither A nor B is high. That is, it is normally high but any kind of non-zero input will take it low.[^1][^2] | ![](https://i.imgur.com/6xMQskk.png) | 
| XNOR | The output is high when both inputs A and B are high and when neither A nor B is high.[^1] | ![](https://i.imgur.com/svOqw7c.png) |


[^1]: [Source](http://hyperphysics.phy-astr.gsu.edu/hbase/Electronic/gate.html#c1)

[^2]: The NAND gate and the NOR gate can be said to be universal gates since [combinations](http://hyperphysics.phy-astr.gsu.edu/hbase/Electronic/nand.html#c4) of them can be used to accomplish any of the [basic operations](http://hyperphysics.phy-astr.gsu.edu/hbase/Electronic/diglog.html#c1) and can thus produce an [inverter](http://hyperphysics.phy-astr.gsu.edu/hbase/Electronic/buffer.html#c3), an OR gate or an AND gate. The non-inverting gates do not have this versatility since they can't produce an invert.

## Metric Prefixes
Abridged for computer architecture applicability[^3]:

| Name | Factor | Name |
| ---- | ------ | ---- | 
| peta | $10^{15}$ | Quadrillion |
| tera | $10^{12}$ | Trillion | 
| giga | $10^{9}$ | Billion |
| mega | $10^{6}$ | Million | 
|      | $10^{1}$ | One | 
| milli | $10^{-3}$ | Thousandth |
| micro | $10^{-6}$ | Millionth |
| nano | $10^{-9}$ | Billionth |

[^3]: [Source](https://www.nist.gov/pml/owm/metric-si-prefixes)
