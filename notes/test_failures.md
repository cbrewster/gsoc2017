# Remaining Test Failures

## Incorrect Implementation

### `custom-element-registry/define.html`
 - [ ] If constructor is arrow function, should throw a TypeError
    * **Reason:** Constructor is not unwraped before calling `IsConstrutor`.
    * **Pull Request:** [Unwrap function before calling IsConstructor](https://github.com/servo/servo/pull/17250)

### `reactions/Element.html`
 - [X] setAttributeNode on Element must enqueue an attributeChanged reaction when replacing an existing attribute
    * **Reason:** Attribute changed callback was not enqueued when replacing the attribute.
    * **Pull Request:** [Enqueue attribute changed callback when replacing attr](https://github.com/servo/servo/pull/18074)

 - [X] setAttributeNodeNS on Element must enqueue an attributeChanged reaction when replacing an existing attribute
    * **Reason:** Attribute changed callback was not enqueued when replacing the attribute.
    * **Pull Request:** [Enqueue attribute changed callback when replacing attr](https://github.com/servo/servo/pull/18074)

### `reactions/NamedNodeMap.html`
 - [X] setNamedItem on NamedNodeMap must enqueue an attributeChanged reaction when replacing an existing attribute
    * **Reason:** Attribute changed callback was not enqueued when replacing the attribute.
    * **Pull Request:** [Enqueue attribute changed callback when replacing attr](https://github.com/servo/servo/pull/18074)

 - [X] setNamedItemNS on NamedNodeMap must enqueue an attributeChanged reaction when replacing an existing attribute
    * **Reason:** Attribute changed callback was not enqueued when replacing the attribute.
    * **Pull Request:** [Enqueue attribute changed callback when replacing attr](https://github.com/servo/servo/pull/18074)

### `reactions/DOMTokenList.html`
 - [ ] replace on DOMTokenList must not enqueue an attributeChanged reaction when the token to replace does not exist in the attribute
    * **Reason:** The update steps were ran even if the token did not exist in the attribute; this caused a reaction to be triggered
    * **Pull Request:** [Only run DOMTokenList update steps if token was found](https://github.com/servo/servo/pull/18092)

## Missing Servo Features

### `reactions/CSSStyleDeclaration.html`
 - [ ] webkit prefixed related tests
    * **Reason:** `webkit-filter` is missing from `CSSStyleDeclaration.webidl`.

### `reactions/Document.html`
 - [ ] execCommand on Document must enqueue a disconnected reaction when deleting a custom element from a contenteditable element
    * **Reason:** `execCommand` is not implemented.

### `reactions/Element.html`
 - [ ] slot on Element must enqueue an attributeChanged reaction when adding slot content attribute
    * **Reason:** Servo does not implement Shadow DOM.

 - [ ] slot on Element must enqueue an attributeChanged reaction when replacing an existing attribute
    * **Reason:** Servo does not implement Shadow DOM.

### `reactions/ElementContentEditable.html`
 - [ ] contentEditable on ElementContentEditable must enqueue an attributeChanged reaction when adding contenteditable content attribute
    * **Reason:** `contenteditable` is not implemented in Servo.

 - [ ] contentEditable on ElementContentEditable must enqueue an attributeChanged reaction when replacing an existing attribute
    * **Reason:** `contenteditable` is not implemented in Servo.

### `reactions/HTMLOutputElement.html`
 - [ ] value on HTMLOutputElement must enqueue disconnectedCallback when removing a custom element
    * **Reason:** `value` is not implemented for `HTMLOutputElement`.

 - [ ] defaultValue on HTMLOutputElement must enqueue disconnectedCallback when removing a custom element
    * **Reason:** `defaultValue` is not implemented for `HTMLOutputElement`.

### `reactions/Selection.html`
 - [ ] deleteFromDocument on Selection must enqueue a disconnected reaction
    * **Reason:** Servo does not implement the `Selection` API.

### `reactions/ShadowRoot.html`
 - [ ] innerHTML on ShadowRoot must upgrade a custom element
    * **Reason:** Servo does not implement Shadow DOM.

 - [ ] innerHTML on ShadowRoot must enqueue connectedCallback on newly upgraded custom elements when the shadow root is connected
    * **Reason:** Servo does not implement Shadow DOM.

 - [ ] innerHTML on ShadowRoot must enqueue disconnectedCallback when removing a custom element
    * **Reason:** Servo does not implement Shadow DOM.

### `adopted-callback.html`
 - [ ] Shadow host/tree related tests
    * **Reason:** Servo does not implement Shadow DOM.

### `conntected-callbacks.html`
 - [ ] Shadow host/tree related tests
    * **Reason:** Servo does not implement Shadow DOM.

### `disconntected-callbacks.html`
 - [ ] Shadow host/tree related tests
    * **Reason:** Servo does not implement Shadow DOM.

## Unknown (Need to Investigate)

### `parser/parser-uses-registry-of-owner-document.html`
 - [ ] HTML parser must not instantiate custom elements inside template elements

 - [ ] HTML parser must use the registry of window.document in a document created by `document.implementation.createHTMLDocument()`

### `reactions/Element.html`
 - [ ] insertAdjacentHTML on Element must enqueue a connected reaction for a newly constructed custom element

 - [ ] insertAdjacentHTML on Element must enqueue a attributeChanged reaction for a newly constructed custom element

### `reactions/HTMLElement.html`
 - [ ] translate on HTMLElement must enqueue an attributeChanged reaction when adding translate content attribute

 - [ ] translate on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] dir on HTMLElement must enqueue an attributeChanged reaction when adding dir content attribute

 - [ ] dir on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] tabIndex on HTMLElement must enqueue an attributeChanged reaction when adding tabindex content attribute

 - [ ] tabIndex on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] accessKey on HTMLElement must enqueue an attributeChanged reaction when adding accesskey content attribute

 - [ ] accessKey on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] draggable on HTMLElement must enqueue an attributeChanged reaction when adding draggable content attribute

 - [ ] draggable on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] dropzone on HTMLElement must enqueue an attributeChanged reaction when adding dropzone content attribute

 - [ ] dropzone on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] contextMenu on HTMLElement must enqueue an attributeChanged reaction when adding contextmenu content attribute

 - [ ] contextMenu on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] spellcheck on HTMLElement must enqueue an attributeChanged reaction when adding spellcheck content attribute

 - [ ] spellcheck on HTMLElement must enqueue an attributeChanged reaction when replacing an existing attribute

 - [ ] innerText on HTMLElement must enqueue a disconnected reaction

### `reactions/HTMLSelectElement.html`
 - [ ] The indexed setter on HTMLSelectElement must enqueue connectedCallback when inserting a custom element

 - [ ] The indexed setter on HTMLSelectElement must enqueue disconnectedCallback when removing a custom element

 - [ ] add on HTMLSelectElement must enqueue connectedCallback when inserting a custom element

### `reactions/HTMLTableElement.html`
 - [ ] caption on HTMLTableElement must enqueue connectedCallback when inserting a custom element

 - [ ] tHead on HTMLTableElement must enqueue connectedCallback when inserting a custom element

 - [ ] tFoot on HTMLTableElement must enqueue connectedCallback when inserting a custom element

### `reactions/Range.html`
 - [ ] createContextualFragment on Range must construct a custom element

### `attribute-changed-callback.html`
 - [ ] Custom Elements: attributeChangedCallback

### `CustomElementRegistry.html`
 - [ ] customElements.define must upgrade elements in the shadow-including tree order
