id: app-development-gini-interfaces-di
summary: interfaces and di
authors: Shay markovich

# Interfaces and di

<!-- ------------------------ -->
##General
In this codelab you will learn about interfaces and DI

<!-- ------------------------ -->
## Interfaces

### What it used for
Interfaces are used for:
- Seperate of consern
- The consumer class only knows about the function that are in the interfance and don't care about other function or implemtation details
- Allow changing the implementation of the function, this can be in for test fakes or other implementations

<!-- ------------------------ -->
## DI - dependency injection
Dependency injection are used for 

### What are they use for

### Manual

### Service locator

### Dagger
A google di framework that helps inject dependentis
in android we can use Android

it has component, Module
**please look at:**
[Using Dagger in Android apps](https://developer.android.com/training/dependency-injection/dagger-android)

### Hilt
Hilt is a di framework base on Dagger but already have all the componnents needed for android

**please look at:**
[Dependency injection with Hilt](https://developer.android.com/training/dependency-injection/hilt-android)


### Koin
Koin is a di framework in kotlin

It have Modules that contains single, factory

We get the dependency by using the "by inject()" delagate function

**please look at:**
[Koin in android](https://insert-koin.io/docs/quickstart/android)