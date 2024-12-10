# Armstrong Number

An Armstrong number (also known as a narcissistic number) is a number that is equal to the sum of its own digits each raised to the power of the number of digits. For example, the number 153 is an Armstrong number because it has 3 digits, and if we calculate $(1^3 + 5^3 + 3^3)$, we get $(1 + 125 + 27 = 153)$. In mathematical terms, a number $(n)$ with $(d)$ digits is an Armstrong number if:

$$ n = \sum_{i=1}^{d} (digit_i)^d $$

## Facts about Armstrong numbers

1. The smallest Armstrong number is 0, and the largest 3-digit Armstrong number is 9474.
2. All single-digit numbers (0-9) are considered Armstrong numbers since they are equal to themselves raised to the power of 1.
3. Armstrong numbers can exist in any base, not just base 10; for example, 1, 2, and 3 are Armstrong numbers in base 2.
4. The number of Armstrong numbers is finite; for instance, there are only 88 Armstrong numbers in base 10.
5. The largest known Armstrong number is 2, and it has 39 digits.

# Armstrong Number

An Armstrong number (also known as a narcissistic number, pluperfect number, or pluperfect digital invariant) in a given number base $b$ is a number that is the sum of its own digits each raised to the power of the number of digits. In decimal (base-10), an Armstrong number of three digits is an integer such that the sum of the cubes of its digits is equal to the number itself. For example, $153 = 1^3 + 5^3 + 3^3$.

## Facts About Armstrong Numbers

1. The smallest Armstrong number in base-10 is $0$.
2. Every single-digit number is an Armstrong number because any number raised to the power of one is the number itself.
3. The Armstrong numbers between $100$ and $999$ are $153$, $370$, $371$, and $407$.
4. The concept can be extended to other bases, not just base-10.
5. Larger Armstrong numbers exist, but they are rare and grow quickly in size as the number of digits increases.

## Approach For Checking Armstrong Number

### Step 1: *Counting the digits*
Determine the number of digits in the number. This step is crucial because each digit will be raised to the power of the total number of digits. For example, for the number $153$, there are $3$ digits. This count will be the exponent in our calculations.

- **Time Complexity**: $O(\log_{10} N)$
- **Reason**: The number of digits in $N$ is proportional to $\log_{10} N$.

### Step 2: *Extracting digits*
Extract each digit of the number. We need to handle each digit individually to raise it to the power determined in the first step. This can be done by converting the number to a string or using mathematical operations. For instance, for $153$, we need to handle $1$, $5$, and $3$ separately.

- **Time Complexity**: $O(\log_{10} N)$
- **Reason**: You need to process each digit, and there are $\log_{10} N$ digits.

### Step 3: *Calculating the power sum*
Raise each extracted digit to the power determined in Step 1 and calculate the sum of these powered digits. This is the core calculation where we see if the sum of the powered digits matches the original number. For $153$, this involves computing $1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153$.

- **Time Complexity**: $O((\log_{10} N)^2)$
- **Reason**: Calculating the power of a single digit takes $O(d)$ time, where $d$ is the number of digits (which is $\log_{10} N$). Thus, for all digits, it takes $O(\log_{10} N \cdot \log_{10} N) = O((\log_{10} N)^2)$.

### Step 4: *Comparing sums*
Finally, compare the calculated sum to the original number. If the sum equals the original number, then the number is an Armstrong number. Otherwise, it is not. For $153$, since $153 = 153$, it confirms that $153$ is indeed an Armstrong number.

- **Time Complexity**: $O(1)$
- **Reason**: Simply comparing two integers.

### Final Time Complexity
The overall time complexity of the algorithm is dominated by the power sum calculation step:

$$O((\log N)^2)$$



This represents the quadratic nature of the operations concerning the number of digits in the number $N$.

## Pseudo Code

```cpp
bool isArmstrong(int n) {
    // Step 1: Determine the number of digits by counting the number of digits
    int d = 0;
    int temp = n;

    while (temp > 0) {
        temp = temp / 10;
        d = d + 1;
    }

    // Step 2: Initialize sum variable
    int armstrongSum = 0;
    // Reset temp to the original number after being done
    temp = n;


    // Step 3: Extract digits and calculate the sum of powers
    while (temp > 0) {
        // Get the last digit
        int digit = temp % 10;
        // Raise the digit to the power of d and add to the sum
        armstrongSum = armstrongSum + (digit ^ d);
        // Remove the last digit from temp
        temp = temp / 10;
    }

    // Step 4: Compare the sum with the original number
    if (armstrongSum == n)
        return true;  // n is an Armstrong number
    else
        return false; // n isn't an Armstrong number
}
```

## Implementations
- [TheAlgorithms](https://the-algorithms.com/algorithm/aliquot-sum)

## Sources
- [Wikipedia](https://www.wikiwand.com/en/articles/Narcissistic_number)
- [Azim Premji University](https://publications.azimpremjiuniversity.edu.in/3157/1/07_satvik_notearmstrongnumbers.pdf) (PDF)
- [GeeksForGeeks](https://www.geeksforgeeks.org/program-for-armstrong-numbers/)