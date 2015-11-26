Experimental HTML Guidelines
============================

Tables
------
> * <mark>Simple tables can have two levels of headers. Each header cell should have `scope="col"` or `scope="row"`.</mark>
> * Complex tables are tables with more than two levels of headers. Each header should be given a unique id and each data cell should have a headers attribute with each related header cell’s id listed.

- [18F on tables][]

Buttons
-------
`<a href="#" role="button">Submit</a>`

vs

`<button role="button">Submit</button>`

vs

`<input type="submit" value="Submit" role="button" />`

Button and input elements are interchangeable, but anchor tags are a different matter, writes [MDN][]:

> Warning: Be careful when marking up links with the button role. Buttons are expected to be triggered using the Space key, while links are expected to be triggered through the Enter key. In other words, when links are used to behave like buttons, adding role="button" alone is not sufficient. It will also be necessary to add a key event handler that listens for the Space key in order to be consistent with native buttons.

Use input elements by defaults and use buttons for a separate purpose or behaviour.

* ["When To Use The Button Element"][csstricks-buttons]
* ["The Difference Between Anchors, Inputs and Buttons"][davidwalsh-buttons]


[18F on tables]: https://playbook.cio.gov/designstandards/tables/
[mdn]: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_button_role
[csstricks-buttons]: https://css-tricks.com/use-button-element
[davidwalsh-buttons]: http://davidwalsh.name/html5-buttons
