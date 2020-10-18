# How to Design Programs, 2nd Edition
This book is freely available online [here].(https://htdp.org/)

## HtDF Recipe

The HtDF recipe consists of the following steps:

1. Signature, purpose and stub.
2. Define examples, wrap each in check-expect.
3. Template and inventory.
4. Code the function body.
5. Test and debug until correct.

## HtDD Recipe

The how to design data consists of the following steps.
1. A possible structure definition (not until compound data)
2. A type comment that defines a new type name and describes how to form data of that type.
3. An interpretation that describes the correspondence between information and data.
4. One or more examples of the data.
5. A template for a 1 argument function operating on data of this type.

## HtDW Recipe

The how to design worlds recipe consists fo the following steps:

1. Domain analysis (use a piece of paper!)
    1. Sketch program scenarios
    2. Identify constant information
    3. Identify changing information
    4. Identify big-bang options
2. Build the actual program
    1. Constants (based on 1.2 above)
    2. Data definitions using HtDD (based on 1.3 above)
    3. Functions using HtDF
        1. main first (based on 1.3, 1.4 and 2.2 above)
        2. wish list entries for big-bang handlers
3. Work through wish list until done