---
layout: project
title: python-practice
category: projects
tags: python
---

## Summary

I first used Python at my internship at [Nypro(now Jabil Healthcare Engineering & Technology)](https://www.jabil.com/industries/healthcare.html){:target="\_blank" rel="noopener noreferrer"}, and ended up taking a full course on Python in my last semester at USF. In an attempt to improve my Python I collected some of the classes and methods I had written or thought of and refactor them.

The collection breaks down into the following two modules:

- Collections
  - DefaultOrderedDict: a dictionary that respects both order of insertion and a default value for missing keys
  - Fold: my implementation of `foldr` and `foldl`
  - Group: groups elements from a list based on certain configurations
  - KeyIgnorer: a dictionary that ignores changes to already existing keys
- Console
  - Printing: a utility for getting choices and drawing fake progress bars in the terminal

## Lessons Learned

One of the goals of writing these collections of classes and utilities was to make it generally applicable and useful to more than just myself. While working on it, I quickly realized that building useful abstractions that are useful to a wide audience is quite difficult. Starting without specific requirements will lead to an explosion of parameters.
