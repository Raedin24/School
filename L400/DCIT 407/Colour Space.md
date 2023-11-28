A *colour space* is a mathematical model describing how colours can be represented.
- It is described in a *specific*, *measurable* and *fixed* range of possible colours and luminance values.
- **OpenCV** can be used to manipulate colour spaces. Written in C/C++, with Python bindings
## RGB Colour Space
- The image is represented as a combination of three colours: *red, blue, green*.
- Each colour is represented by a value ranging from **0 to 255**. 
- Combining the 3 can create all possible colours in the visible spectrum

## HSV Colour Space
- **HSV** stands for *Hue, Saturation*  and *Value*.
- Closer to how humans perceive colour.
- Hue ranges from **0 to 179**
- Saturation and Value range from **0 to 255**.

## CMYK Colour Space
- Stands for *(C)yan, (M)agenta, (Y)ellow*  and *blac(K)*
- Is a subtractive colour model.
- Cyan, Magenta and Yellow are gotten from white light minus *red, green*