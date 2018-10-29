# A letter template in LaTeX (using scrlttr2) that can be used with pandoc

## Setup
1. Install [pandoc](https://pandoc.org/) for your platform.
2. Place the `letter.latex` file inside the `~/.pandoc/templates` directory
   (create the directory if it does not exist yet).

## Usage
You can tell pandoc to use the `letter` template using the `--template
letter` argument. The most basic pandoc command hence looks like this:

```
pandoc example.md -o example.pdf --template letter
```

![Example output](https://github.com/mariuskiessling/letter-template/blob/master/example/example.png)

### Parameters
The template provides some variables you can set inside the YAML meta data
block. The block is surrounded by `---` and can be located anywhere inside your
markdown document. In most cases the block is located at the beginning of your
document.

**Please note**: All parameters, **except** the opening parameter, are
optional. However to make good use of this template you should define most of
the parameters.

The following code block shows a YAML meta data block that contains **all**
parameters. 

```
from:
  - name: Alice Diffie
  - address: Example Road 1, 12345 Town
to:
  - company: Crypto Company
  - name: Bob Hellman
  - street: Key Avenue 2
  - town: 12345 Town
place: Town
date: 10.10.2018
opening: Dear Bob,
closing: Best regards
subject: Let's talk about keys
signature: ./signature.pdf
```

---

- **from**: A list of information identifying the sender.
  - **name**: The sender's name.
  - **address**: The sender's address.
- **to**: A list of information identifying the receiver. 
  - **company**: If the receiver is a company, you can specify the company's
    name.
  - **name**: The receiver's name.
  - **street**: The receiver's street (including the house number).
  - **town**: The receiver's town (including the postal ode).
- **place**: The place where the letter was written. If no place is supplied,
    no place is rendered next to the letter's date.
- **date**: The date when the letter was written. If no date is supplied,
  today's date will be used instead. **Please note**: If no date is provided
  each time the letter is recompiled, the current date is used. If you thus plan
  to compile the letter on multiple days you should always specify a date.
- **opening**: The letter's opening (e.g. Dear Bob,).
- **closing**: The letter's closing (e.g. Best regards).
- **subject**: The letter's subject rendered in a bold font (14pt) above the
  opening and below the letter's date.
- **signature**: The sender's signature rendered below the opening and above
  the sender's name. The signature's image is shifted a few millimeters above
  the sender's name to create the "feeling" of a handwritten signature. The
  signature's height is limited to 1.8cm (the width is not limited). If the
  signature parameter is not provided only the sender's name is rendered below
  the closing. **Please note**: The path to the signature must not include
  non-alphanumerical characters (except space, slash and dot).
