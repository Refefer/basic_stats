basic_stats
===========

A command-line tool to calculate basic summary statistics on a set of numbers.  It handles numbers embedded in strings (ie. "22.5%" or "$10.32") with variable delimiters.

Flags
---
    -F Delimiter: Delimiter to use.  Default is whitespace.  This can also take regular expressions
    -v field=COLUMN: Which column to look for the numbers.  Default is the last column.
    -v scalar=SCALAR: How much to scale each number before calculations.  Useful for representation.
    -v buckets=SCALAR: How many buckets to show in the histogram.
    -v nines=SCALAR: How many nines to show.

Usage
----

Example 1: CSV text file __salaries.csv__ with numbers in 3rd column.

        basic_stats -F, -v field=3 salaries.csv

Example 2: Whitespace delimited text file __country_gdp.txt__ containing percents in the 2nd column.

        basic_stats -v field=2 country_gdp.txt

Example 3: Tail of the last 1000 lines from multiple log files where the numbers are in the last column, whitespace delimited.  Show with 5 Nines and 20 buckets

        tail -n 1000 apache.*.log | basic_stats -v nines=5 -v buckets=20
