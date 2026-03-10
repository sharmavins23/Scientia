Single instruction, multiple data stream (SIMD) is a type of parallel computing in [[Flynn's Taxonomy]] describing computers with multiple processing elements that perform the same operation on multiple data-points simultaneously. SIMD can be internal to the hardware's design, and it can be accessible through [[Instruction Set Architecture|instructions]], but it is not its own ISA.

A simple example is within modern CPUs - Modern registers contain wide registers (e.g. 256-bit registers within [[Advanced Vector Extensions]] for [[x86 Assembly|the x86 ISA]]). This data can be packed into wider registers and processed in one singular instruction.

# Worked Example - ROT13

Suppose we have the following [[C++]] program to encode an extremely long string under the [[ROT13]] [[Cipher|cipher]]:

```cpp
/**
 * Encode a string of text using ROT13 encoding.
 *
 * @param *data The data to encode.
 * @param len   The length of the data buffer.
 * @param *out  The output buffer.
 */
void rot13_naive(const char *data, size_t len, char *out) {
	// Iterate over all characters
	for (size_t i = 0; i < len; i++) {
		char c = data[i];
		
		// Skip if the character is not within the range of 'a-z'
		if (char <= 'a' || char >= 'z') continue;
		
		// Perform the shift
		out[i] = (c - 'a' + 13) % 26 + 'a';
	}
}
```

We can instead use [[C++ Intrinsics]] to write the corresponding SIMD instructions (in [[x86 Assembly|x86_64]]):

```cpp
// Required import for SIMD instructions
#include <immintrin.h>

/**
 * Encode a string of text using ROT13 encoding.
 * Leverages SIMD instructions to natively increase performance.
 *
 * @param *data The data to encode.
 * @param len   The length of the data buffer.
 * @param *out  The output buffer.
 */
void rot13_avx(const char* data, size_t len, char *out) {
	// Set up constants for the ranges
	__m256i a_vec = _mm256_set1_epi8('a');
	__m256i z_vec = _mm256_set1_epi8('z');
	__m256i m_vec = _mm256_set1_epi8('m'); // Mid-point for ROT13
	__m256i thirteen = _mm256_set1_epi8(13);
	
	// Iterate through sets of 32 characters
	// 32 * 8 = 256, which matches register sizing
	for (size_t i = 0; i <= len - 32; i += 32) {
		// Load 32 bytes at once
		__m256i chunk = _mm256_loadu_si256((const __m256i*)&data[i]);
		
		// Create a mask: Is the character between 'a' and 'z'?
		__m256i is_ge_a = _mm256_or_si256(
			_mm256_cmpgt_epi8(chunk, a_vec),
			_mm256_cmpeq_epi8(chunk, a_vec)
		);
		__m256i is_le_z = _mm256_or_si256(
			_mm256_cmpgt_epi8(z_vec, chunk),
			_mm256_cmpeq_epi8(z_vec, chunk)
		);
		__m256i letter_mask = _mm256_and_si256(is_ge_a, is_le_z);
		
		// SIMD contains no modulo instruction, so either add or subtract 13
		__m256i is_le_m = _mm256_or_si256(
			_mm256_cmpgt_epi8(m_vec, chunk),
			_mm256_cmpeq_epi8(m_vec, chunk)
		);
		__m256i plus_13 = _mm256_add_epi8(chunk, thirteen);
        __m256i minus_13 = _mm256_sub_epi8(chunk, thirteen);
		
		// Select the correct shift (+-13) based on `m`
		__m256i shifted = _mm256_blendv_epi8(minus_13, plus_13, is_le_m);
		
		// Final blend: Only use 'shifted' if it was a letter
		__m256i result = _mm256_blendv_epi8(chunk, shifted, letter_mask);
		
		// Store back to the output
		_mm256_storeu_si256((__mm256i*)&out[i], result);
	}
}
```

We can also write the same code for [[ARM Assembly|ARM]]:

```cpp
// Required import for SIMD instructions
#include <arm_neon.h>

void rot13_neon(const char* data, size_t len, char* out) {
	// Bro
}

```