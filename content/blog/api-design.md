---
title: Don’t just write APIs DESIGN them!
date: "2019-07-21T22:12:03.284Z"
description: "A small guide to help you design your next API in a better way."
---

This post is heavily inspired by the paper published by Jasmin Blanchette on June 19, 2008, titled “The Little Manual of API Design”. You can read the paper by going [here](https://github.com/papers-we-love/papers-we-love/blob/master/api_design/api-design.pdf).

#### What exactly is an API?

According to Wikipedia, An Application Programming Interface (API) is a set of functions, procedures, methods or classes used by computer programs to request services from the operating system, software libraries or any other service providers running on the computer. A computer programmer uses the API to make application programs.

An API is pretty much the building blocks of any application, and it is really important to write those very deliberately and with utmost care. Given below is a small guide that can help you design better APIs.

> Software is built on abstractions. Pick the right ones, and programming will flow naturally from design; modules will have small and simple interfaces; and new functionality will more likely fit in without extensive re-organisation. Pick the wrong ones, and programming will be a series of nasty surprises. - Daniel Jackson

#### Easy to Learn and Memorise

An API should be easy to learn and memorize. Suppose you have an API to get apples from a tree, and you name the method to get the apples from the tree as `apples()` It will be really hard for another developer who is going to use this API to know what the `apples()` method is going to do. While naming your APIs, focus on making there purpose easily understandable. For example, the method to get apples from a tree can be called as `getApplesFromTree()` or `fetchApplesFromTree()` and they instantly make sense to another developer, what the method is actually going to do. Supposedly the tree has different kinds of fruits the developer need not think very hard as what the method to get Oranges from the tree will be. A more concrete example in real life can be seen in the React library, the lifecycle methods in react are so awesomely named, you can just tell when will a lifecycle method be called by their name only. for example, `componentWillMount()`, `componentDidMount()`, and so on.

#### Readable Code

```
// Bad Code Example
const capitalizeAndAddDotAtTheEnd = (word) => {
  return word[0].toUpperCase() + word.slice(1) + ".";
};
// Good Code Example
const capitalizeFirstLetterOfWordAndAddDotAtTheEnd = (word) => {
  const firstLetter = word[0];
  const remainingLetters = word.slice(1);
  return firstLetter.toUpperCase() + remainingLetters + ".";
}
```

The above-given functions both do the same thing but one of them is more expressive than the other one, going with fewer lines of code and compromising readability is not a good choice. Application code is written once but is read over and over again by different developers over the lifetime of the application. When you are writing code, have more focus on readability than just performance. Most of the time when it comes to readability vs performance, choosing readability is most often the best thing to do.

#### Hard to Misuse

A well-designed API makes it easier to write correct code than incorrect code and encourages good programming practices. In the above-given example, the actual intention of `capitalizeAndAddDotAtTheEnd()` was to take a WORD, capitalize the first letter and add a dot to it, but because of the name, the first impression of the method was not clear. But in the second example, the method `capitalizeFirstLetterOfWordAndAddDotAtTheEnd()` is very verbose and tells exactly what it is expecting, in general, if you see it for the first time you will always pass a word to that method in place of passing a sentence. If you are really precise and clear with your intentions, it will be really hard to misuse the API.

#### Easy to Extend

While designing API methods try to think a step ahead. Taking the same tree analogy as we discussed earlier, a tree that can have all kinds of fruits, suppose you design a method `getOranges()` and tomorrow you need to make a method to get apples from the same tree and you write `getApples()` , if you keep on doing this you won’t be able to extend the code that you wrote to get oranges from the tree in the first place. Try to generalize things wherever possible. For example in the above analogy, you can design a method called `getFruits()` and pass the name of the fruit as an argument, this will make your code a lot easier to extend. Now every time there is a new fruit in the tree you won’t have to write the method again and again but you can just re-use your `getFruits()` method and get the job done.

#### Resources and Further Readings.

[Research Paper published by Jasmin Blanchette on API design](https://github.com/papers-we-love/papers-we-love/blob/master/api_design/api-design.pdf)

[How to design APIs and why it matters?](https://www.youtube.com/watch?v=aAb7hSCtvGw)

[Code is for humans. A talk by Kyle Simpson on writing code for humans and not just for computers.](https://frontendmasters.com/teachers/kyle-simpson/code-is-for-humans/)
