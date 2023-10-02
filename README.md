# Restaurant Review System

## Phase 3 Week 2 : Object Relations Code Challenge - Restaurants

[![license](https://img.shields.io/badge/license-%20MIT%20-green.svg)](./LICENSE)
![python version](https://img.shields.io/badge/python-3.10.12+-blue.svg)
![pytest version](https://img.shields.io/badge/pytest-7.1.3+-cyan.svg)
![platforms](https://img.shields.io/badge/Platforms-Linux%20|%20Windows%20|%20Mac%20-purple.svg)

## Introduction

This repo contains code for a restaurant review system for Phase 3 Week 2 Code Challenge based on python classes and instances, class and instance methods, variable scope, object relationships, and lists and list methods working with a Yelp-style domain.

This project utilizes the `pytest` library for testing purposes. The `pytest framework` makes it easy to write small, readable tests, and can scale to support complex functional testing for applications and libraries.

*The test suite encompases all deliverables for this code challenge. All tests should be passing.*

## Table of Contents

- [Features](#features)
- [Project Setup](#project-setup)
- [Usage](#usage)
- [Examples](#examples)
- [Assignment Details](#assignment-details)
- [Author & License](#author--license)

## Features

- Create and manage customer profiles
- Add and retrieve reviews for restaurants
- Calculate average star ratings for restaurants
- Find customers and restaurants based on reviews
- Retrieve a list of all reviews

## Project Setup

### 1. Clone the repository

```python
git clone https://github.com/ArshavineRoy/restaurants-code-challenge
```

### 2. Navigate to the project's directory

```python
cd restaurants-code-challenge
```

### 3. Install all the required dependencies

The root directory of this repository contains the `Pipfile` with all the required Python libraries for this project and restricts them to this repository.

To install `pytest` and any other required libraries, run:

```python
pipenv install
```

### 4. Enter the pipenv shell

```python
pipenv shell
```

### 5. Use pytest to run the test suite

Tests for this project are contained in the `testing` directory, and are based on the deliverables for this code challenge.

`Pytest` provides useful information about what went right or wrong with the code:

- Which tests passed/didn't pass
- Why each failing test failed (the difference between the expected output and the actual output)
- The line number of the failing test

**All tests should be passing.*

To run the test suite, use the following in the `pipenv shell`:

```python
pytest
```

## Usage

You can use the Restaurant Review System to simulate interactions between customers, restaurants, and reviews. Follow these steps to get started:

1. Create customer and restaurant instances.
2. Add reviews using the add_review method.
3. Retrieve information about customers, restaurants, and reviews using the provided methods.

## Examples

```python
customer1 = Customer("John", "Doe") # Create customer profiles
customer2 = Customer("Jane", "Smith")
customer3 = Customer("John", "Johnson")
review1 = Review("John Doe", "Highlands", 3)
review2 = Review("Mike Posner", "Azuri", 5)
review3 = Review("Jane Doe", "Kilimanjaro Jamia", 2)
review4 = Review("Ed Sheeran", "Highlands", 4)
review5 = Review("Ed Sheeran", "Highlands", 4)
restaurant1 = Restaurant("Highlands")
restaurant2 = Restaurant("Kilimanjaro Jamia")
customer1.add_review(restaurant1, 4) # Add reviews for restaurants
customer1.add_review(restaurant2, 5)
customer2.add_review(restaurant1, 3)

print(customer1.first_name) 
print(customer1.reviews()) # Find customers reviews
print(restaurant1.reviews())  # Find restaurant reviews
print(restaurant1.average_star_rating()) # Calculate average star ratings for restaurants
print(Review.all()) # Retrieve a list of all reviews
```

## Assignment Details

For this assignment, we'll be working with a Yelp-style domain.

We have three models:

- `Restaurant`
- `Customer`
- `Review`

For our purposes, a `Restaurant` has many `Reviews`, a `Customer` has many `Review`s, and a `Review` belongs to a `Customer` and to a `Restaurant`.

`Restaurant` - `Customer` is a many-to-many relationship.

**Note**: You should draw your domain on paper or on a whiteboard *before you start coding*. Remember to identify a single source of truth for your data.

### Topics

- Classes and Instances
- Class and Instance Methods
- Variable Scope
- Object Relationships
- lists and list Methods

### Instructions

*To get started, use this Pipfile to install all dependencies required for this project.*

*Build out all of the methods listed in the deliverables. The methods are listed in a suggested order, but you can feel free to tackle the ones you think are easiest. Be careful: some of the later methods rely on earlier ones.*

*Note!  - You'll need to create your own test sample instances so that you can try/test out your code. Make sure your relationships and methods work in the console before submitting.*

*Writing error-free code is more important than completing all of the deliverables listed - prioritize writing methods that work over writing more methods that don't work. You should test your code in the console as you write.*

*Similarly, messy code that works is better than clean code that doesn't. First, prioritize getting things working. Then, if there is time at the end, refactor your code to adhere to best practices. When you encounter duplicated logic, extract it into a shared helper method.*

*Before you submit! - Save and run your code to verify that it works as you expect. If you have any methods that are not working yet, feel free to leave comments describing your progress.*

## Deliverables

Write the following methods in the classes in the files provided. Feel free to build out any helper methods if needed.

#### Initializers, Readers, and Writers

`Customer`

- `Customer __init__()`
  - Customer should be initialized with a given name and family name, both strings (i.e., first and last name, like George Washington)"
- `Customer given_name()`
  - returns the customer's given name
  - should be able to change after the customer is created
- `Customer family_name()`
  - returns the customer's family name
  - should be able to change after the customer is created
- `Customer full_name()`
  - returns the full name of the customer, with the given name and the family name concatenated, Western style.
- `Customer all()`
  - returns **all** of the customer instances

`Restaurant`

- `Restaurant __init__()`
  - Restaurants should be initialized with a name, as a string
- `Restaurant name()`
  - returns the restaurant's name
  - should not be able to change after the restaurant is created

`Review`

- `Review __init__()`
  - Reviews should be initialized with a customer, restaurant, and a rating (a number)
- `Review rating()`
  - returns the rating for a restaurant.
- `Review all()`
  - returns all of the reviews

#### Object Relationship Methods

`Review`

- `Review customer()`
  - returns the customer object for that review
  - Once a review is created, should not be able to change the customer
- `Review restaurant()`
  - returns the restaurant object for that given review
  - Once a review is created, should not be able to change the restaurant

`Restaurant`

- `Restaurant reviews()`
  - returns a list of all reviews for that restaurant
- `Restaurant customers()`
  - Returns a **unique** list of all customers who have reviewed a particular restaurant.

`Customer`

- `Customer restaurants()`
  - Returns a **unique** list of all restaurants a customer has reviewed
- `Customer add_review(restaurant, rating)`
  - given a **restaurant object** and a star rating (as an integer), creates a new review and associates it with that customer and restaurant.

#### Aggregate and Association Methods

`Customer`

- `Customer num_reviews()`
  - Returns the total number of reviews that a customer has authored
- `Customer find_by_name(name)` class method
  - given a string of a **full name**, returns the **first customer** whose full name matches
- `Customer find_all_by_given_name(name)` class method
  - given a string of a given name, returns an **list** containing all customers with that given name

`Restaurant`

- `Restaurant average_star_rating()`
  - returns the average star rating for a restaurant based on its reviews
  - Reminder: you can calculate the average by adding up all the ratings and dividing by the number of ratings

## Author & License

Authored by [Arshavine Waema](https://github.com/ArshavineRoy).

Licensed under the [MIT License](LICENSE) - see the [LICENSE](LICENSE) file for details.
