# Arithmetic operations

Bash supports arithmetic operations using different methods. Below are some common ways to perform arithmetic calculations in a Bash script.

### 1. Using `expr` Command
```bash
#!/bin/bash
a=10
b=5
sum=$(expr $a + $b)
echo "Sum: $sum"
```

### 2. Using `$(( ))` (Recommended)
```bash
#!/bin/bash
a=10
b=5
sum=$((a + b))
diff=$((a - b))
mul=$((a * b))
div=$((a / b))
mod=$((a % b))

echo "Sum: $sum"
echo "Difference: $diff"
echo "Product: $mul"
echo "Quotient: $div"
echo "Modulus: $mod"
```

### 3. Using `let` Command
```bash
#!/bin/bash
a=10
b=5
let sum=a+b
let diff=a-b
let mul=a*b
let div=a/b
let mod=a%b

echo "Sum: $sum"
echo "Difference: $diff"
echo "Product: $mul"
echo "Quotient: $div"
echo "Modulus: $mod"
```

### 4. Using `bc` for Floating Point Arithmetic
```bash
#!/bin/bash
a=10
b=3
div=$(echo "scale=2; $a / $b" | bc)
echo "Division: $div"
```

> If you need floating-point calculations, `bc` is the best choice.

