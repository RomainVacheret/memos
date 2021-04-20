# Plantuml 
* Langage to create diagrams from plain text
* Starts with `@startuml` 
* Ends with `@enduml`

## Class diagram

### Modifiers
* Abstract: `{abstract}` 
* Static: `{static}`

### Keywords
* Package: `package`
* Class: `class`
* Interface: `interface`
* Enumeration: `enum`
* Annotation: `annotation`
* Abstract: `abstract`
  
### Visibility
* Private: `-`
* Protected: `#`
* Package: `~`
* Public: `+`

### Separators
* `--`
* `..`
* `==`
* `__`
* Text can be inserted into the separators: `-- text --`

### Notes
* Notes can be added
  ```
  note <position> of <object>::<element>
    <text>
  end note
  ```
  * Element can be
    * A string
    * A method
    * A field

### Some HTML tags
* `<b>`
* `<u>`
* `<s>`
* `<del>`
* `<font color="X">`
* `<color:X>`
* `<size:X>`
* `<img src="X">` or `<img:X>`


###  Relations between classes
* Extension
  * Syntax: `A <|-- B ` or `class B extends A {}`
  * Syntax: `A <|.. B ` or `class B implements A {}`
* Composition
  * The child can exist independantly of the parent
  * Syntax: `*--`
* Aggregation
  * The child cannot exist independently of the parent
  * Syntax: `o--`
* For composition and aggregation
  * Association
    * Object A owns object B
    * Syntax: `--`
  * Dependency
    * Object A uses object B
    * Syntax: `..`
