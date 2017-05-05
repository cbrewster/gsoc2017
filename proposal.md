# Servo Custom Element Proposal
GSoC 2017

Personal Details:
* **Name:** Connor Brewster
* **Github:** cbrewster
* **IRC (mozilla):** cbrewster

## Project Proposal

The goal of this project is to implement custom elements in Servo according to the WHATWG specification1. A custom element is a DOM element that is defined through javascript.

There are two kinds of custom elements:
* Autonomous custom elements
  * Extends HTMLElement
  * Does not build on top of functionality from other HTML elements
* Customized built-in elements
  * Extends the functionality of existing HTML elements

Both allow the user to implement a custom prototype and constructor for the custom element. These elements allow javascript authors to create reusable web components. While the custom element specification is new, many projects such as Polymer are now using this API. As custom elements become more widely used, it would be beneficial for Servo to support this API.

Planned Functionality:
* Custom Element Registry
  * .define(..) Defines custom elements
  * .get(..) Returns the constructor for defined custom elements
  * .whenDefined(..) Returns a promise that will be fulfilled when a custom element with the specified name is defined
* Custom Element Creation
  * The HTML parser and JS document should be able to create custom elements (both autonomous and customized built-in elements).
* Custom Element Reactions
  * Specified callbacks should be called when reactions are triggered (attribute mutation, connected/disconnected, document adoption, and upgrades)
* CEReactions WebIDL extended attribute
  * When an operation/attribute is decorated with this extended attribute, codegen should generate code to watch for any reactions that should be triggered on custom elements after the operation has completed.
* The implementation should be tested by the existing WPT tests located in tests/wpt/web-platform-tests/custom-elements. All tests in that directory should be passing after this project except any tests that use other non-implemented features in servo (outside of the custom element specification).

**WHATWG Specification:** https://html.spec.whatwg.org/multipage/#custom-elements

## Implementation Overview

I have split the project into a few smaller pieces. I will implement custom elements incrementally. I plan on placing the implementation behind a custom element preference flag at least until custom elements are fully implemented and all the relevant tests are passing.

### Custom Element Registry
2 Weeks

The custom element registry is in charge of managing the available custom elements in a window. Each window has its own registry.
The registry does the following things:
* Allows new custom element definitions to be registered
* Retrieve the constructor for any custom element
* Retrieve a promise for a custom element name that will be fulfilled when a custom element of that name has been registered

**Possible Complications:**

Validation of new custom element definitions using jsapi functions.

### Custom Element Creation
2 Weeks

Once the registry is in place, the element creation process can check the registry to see if a custom element definition exists for the given element name. If no custom element is defined, but the name is a valid custom element name, a HTMLElement is created rather than a HTMLUnknownElement.

**Possible Complications:**

Creating the custom element from the constructor in the registry using jsapi functions.

### Custom Element Reactions
2 Weeks

Custom element reactions are a collection of callbacks that are called when certain events happen from running author code. These events include:
* Upgrades
* When the element is connected
* When the element is disconnected
* When the element is adopted into a new document
* When any of the elements attributes are mutated

**Possible Complications:**
Upgrades seem to be the most complex reaction to deal with, so I have moved it to its own section.

### Custom Element Upgrades
2 Weeks

If an element was created with a valid custom element name when no custom element with that name was defined it should create a HTMLElement. If a custom element is later defined with that name, the already existing elements should upgraded.

### CEReactions WebIDL extended attribute
2 Weeks

This is a new WebIDL extended attribute that marks any operation that could trigger any custom element reactions. This requires adding the attribute to the WebIDL parser and checking to see if any reactions should be triggered after the operation is completed.

**Possible Complications:**

I have not worked with the WebIDL parser before, so I will have to spend some time familiarizing myself with the code. This will also require going through each interface in the specification and adding [CEReactions] where needed.

## Schedule of Deliverables
**May 4 - May 27 (3 Weeks):** Study specification in more detail and begin initial implementations.

**May 28 - June 10 (2 Weeks):** Implement the custom element registry

**June 11 - June 24 (2 Weeks):** Make element creation aware of the custom element registry

**June 25 - July 1 (2 Weeks):** Implement custom element reactions

**July 2 - July 29 (2 Weeks):** Implement custom element upgrades

**July 30 - August 5 (2 Weeks):** Implement WebIDL CEReactions extended attribute

**August 6 - August 29 (> 3 Weeks):**
Handle any unforeseen complications or issues and tidy up any loose ends.

## Open Source Development Experience
I have been involved in open source development for almost a year as an active contributor of the Servo project. I mainly work on the constellation and browser history related issues. Outside of Servo I have landed some commits on rustfmt. Open source development has allowed me to work on larger larger projects, learn how a workflow works on large projects such as Rust and Servo, and sharpen my skills as a software developer. I plan to keep giving back and to stay involved in the open source community going forward.

## Work/Internship Experience
I have experience working as a student IT at my previous high school for 2 years and have done various contracting jobs in areas ranging from iOS apps to websites. This last year I was contracted to develop iOS and android apps for an on-campus startup at my university.

## Academic Experience
I am a Computer Engineering major and Computer Science minor undergrad at Oklahoma Christian University. I am finishing my freshman year; however, I am currently a senior in standing. The majority if my programming knowledge is self-taught through working on my own personal projects.

## Why Me
I have been contributing to Servo for almost a year with experience working with the script and constellation components. I believe I am capable of undertaking this task from my prior experience and would love to spend more time working on Servo over the summer.

## Why Mozilla
Mozilla creates an open and welcoming community. I agree with Mozilla’s values in the web space and would like to continue to help the effort to maintain an open web.

Mozilla supports projects like Rust and Servo which I believe will be playing important roles in the future. I would like to continue helping in the effort to push these new technologies forward.
