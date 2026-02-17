# @natokpe/shannon-entropy

This library provides a high-performance, mathematically accurate suite for Shannon Information Theory metrics. It features a unified API that handles both raw data (frequency analysis) and pre-calculated probability distributions.

## Features

*   **Unified API**: Overloaded functions that accept `string`, `Buffer`, `Uint8Array`, or `number[]`.
*   **Comprehensive Metrics**: Includes Shannon, Binary, Joint, Conditional, and Relative (KL Divergence) entropies.
*   **Zero Dependencies**: Extremely lightweight and tree-shakeable.
*   **Environment Agnostic**: Works seamlessly in Node.js and modern browsers.
*   **TypeScript Ready**: Built with full type definitions and IDE autocomplete support.

## Installation

```bash
npm install @natokpe/shannon-entropy
```

## Usage

### 1. Basic Entropy
Calculate the average uncertainty. Pass a probability distribution or raw data.

```javascript
import { entropy } from '@natokpe/shannon-entropy';

// From a probability distribution
entropy([0.5, 0.5]); // returns 1

// From a string (frequency analysis)
entropy("aaaaa"); // returns 0
entropy("abcde"); // returns 2.3219...
```

### 2. Binary Entropy
Specialized function for Bernoulli trials (success/failure).

```javascript
import { binaryEntropy } from '@natokpe/shannon-entropy';

// H_b(p) where p = 0.5
binaryEntropy(0.5); // 1.0
```

### 3. Joint and Conditional Entropy
Measure how two variables interact.

```javascript
import { jointEntropy, conditionalEntropy } from '@natokpe/shannon-entropy';

const dataX = "abab";
const dataY = "aaaa";

// Total uncertainty of the combined system
jointEntropy(dataX, dataY); 

// Uncertainty of Y given that X is known
conditionalEntropy(dataY, dataX); 
```

### 4. Relative Entropy (KL Divergence)
Measure the "distance" between two probability distributions.

```javascript
import { relativeEntropy } from '@natokpe/shannon-entropy';

const P = [0.9, 0.1];
const Q = [0.5, 0.5];

relativeEntropy(P, Q); // D_KL(P || Q)
```

## API Reference

### `entropy(input: number[] | string | Uint8Array | Buffer): number`
Returns the Shannon entropy in bits. Handles $0 \log 0 = 0$ convention.

### `binaryEntropy(p: number): number`
Returns the binary entropy for a single probability $p$.

### `jointEntropy(arg1, arg2?): number`
Calculates $H(X, Y)$. Accepts a 2D probability matrix or two sequences of equal length.

### `conditionalEntropy(arg1, arg2): number`
Calculates $H(Y|X)$. Accepts (JointMatrix, MarginalX) or (DataY, DataX).

### `relativeEntropy(P: number[], Q: number[]): number`
Calculates the Kullback-Leibler divergence between two distributions.

## Contributing

Contributions are welcome! Whether you are fixing a mathematical edge case or optimizing the frequency analysis, please follow these steps:

1. **Fork** the repository on GitHub.
2. **Clone** your fork.
3. **Install** dependencies: `npm install`.
4. **Create** a feature branch: `git checkout -b feature/amazing-feature`.
5. **Test** your changes: `npm test`.
6. **Commit** your changes: `git commit -m 'Add some amazing feature'`.
7. **Push** to the branch: `git push origin feature/amazing-feature`.
8. **Open** a Pull Request.

## Issues

If you find a bug or have a suggestion for a new entropy variation, please open an issue in the GitHub Issue Tracker.

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct. Please read the full [Contributor Covenant](https://www.contributor-covenant.org) before contributing.

## Security

If you discover a security vulnerability, please do not open a public issue. Instead, please email the project maintainer directly.

## License

[MIT](https://opensource.org) © [natokpe](https://github.com)
