## Description

- Ideate and decide on a unit testing framework for platform.
	- Simple, we'll just use Django's inbuilt `unittest`.
- Estimate the efforts.
	- Fixtures needed to be created
	- Need to set up proper test distribution
		- We can start with just basic `models`, `views`, `urls`
		- Need to make it up as we go - can't plan the whole thing out.
		- Focus on creating as many tests as we possibly can, no bounds on that! Comprehensiveness is more important than beauty.
		- Testing models, functions and urls is not going to be a big deal - and that's the magic of unit testing!
		- We can take note of the most commonly used models and already create mock entries for them that we can use to test other things.
			- It would be hard to setup, but once in place, I feel it would make writing tests really-really easy.
	- Code formatting tool (black, for e.g.,) must be used to properly format the code according to standards.
- Implement a PoC for the same for Localized Average Pricing Feature.
- Evaluate output.

**Note:** The goal is not perfection - but to get started. We'll make it up as we go.

## Bottlenecks:
- Test database takes an awful lot of time to be created
	- Workaround is to use `manage.py test -keepdb`
	- [[Test database creation is really  slow]]
- Test data for some specialized tests.


**Note**: I don't know much about the actual databases of Jenda - this research is fully theoretical, as of now.

**Note**: This is **NOT** Zulip.