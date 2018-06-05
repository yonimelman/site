---
title: "Developer Testing: How I learned to stop worrying and start testing"
date: 2018-06-05T07:00:17+03:00
tags: ["testing", "python"]
draft: false
---

"Why do I need testing? I write code with little or no bugs", "I tested my code! when I wrote it" or "Isn't it QA's responsibility?" 
are all sayings some of us make regarding testing. Sure, testing is an annoyance no developer wants to deal with.. 
after all, we're not quality assurance engineers. We write the code, the features, the business logic. 
And maybe they're even right. If you must deliver as soon as possible, it's easier to leave formality aside, 
crunch the code real fast, deliver and move to the next challenge. 

But in reality there's always a price, and for me, it is usually anxiety. I'll explain. 
Most of us don't work in a vacuum. What we do matters to other people, and of course to ourselves. 
What if this new component I built just doesn't do what it's supposed to do? anxiety! 
Someone needs to modify my code, or worst, I'm supposed to modify someone else's, who knows what could break... anxiety! 
I use someone else's code and they change it. will my component survive?... anxiety!

As I see it, the best way to confront all these terrible feelings is to regain control. 
I've written tests for my code for the last two years and i'm never going back. To me, testing doesn't delay work,
it's strengthening the ground beneath me, enabling me to really go fast and to deliver even better results.

I'd like to discuss some of the motivations to incorporate developer testing in your work:

#### Confidence
While developing, testing provides a methodical way of knowing, and persisting the knowledge that your component is doing what it needs to be doing.
This is because (proper) testing forces you to focus on the required behavior, and go above the implementation.
Writing tests for the business logic scenarios of your component, gives you the confidence that at any given time, you know the status of your code.
Of course, this "radical" approach requires you to actually write the tests before you've even written the code (also known as Test Driven Development - TDD).
But there are ways to enjoy a good level of certainty for a good period of your development time with less drastic measures. I'll discuss these in future posts.

Going beyond your ongoing work, providing a well tested component gives your colleagues and managers a high confidence that 
the code you've delivered is, at least, working and not breaking the rest of the system. 
This enables your code reviewer to focus on your implementation without fearing that any change she'll ask you to make would break something (leading to better code quality, which i'll discuss soon).
Other beneficiaries are the QA engineers who usually require a frozen state of the code to actually verify the component. This is because whenever somebody makes a change, a new risk is introduced to the system and they have to make sure all the components still work.
With your tested component, QA would have to spend far less (if any) time on it, ideally only verifying the integration of your component with the rest of the system as a whole (usually not covered by your tests).

Up to this point, these arguments are still not the enough for some of the stubborn developers. 
Usually developers who reject testing claim that they don't see a point to all the formality and additional effort.
They've delivered many components without writing proper tests for them. They just tested the code after development by running it, 
made sure that it works and delivered a good component to the system. It's understandable why have these rejections when they get the same apparent results with less the effort.
But it's important to understand, automated tests gives you confidence in the future. Whether you or someone else is going to be working on a system in the future, 
it makes a huge difference if it's backed by tests or not.

#### Improve code quality
Writing good tests forces you to write good code, simply because bad code is very hard to test.
When designing an implementation, and keeping the test requirement in mind, you'll make sure everything is structured as neatly as possible.
You'll identify over complication in no time, because its going to be harder to test it.

Another great thing about tests, is that they enable, not to say, promote the ability to refactor the code.
Features and components change all the time, sometimes even to the infrastructural level. In an untested system,
making changes is far more riskier, and you'll be inclined to perform the minimal operation to the code to enable
the changed request and in no time the system will be filled with specific ifs and patches. But, with a tested system,
there is far less risk and making the proper change is possible, if not encouraged.  


#### Realize design problems in advance
Because tests address the business logic of your component, it makes you think about the inputs and expected outputs of it.
You'll have to really dig deep into the behavior of your component, understanding it before writing or finalizing the code.

This helps a lot in cases where you get a complicated product design for the a feature. 
The product manager can swear he has all the details correct and still sometimes while coding you realize there are conflicting flows.
Taking the tests driven approach to development means having a critical eye on the required business logic flow.
  
#### Challenging
Funny to say, but sometimes even the most boring and routine development tasks entail challenging testing scenarios or setup.
Let's say you need to test the outputs of a very complicated system. you'll have to devise a test scheme that doesn't involve 
writing the whole component again inside the test. 

Other interesting and challenging scenarios include: figuring ways to patch/ inject some complicated dependency,
handling testing situations where a dependency doesn't include a testing api (database for example) and more.

# ~  
So that's it. I hope you'll consider writing tests for your future components. In future posts I'll discuss
the gist of the actual tests methodology (unit, integration, etc..) and how to setup and perform tests 
on Python code with the [Pytest Framework](https://pytest.org).    