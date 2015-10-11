Experimental HTML Guidelines
============================

Tables
------
> * <mark>Simple tables can have two levels of headers. Each header cell should have `scope="col"` or `scope="row"`.</mark>
> * Complex tables are tables with more than two levels of headers. Each header should be given a unique id and each data cell should have a headers attribute with each related header cell’s id listed.

- [18F on tables][]

Alerts
------
> * Use the ARIA `role="alert"` to inform assistive technologies of a time-sensitive and important message that is not interactive. If the message is interactive, use the `alertdialogue` role instead.

- [18F on alerts][]

Forms
-----
Always use `for` in `<label>` and `id` in `<input>`. When sending data to a webserver, include `name` in your `<input>`.

> * All form control tags should have an associated label.
> * Any additional information—such as required, optional, or example text—should be wrapped within the label tags. For example: <label for="name">Favorite Pie <span>Optional</span></label>. This way screen readers know what additional information is related to each field.

Use [aria-describedby][] for error messages.

> * <mark>Avoid placeholder text for accessibility reasons. Most browsers’ default rendering of placeholder text does not provide a high enough contrast ratio.</mark>
> * Avoid breaking numbers with distinct sections (such as phone numbers, Social Security Numbers, or credit card numbers) into separate input fields. For example, use one input for phone number, not three (one for area code, one for local code, and one for number). Each field needs to be labeled for a screen reader and the labels for fields broken into segments are often not meaningful.

Choose input type based on the size and length of input; in ascending order:

* Radio
* Checkbox
* Dropdown (options)
* Text input with autocomplete (eg `<datalist>`)

> * When most users will (or should) pick a particular option, make it the default: `<option selected="selected">Default</option>`

### Checkboxes ###

>Surround a related set of checkboxes with a `<fieldset>`. The `<legend>` provides context for the grouping. Do not use fieldset and legend for a single check.

Think of `<legend>` as `<label>` for an input group.

> Avoid using negative language in labels as they can be counterintuitive.

- [18F on form controls][]

### Templates ###

> * Display form controls in the same order in HTML as they do on screen. Do not use CSS to rearrange the form controls. Screen readers narrate forms in the order they appear in the HTML.
> * Keep your form blocks in a vertical pattern. It’s an ideal approach for accessibility, due to limited vision that makes it hard to scan from right to left.
>
> * Leave the title and suffix fields as text boxes instead of offering drop downs. There are many possible titles and suffixes; text boxes accommodate them all.

- [18F on form templates][]


[18F on tables]: https://playbook.cio.gov/designstandards/tables/
[18F on alerts]: https://playbook.cio.gov/designstandards/alerts/
[aria-describedby]: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-describedby_attribute
[18F on form controls]: https://playbook.cio.gov/designstandards/form-controls/
[18F on form templates]: https://playbook.cio.gov/designstandards/form-templates/
