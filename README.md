# Assignment-4-Intro-to-R
## Name: Saloni Dixon 
## Programming Language: R
## Date: 11/09/23
### Description 
For this assignment, a R script was created in order to implement additional practice with the fundamental R programming concepts and data manipulation techniques, understanding of how to use R basic vectors and matrices, loops, and conditional loops in R programming, create basic objects in R, carry out mathematical operations in R, installing R libraries, using R functions to perform statistical operations and measurements, and managing a Git repository.

### Required Files: 
Auto: gas mileage, horsepower, and other information for 392 vehicles data. This dataset was taken from the StatLib library which is maintained at Carnegie Mellon University.
The dataset was used in the 1983 American Statistical Association Exposition.

### Required Packages: 
ISLR: data for an introduction to statistical learning with applications in R

### Execution: 
1. Created a vector containing numbers from 1 to 50.
```
numbers <- 1:50
```
2. Created a 5x10 matrix using vectors.
```
matrix_5x10 <- matrix(numbers, nrow = 5, ncol = 10, byrow = TRUE)
```
3. Created a logical matrix based on the condition of the values of the matrix being evenly divisible by 3 or has a remainder of 1 when divided by 6.
```
logical_matrix <- (matrix_5x10 %% 3 == 0) | (matrix_5x10 %% 6 == 1)
```
4. Extracted the values based on the logical matrix.
```
extracted_values <- matrix_5x10[logical_matrix]
```
5. Define the Hailstone function.
```
hailstone <- function(x) {
  cycles <- 0
  while (x != 1) {
    if (x %% 2 == 0) {
      x <- x / 2
    } else {
      x <- x * 3 + 1
    }
    cycles <- cycles + 1
  }
  return(cycles)
}
```
6. Applied the Hailstone fucntion to the extracted values and then printed the values.
```
cycle_counts <- sapply(extracted_values, hailstone)
cycle_counts
```
7. Installed the ISLR library and load the Auto dataset.
```
# install & load the ISLR library
install.packages("ISLR")
library(ISLR)

# load the Auto dataset
data("Auto")
```
8. Removed qualitative data columns
```
Auto_numeric <- Auto[, sapply(Auto, is.numeric)]
```
9. Wrote a loop through columns and printed the range of each quantitative variable.
```
for (col in names(Auto_numeric)) {
  cat("Range of", col, ":", range(Auto_numeric[[col]]), "\n")
}
```
10. Created a matrix containing the mean and standard deviation of each column.
```
summary_matrix <- matrix(0, nrow = 2, ncol = ncol(Auto_numeric) * 2, 
                        dimnames = list(c("Mean", "SD"), rep(names(Auto_numeric), each = 2)))

for (col in names(Auto_numeric)) {
  summary_matrix["Mean", col] <- mean(Auto_numeric[[col]])
  summary_matrix["SD", col] <- sd(Auto_numeric[[col]])
}
```
11. Identified rows with less than the mean amount of mpg and removed them.
```
mean_mpg <- mean(Auto$mpg)
Auto_filtered <- Auto[Auto$mpg >= mean_mpg, ]
```
12. Recalculated the mean and standard deviation, and then printed the results.
```
Auto_numeric_filtered <- Auto_filtered[, sapply(Auto_filtered, is.numeric)]
summary_matrix_filtered <- matrix(0, nrow = 2, ncol = ncol(Auto_numeric_filtered) * 2, 
                                  dimnames = list(c("Mean", "SD"), rep(names(Auto_numeric_filtered), each = 2)))

for (col in names(Auto_numeric_filtered)) {
  summary_matrix_filtered["Mean", col] <- mean(Auto_numeric_filtered[[col]])
  summary_matrix_filtered["SD", col] <- sd(Auto_numeric_filtered[[col]])
}

print("Original Summary Matrix:")
print(summary_matrix)
print("\nFiltered Summary Matrix:")
print(summary_matrix_filtered)
```
13. In Python, I believe that the same tasks can be accomplished by using libraries like Numpy and pandas, which provide similar functionality to R. Granted, the syntax and specific functions may vary, but the overall logic and approach remain consistent across both of the languages.
Both languages have similar functionality for data manipulation, matrix operations, and statistical analysis. For instance, R has a concise syntax for matrix operations, and its data manipulation and statistical packages (like dplyr and ggplot2) make certain tasks more straightforward. On the other hand, Python, with libraries like NumPy and pandas, provides readability and versatility. It is often preferred for its general-purpose programming capabilities.
Personally, I think that I prefer Python over R. Python perfroms a wide range of tasks beyond bioinformatics, such as web development, automation, and machine learning. Overall, its versatility is such a valuable skill that can be translated in various domains! Furthermore, I find the syntax to be really straightforward and easier to read, which makes it very easy to write and maintain code. 
