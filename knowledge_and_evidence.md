<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a _Competent_ grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/CREATE_A_SCREENSHOT_OF_YOUR_local_setup.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name   | value           |
   | ----------------------- | ------ | --------------- |
   | built-in primitive type | dimmed | True            |
   | built-in composite type | WHITE  | (255, 255, 255) |
   | user-defined type       | show   | self.pixels     |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                  | Type                    |
   | ----------------------- | ----------------------- |
   | self.pixels             | built-in composite type |
   | A member of self.pixels | built-in primitive type |
   | self                    | user-defined type       |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File      | First line | Line range |
   | ------------ | --------- | ---------- | ---------- |
   | sequence     | smiley.py | 17         | 9          |
   | selection    | sad.py    | 26         | 2          |
   | iteration    | happy.py  | 30         | 2          |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type  | Used? | Example                                 |
   | ----- | ----- | --------------------------------------- |
   | int   | yes   | eyes = [10, 13, 18, 21] (a list of int) |
   | float | yes   | delay=0.25                              |
   | str   | no    | "string"                                |
   | bool  | yes   | wide_open=True                          |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> A class variable stays within the class and therefore cannot be changed without the class changing.
> An instance variable is set outside of the class and may vary depending what is required beforehand

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:

   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > The constructor sets variables and any other initialisation requirements for the class
   > In Happy, it is used to get the correct characteristics for the face, eyes and mouth

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > It calls the super().**init**() which is the overall "face"
   > It calls draw_mouth() which creates the "smile"
   > It calls draw_eyes() for the "eyes"

### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:

> PEP8. Yes as it helps keep it standard and as it's shared between developers, this helps everyone understand the code better.

2. List three aspects of this convention you see applied in the code.

> imports at the top of the files
> classes are CamelCase
> functions and variables are using lowercase_with_underscores

3. Give two examples of organizational documentation in the code.

> """
> Renders a mouth by blanking the pixels that form that object.
> """

> """

       Draws the eyes (open or closed) on the standard smiley.
        :param wide_open (bool): eyes open or closed.
        """

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.

Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s)  |
| ---------- | ------------- | ----------------- |
| Smiley     | Super         | none              |
| Blinkable  | Super         | none              |
| Sad        | Sub           | Smiley            |
| Happy      | Sub           | Smiley, Blinkable |

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction is a way of hiding data or methods from the user which may not be needed by them. They may still be used by the class itself. For example, happy and sad both have "draw eyes" and "draw mouth" methods, but the end-user only knows that it will display the smiley. They don't know how it all came together.

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> The process is called inheritence. In this project it uses inheritence to get the pixels required to make the smiley.

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > Happy has a "blink" method, while sad does not
   > pixels for eyes and mouth are also different.
2. What are the key similarities?
   > They both have draw_eyes and draw_mouth methods
3. What difference stands out the most to you and why?
   > Smiley has the blink method. It gives the class an extra action
4. How does this difference affect the functionality of these classes
   > Happy has more than just a plain face. It does more.

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > Happy, Sad and Smiley all use the functionality. Blickable does not.
2. Which of these classes directly interact with the SenseHat functionalities?
   > the "Smiley" class directly utilises SenseHat in its **init**
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > SenSeHat was initialised under the Smiley class init. the double ** makes that method a "private" function (only useable within that class). The other classes access it in their own private **init\*\*, however utilising the super() (or parent class) init.
   > By doing it this way it is keeping SenSeHat the same and only changing certain methods, keeping the rest of the smiley in tact and still usable in the same way by other classes.

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> No, which is why the method is only in the Happy class. THe happy class also imports the Blinkable class. Sad would also require this to blink.

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> No, the blink() method allows for a "delay" parameter, so it means any smiley could blink for longer or shorter periods rather than a fixed amount of time.

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> Polymorphism is inheriting properties or methods from parent classes giving more "default" values for alike items.

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> As sad does not have a blink method and does not inherit the blinkable class, it will not blink.
> While happy inherits the Blinkable class, Happy has it's own blink() method, so it will override the Blinkable class's blink() method.

1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25):
       pass  # Replace 'pass' with your implementation
   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![Sad Smiley Blinking](screenshots/sad_blinking.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > None

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > It is a subclass of the ABC class

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > An abstract class

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > Abstraction, you can see that it blinks, but you don't know how it blinks

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > If the Sad class does not inherit Blinkable, it could use the same blink() method from Happy and it will still work the same way. Blinkable would only be used if there was no blink() method.

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > The concept is called Duck Typing. In Python you don't need to know what the type is to call a method, you just need to know it exists.

  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > The colours are all defined in the Smiley class.
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > as the variables are in UPPERCASE, they are constants, therefore they would not be expected to change.
     3. Add the color blue to the appropriate class using the appropriate format and values.

     ```python
     BLUE = (0, 0, 255)
     ```

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > The colours are used in both Happy and Sad for the eyes, blink and mouth.
        > The colours are used in the Smiley class to define the face

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > in the Smiley **init** make the Y constant = self.GREEN

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

```python
def complexion(self):
       return self.YELLOW
```

2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

```python
 for pixel in eyes:
            if wide_open:
                eyes = self.BLANK
            else:
                eyes = self.complexion()
            self.pixels[pixel] = eyes
```

3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

   > I believe it is Encapsulation

4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

### Flexible Colors – Step 2

Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

![Bulk Rename](screenshots/bulk_rename.png)

5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

### Flexible Colors – Step 3

With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

   ```python
   super().__init__(complexion=self.BLUE)
   ```

2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

---
