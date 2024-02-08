So this is before and after of the same report with same Date range and OOD days. But Remove assortment bias is checked and unchecked.

Checked:
![[Pasted image 20240208170609.png]]

Unchecked:
![[Pasted image 20240208170651.png]]

So it's pretty clear that the values of all the columns were changed (except the Any Available As % Of Distribution column).

Now I don't have much understanding of the underlying calculations, but from what I understand of it, for each column - if remove assortment bias is checked - it's considering only those stores that sell the product type of the current SKU in the calculations. If it's unchecked, even the stores that don't sell that product type are being considered in the calculations.

Hence If we remove the "Remove Assortment Bias" configuration and default it to false, these calculations would also get affected.

