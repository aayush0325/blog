---
title: "Optimizing matrix multiplication"
description: "A deep dive into making the backbone of neural nets performant."
pubDate: 2026-03-01
---

## Introduction

Matrix multiplication is the backbone of linear algebra. It is used in a wide range of applications, including computational fluid dynamics, machine learning, deep learning, computer graphics, and many more. I got introduced to numerical computing in my second year of college when i stumbled upon [stdlib-js](https://github.com/stdlib-js/stdlib), a javascript library for numerical computing. I was amazed by the fact that we could do numerical computing in javascript and out of curiosity I started contributing to it.

This was a really fruitful experience for me and led to me being selected as one of the contributors for the [Google Summer of Code](https://summerofcode.withgoogle.com/) program in 2025, where I worked on implementing LAPACK routines in javascript. This was a gentle introduction for me into the world of high performance computing, I learned about cache locality, loop re-ordering, loop tiling and other optimization techniques that are used to make such routines performant. I'm really grateful to the mentors and maintainers of the project for guiding me in a way that encourages my curiosity to go deeper.

After the program ended I read about SIMD instructions work, how OpenMP can be used to optimize such operations across multiple cores and how and why GPUs are so good at such tasks. I'm writing this blog to summarize the key insights I gained and share them with the world.

## Introduction to GEMM



## The Naive Approach

The standard $O(n^3)$ algorithm look like this:

```cpp
for (int i = 0; i < N; ++i) {
    for (int j = 0; j < N; ++j) {
        for (int k = 0; k < N; ++k) {
            C[i][j] += A[i][k] * B[k][j];
        }
    }
}
```

## Memory Hierarchy and Cache Locality

Computers aren't magic. Memory access patterns matter.

## Tiling / Blocking

Breaking matrices into smaller "tiles" that fit in cache.

## SIMD Vectorization

Using AVX/AVX-512 to do multiple additions/multiplications in a single clock cycle.

## Parallelization with OpenMP/Pthreads

Many cores, many threads.

## Conclusion

We've gone from naive $O(n^3)$ to a highly optimized implementation.
