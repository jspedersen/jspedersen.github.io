---
layout: essay
type: essay
title: "There's Always Someone SMARTer!"
# All dates must be YYYY-MM-DD format!
date: 2024-01-25
published: true
labels:
  - Smart Questions
  - Learning
---

<img class="img-fluid" src="../img/always-smarter.jpg">

*There's always going to be someone smarter than you.*

## Navigating the Landscape of Technical Questions

Learning is a neverending process that all of us collectively are constantly doing. Whether it’s in the classroom, or on a job site, there’s always going to be someone that may be “better,” or know more about certain topics that you do. However, this doesn’t mean we can’t get to the same level as some people! 

We can take various actions towards becoming smarter and understanding more, such as asking ‘smart’ questions. Asking professional and ‘smart’ questions is important, especially in the vast world of computer science, and software engineers due to the sheer amount of technical information out there.

Upon reading and learning about ‘smart’ questions, it kind of conflicted with me. Growing up, I was told that it's always best to ask questions, as there are no ‘dumb’ questions. However, I quickly understood why this is the standard for technical questions. There is so much information already out there, that the questions we may have on particular topics, very much have been answered years prior. For this reason, we have implemented a standard for ‘smart’ questions.


## Defining a Smart Question

A ‘smart’ question is a comprehensive thought-out and specific question, that is carefully formulated and presented to a forum, person, or other medium, (in our case with this essay, we will be looking at StackOverflow) that follows specific professional and respectful guidelines, to ensure that the question is well-written to promote a favorable response. Eric Raymond in his essay, “How To Ask Questions The Smart Way” describes the specificities of smart questions, indicating that a good question is grammatically correct, and holds precise and explicit information about a code, question, or a problem’s symptoms, as well as (if needed for the question) the software/program(s) the person is using.

A smart question, however, should be formulated and asked after we have done extensive research. If we, by chance do not find a plausible answer, that’s when the importance of smart questions comes into play, which is why it’s so important for software engineers, as formulating a precise question may direct you to individuals who know how to help.


## Smart Question by Bill!

Linked below is a question asked by user ‘bill’, taken from StackOverflow which demonstrates the action of asking a smart question. The question, which has been viewed over 947,000 times, asks "[How to pass “Null” (a real surname!) to a SOAP web service in ActionScript 3](https://stackoverflow.com/questions/4456438/how-to-pass-null-a-real-surname-to-a-soap-web-service-in-actionscript-3)". Null, as I am sure lots of us programmers and software engineers know, is a very common and widely used value. The problem, as the title suggests, states that an employee with the surname of Null kills the employee lookup application every time that specific surname is being searched. The author also has attached a runtime error code in the application, indicating that the surname string parameter passed to the function is not being found, thus providing intricate details about the symptoms he is having. To end, he provides the details of the programs he is using additional information about the symptoms of his problem, and valid question tags to direct his question to the right subforum.

```
We have an employee whose surname is Null. Our employee lookup application is killed when that last name is used as the search term (which happens to be quite often now). The error received is:

<soapenv:Fault>
   <faultcode>soapenv:Server.userException</faultcode>
   <faultstring>coldfusion.xml.rpc.CFCInvocationException: [coldfusion.runtime.MissingArgumentException : The SEARCHSTRING parameter to the getFacultyNames function is required but was not passed in.]</faultstring>
The parameter type is string.

I am using:

WSDL (SOAP)
Flex 3.5
ActionScript 3
ColdFusion 8
Note that the error does not occur when calling the webservice as an object from a ColdFusion page.
```

As ‘bill’ met all the requirements for asking a smart question, he got multiple intelligent and extensive answers, with the top-rated one precisely indicating ways of back-tracking the bug, as well as indicating the cause of the problem, and how to solve it, with code examples from their previous encounters with the problem, or similar situations of such!

```
Tracking it down
At first I thought this was a coercion bug where null was getting coerced to "null" and a test of "null" == null was passing. It's not. I was close, but so very, very wrong. Sorry about that!

I've since done lots of fiddling on wonderfl.net and tracing through the code in mx.rpc.xml.*. At line 1795 of XMLEncoder (in the 3.5 source), in setValue, all of the XMLEncoding boils down to

currentChild.appendChild(xmlSpecialCharsFilter(Object(value)));
which is essentially the same as:

currentChild.appendChild("null");
This code, according to my original fiddle, returns an empty XML element. But why?

Cause
According to commenter Justin Mclean on bug report FLEX-33664, the following is the culprit (see last two tests in my fiddle which verify this):

var thisIsNotNull:XML = <root>null</root>;
if(thisIsNotNull == null){
    // always branches here, as (thisIsNotNull == null) strangely returns true
    // despite the fact that thisIsNotNull is a valid instance of type XML
}
When currentChild.appendChild is passed the string "null", it first converts it to a root XML element with text null, and then tests that element against the null literal. This is a weak equality test, so either the XML containing null is coerced to the null type, or the null type is coerced to a root xml element containing the string "null", and the test passes where it arguably should fail. One fix might be to always use strict equality tests when checking XML (or anything, really) for "nullness."

Solution
The only reasonable workaround I can think of, short of fixing this bug in every damn version of ActionScript, is to test fields for "null" and escape them as CDATA values.
CDATA values are the most appropriate way to mutate an entire text value that would otherwise cause encoding/decoding problems. Hex encoding, for instance, is meant for individual characters. CDATA values are preferred when you're escaping the entire text of an element. The biggest reason for this is that it maintains human readability.
```

## The Power of Asking for Help

While learning is an ongoing process we are all continuously doing, we can help ourselves by first researching thoroughly, and if needed, crafting strategic and enticing questions that promote the dedication to learning and collaboration in the world of software engineering. Learning is a million times easier when we know the skill of asking for help!



### Resources:
<a href="https://stackoverflow.com/questions/4456438/how-to-pass-null-a-real-surname-to-a-soap-web-service-in-actionscript-3">Smart Question - 'Null' Surname Parameter</a>


**- ChatGPT used for paragraph headers**
