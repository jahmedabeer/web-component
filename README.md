 
    * Web components consists of three main technologies  
    - Custom elements ( two types )
        - Customized built-in elements
        - Autonomous custom elements
    - Shadow DOM
    - HTML templates

    * Rules on creating custom elements
    - The name of a custom element must contain a dash (-). So <x-tags>, <my-element>, and <my-awesome-app> are all valid names, while <tabs> and <foo_bar> are not. This requirement is so the HTML parser can distinguish custom elements from regular elements.
    - You can't register the same tag more than once. Attempting to do so will throw a DOMException
    - Custom elements cannot be self-closing because HTML only allows a few elements to be self-closing. Always write a closing tag (<app-drawer></app-drawer>)

    * Custom element reactions
        - A custom element can define special lifecycle hooks for running code during interesting times of its existence. These are called custom element reactions.
    
    - constructor
        - constructor() is called when the element is created
        - In the constructor() call, you can create the Shadow DOM, but you can't add Nodes inside the normal DOM, and you can't add or set an attribute either.
        - Requirements for custom element constructors and reactions
            - A parameter-less call to super() must be the first statement in the constructor body, to establish the correct prototype chain and this value before any further code is run
            - A return statement must not appear anywhere inside the constructor body, unless it is a simple early-return (return or return this).
            - The constructor must not use the document.write() or document.open() methods.
            - In general, the constructor should be used to set up initial state and default values, and to set up event listeners and possibly a shadow root.
    
    - connectedCallback
        - Called every time the element is inserted into the DOM. Useful for running setup code, such as fetching resources or rendering.
    
    - disconnectedCallback
    
    - attributeChangedCallback(attrName, oldVal, newVal)
    
    - adoptedCallback


    
    * The upgrade occurs when an unknown tag declared in the HTML code is defined afterwards (by the customElements.define() method). The "unknown" element becomes a "custom" element. The constructor() and connectedCallback() methods are then called.

    * Extending HTMLElement ensures the custom element inherits the entire DOM API and means any properties/methods that you add to the class become part of the element's DOM interface