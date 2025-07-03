## Shor's Algorithm Oracle

**Shor's algorithm** is a quantum algorithm for efficiently factoring large integers, threatening classical encryption methods such as RSA. The core idea involves finding the period \( r \) of the function (which is the smallest integer that satisfies:

$$
f(x)=s^x \mod N
$$

where:

- **N** is the integer to factor.
- **a** is a randomly chosen integer coprime to N.

---

### What is the oracle?

The **oracle** in Shor's algorithm is the quantum circuit that performs **modular exponentiation**, implementing the transformation taking two inputs $a,N$ positive integers such that $a<N$ and output the following:

$$
|x>_1 |a y \bmod N>  \text{if } x=1 \text{ and } 0 \leq y < N,
$$
 It leaves the input register |x⟩ unchanged while computing the function in superposition and storing the result in an output register.

---

### Why is it needed?

The period-finding subroutine (using the Quantum Fourier Transform) requires evaluating **f(x)** coherently across all inputs. The oracle:

- Encodes the **periodicity information** into the quantum state.  
- Allows extraction of the period \( r \) by measuring after applying the QFT.

---

### Implementation notes

- Built from **modular multiplication** and **modular addition** circuits using controlled operations.  
- Typically constructed via **repeated squaring** techniques to implement modular exponentiation efficiently.  
- Optimizing the oracle is crucial to reduce gate depth and error in real quantum hardware.
