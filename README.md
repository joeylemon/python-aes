# python-aes
![Test](https://github.com/joeylemon/python-aes/workflows/Test/badge.svg)

An implementation of the Advanced Encryption Standard (AES/Rijndael) algorithm in Python, following the Federal Information Processing Standards Publication 197 ([FIPS-197](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)) specification sheet.

## Motivation

As students in COSC483: Applied Cryptography at the [University of Tennessee Knoxville](https://utk.edu), we were tasked with implementing the AES algorithm from scratch in any programming language of our choice. This involved implementing finite field arithmetic, key expansion routines, the cipher (encrypt) function, and the inverse cipher (decrypt) function. The only resources behind the algorithm which we were allowed to use was the [FIPS Publication 197](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf), an [animation](https://www.youtube.com/watch?v=gP4PqVGudtg), a [stick figure guide](http://www.moserware.com/assets/stick-figure-guide-to-advanced/A%20Stick%20Figure%20Guide%20to%20the%20Advanced%20Encryption%20Standard%20%28AES%29.pdf), and [Wikipedia's write-up for AES](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard). I followed these instructions and only used the given resources, with almost 98% of my time spent looking over FIPS-197.

FIPS-197 provides a plethora of information to assist in implementing the AES algorithm. Among the provided information is the test output in Appendix C, which provides step-by-step values for each round of the cipher and inverse cipher routines. This program matches the output from Appendix C exactly.

## How to Use

This program requires [Python3](https://www.python.org/downloads/). It was specifically tested with Python v3.9.0.

To run the program with default output similar to Appendix C of FIPS-197, simply run the command:
```sh
> python aes.py
```

Depending on your Python installation, you might have to explicity specify Python3:
```sh
> python3 aes.py
```

## How to Test

This program is accompanied by a suite of unit tests designed to ensure the correct functionality of every routine involved in the AES algorithm. To run the unit tests, simply run the command:
```sh
> python -m unittest test.py -v
```

You should see an output similar to:
```
test_ff_add (test.TestArithmetic) ... ok
test_ff_multiply (test.TestArithmetic) ... ok
test_xtime (test.TestArithmetic) ... ok
test_decrypt (test.TestCipher) ... ok
test_encrypt (test.TestCipher) ... ok
test_inverses (test.TestCipher) ... ok
test_rounds (test.TestCipher) ... ok
test_key_expansion (test.TestExpansion) ... ok
test_rot_word (test.TestExpansion) ... ok
test_sub_word (test.TestExpansion) ... ok
test_matrix_to_text (test.TestUtilities) ... ok
test_text_to_bytes (test.TestUtilities) ... ok
test_text_to_matrix (test.TestUtilities) ... ok

----------------------------------------------------------------------
Ran 13 tests in 0.018s

OK
```
