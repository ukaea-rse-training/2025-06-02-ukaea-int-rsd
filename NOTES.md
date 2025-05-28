# Int RSE Course

## Section 3

### Software Requirements

- Everyone seemed to follow quite well, but it wasn't terribly explicit that we were skipping the
  Software Requirements section (glazed over somewhat)

#### Software Architecture and Design

- There are quite a few slides up to the one on refactoring without a pause... but that is true of
  the whole course!
  - in general, we should add some more figures and things to slides
- Standing up is a good idea!
- Timings of the exercises was spot on, and I really liked the discussions
- We are running into a ton of problems with the package not being installed (e.g. pytest not
  finding things)
  - This made it difficult to actually run the `compute_data.py` and its functions to get the output
    of what that should be
  - We should do some sort of install earlier rather than later

#### Refactoring functions to do just one thing

- There was a bit of hiccup getting the results out of the `compute_data.py::analyse_data()`
  function to write the regression test, so perhaps there needs to be a bit more hand holding (this
  is even outside of the trouble with the package not being installed)
- well done to suggest optional exercises (e.g. find some functions in your own code and determine
  if they are pure or impure). We should definitely include more of these in the material.

#### Classes

- When talking about abstrations, would it be good to also mention that an abstration will crucially
  define an interface
- Exercise: Decouple the file loading from the computation
  - Got a bit jumbled here. The explanation of what needs to be done was unclear, and crucially the
    lesson material itself is a bit unclear
    > Currently the function is hard coded to load all the files in a directory Decouple this into a
    > separate function that returns all the files to load
  - We don't want this new function to return the files, but rather to return the entire data
  - I wonder if this could be included in the functional programming section? because this is
    basically another functional programming technique and we are basically just pulling out a
    method
  - It could also be a good opportunity to use VS Codes refactoring tool "extract function"
- When explaining classes, probably the word "instance" should have been introduced
  - the analogy of cookies and cookiecutters is good, but then that should have been more directly
    connected to class and instance
- Could classes be introduced without the usual resort to Shapes being implemented
  - It might be a bit tough because then we would eliminate the opportunity to do the exercises

#### Project Architecture

- Got a little astray explaining MVC and the main point of it: modularity!!!
  - needs to be a bit more connected to the things we have just done... but perhaps we will get to that
- For the exercise on drawing an architecture diagram, we used the course
  project because no one brought their own ideas. This seemed to work out
  pretty well, so it would be suitable to include this as the fallback
  suggestion in the text.


## Section 4

### Packaging

- We were unsuccessful getting poetry installed on freia
  - need to look at how we would get this to work
  - freia/heimdall support in general very fraught and we need a better
    strategy

## General

- for colour blind (particularly red-green) the light green and light orangish stickies did not
  particularly distinguish well. Probably green and blue? or blue and red? or even something with
