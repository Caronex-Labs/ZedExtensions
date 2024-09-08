# ZedExtensions
Our collection of Zed extensions, workflows and prompts.

> NOTE: These prompts are built to be used alongside our workflow. It's built to compliment it. We will cover our workflow first so you know if this is for you or not. Either way, feel free to pick up only the parts you like.

## Table Of Contents
1. Our Workflow






## Our Workflow
### Overview

### Index
* The first step is the `Index` stage. 
* This is in order to avoid heavy queries to find relevant files later on.
* It aims to generate a tree structure to understand the logic flow and purpose of each class and function. It's like a context map of the repository.
* Future prompts use this to know which files are relevant. 

### PRD
* The next step is the `PRD` stage. 
* The `/PRD` prompt covers that. You provide a product description of the change or feature you wish to implement. 
* You must pass whatever context that is relevant to the change, or just pass everything using `/full-context`. (Expensive.).

### TRD
* The `TRD` stage comes next. 
* You must pass the PRD as the input.
* The `/TRD` prompt covers that. You must provide the PRD as the input. 
* The prompt will then ask you a ton of questions. (Cost of progress)
* These will help the TRD bridge the gap between the PRD and the code itself.

### Diff
* The `Diff` stage is where actual code changes are proposed for the first time.
* The diff is generated and presented for each relevant file. We are still working on automatically providing a diff in the code.
* Tests are always created first for the whole feature.
* You must go through these tests very carefully. They represent the behaviour of the system you are about to build.
* Once you are done editing or approving the tests, you must call the `/execute` command. This will generate code and present it to you.
* You must copy over all the changes. (Working on an automatic process)
* You run the tests, every time you run into an error, call the `/terminal`.
* Once it runs as expected, you can run the code and confirm the output.

### Tech Review
* Sometimes you want things done a certain way. This step addresses those times.
* You must use the `/refactor` command to make the changes. You will get a behaviour change review, then a code change review and finally the testing loop.

### Product Review
* Sometimes the code works as expected but we don't get the right visual output. The `Product Review` step addresses that phase. 
* You must call the `/product-review` prompt for this step.
* Explain in product terms the issue you are facing.
* The AI will respond with upto 5 possible issues, these will be detailed code level descriptions.
* You can choose to explore any number of them by responding with a list of the numbers corresponding with the issue. (`1, 2, 3`)
* The code will review the relevant tests first. If it finds an issue it will fix that.
* It will then attempt to write code that may pass the new test. (Copy paste (for now (Hurry Zed!)))
* Run the tests, pass to the assistant using `/terminal`
* Once they pass, review. repeat.

