# CSE 220 Homework 5 Starter Kit

Read the assignment description first. It has the full rules, all the examples,
and the grading breakdown. This file only covers how to build and run things.

## What is in here

    Makefile             builds everything into build/
    matrix.h             the four prototypes, do not change
    matrix.c             write your code here
    matrixHelpers.h      provided helpers, do not change
    matrixHelpers.c      provided helpers, do not change
    tests/test_matrix.c  your Criterion tests

## Building and running

    make          build your code and the tests into build/
    make test     build if needed, then run every test
    make clean    remove build/
    make objects  compile only matrix.c, without Criterion

The Makefile compiles with `-Wall -Wextra -Werror -std=c11`, so any warning
stops the build. The starter kit compiles as given, and the sample tests fail
until you implement the functions. That is expected.

## Criterion

The tests use Criterion, which is already installed on the lab machines, so
`make test` works there with no setup.

On your own machine, install it first:

    macOS (Homebrew):   brew install criterion
    Ubuntu or Debian:   sudo apt install libcriterion-dev

The Makefile finds Criterion through pkg-config, and falls back to
`-lcriterion` if pkg-config does not know about it.

## The helpers

`matrixHelpers.h` gives you two functions for your tests:

    int matricesEqual(int rows, int cols, const int A[rows][cols], const int B[rows][cols]);
    void printMatrix(const char *label, int rows, int cols, const int M[rows][cols]);

`matricesEqual` checks a whole output matrix in one assertion, which is how the
TAs check your work too:

    int expected[2][3] = {{2, 6, 12}, {20, 30, 42}};
    cr_assert(matricesEqual(2, 3, A, expected));

`printMatrix` prints a labeled matrix while you debug. Use the helpers only in
your tests, never inside `matrix.c`.

## What you have to write

* The four functions in `matrix.c`, using pointer arithmetic for every matrix
  element. Write `*(*(M + i) + j)`, not `M[i][j]`. This is worth 10 points and
  is checked by reading your code.
* At least 5 Criterion tests per function in `tests/test_matrix.c`, which is 20
  in total. Check the output matrices, not only the return values.
* Your name and SBU ID in a comment at the top of every file you write.

## Submitting

You submit through CodeGrade, not as a ZIP file. Open the HW5 link on
Brightspace and CodeGrade opens with all of the files above already in its
editor. Edit `matrix.c` and `tests/test_matrix.c` there. If you built and tested
them on your own machine, copy your finished versions into the editor. Then
hand in.

Do not delete or rename any file. Changes to `Makefile`, `matrix.h`,
`matrixHelpers.h` and `matrixHelpers.c` are ignored when your code is tested, and
they are flagged for the TAs to review.
