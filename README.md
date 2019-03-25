# Project 2 - Greedy vs. Exhaustive Performance Comparison 
A project for CPSC 335 Algorithm Engineering at CSUF

## Created by 
[Dayna Anderson](dayna.anderson@csu.fullerton.edu)

[Stephen Lastimosa](slastimosa@csu.fullerton.edu)

[Jon Moubayed](jonmoubayed@csu.fullerton.edu)

## Requirements
This project will implement and compare two algorithms that solve the same problem. The first is a greedy algorithm with a fast (polynomial) running time, while the second is an exhaustive search algorithm with a slow (exponential) running time.

Both algorithms will solve the problem of planning a high-protein diet. More specifically, given a set of many food items available to eat, these algorithms pick a subset of foods that fit within a given calorie budget while maximizing protein content.

The premise of our problem is that a person wants to choose foods that maximize protein (measured in units of grams) while staying within a set calorie budget (measured in units of kilocalories, commonly called just “calories”). This problem can generalize to any other kind of dietary optimization; we could just as easily minimize fat within a calorie budget, maximize omega-3 acids within a calorie budget, minimize calories while meeting all vitamin requirements, and so on. We’re choosing protein somewhat arbitrarily to make this a concrete problem, and because calorie and protein data are both easily obtainable.

This problem actually reduces to the knapsack problem covered in section 6.9 of ADITA. In the knapsack problem, the input is a weight budget, and set of abstract “objects,” each with a weight and value; and the goal is to pick a subset of objects, that fit within a weight budgets, and maximize the total value. The high-protein diet problem is essentially the same problem, where a food corresponds to an object, calories correspond to weight, and protein corresponds to value.

Note that we require each food’s calorie value c>0 to be positive; we are omitting zero-calorie foods, such as water and diet soda, which never contain protein.

This problem actually reduces to the knapsack problem covered in section 6.9 of ADITA. In the knapsack problem, the input is a weight budget, and set of abstract “objects,” each with a weight and value; and the goal is to pick a subset of objects, that fit within a weight budgets, and maximize the total value. The high-protein diet problem is essentially the same problem, where a food corresponds to an object, calories correspond to weight, and protein corresponds to value.

You must implement the following two algorithms for the high-protein diet problem.

The first uses the greedy pattern. The greedy heuristic is to always choose the highest-protein food that fits within the calorie budget.

```python
greedy_max_protein(C, foods):
    todo = foods
    result = empty vector
    result_cal = 0
    while todo is not empty:
        Find the food f in todo of maximum protein.
        Remove f from todo.
        Let c be f’s calories.
    if (result_cal + c) <= C:
        result.add_back(f)
        result_cal += c
    return result
```

The second uses a proper exhaustive search.
```python
exhaustive_max_protein(C, foods):
    best = None
    for candidate in subsets(foods):
        if total_calories(candidate) <= C:
            if best is None or
                total_protein(candidate) > total_protein(best):
                    best = candidate
    return best
```

Our theory predicts that the O(2^n⋅n) exhaustive search algorithm will be far slower than the greedy algorithm with its O(n^2) or O(n logn) time complexity. Your experiment will show whether this is the case.


## Implementation
Project skeleton files provided by the professor with the following implementations in maxprotein.hh by our team.
* filter_foods()
* greedy_max_protein()
* exhaustive_max_protein()

## Execution
```
$ make 
$ ./simulator in1.txt
```