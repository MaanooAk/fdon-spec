# fdon specification

Freedom Object Notation is a free form data format, was created for the Freedom programming language.

## Definitions

- **whitespace**: `=`, `,` and whitespace ( ` `, `\t`, `\r`, `\n` )

- **special**: `{`, `}`, `[`, `]`, `(`, `)` `:`, `'`,

- **data**: everything else

## Structure

Fdon structure consists of the base **fdon-base** and the extensions **fdon-types** and **fdon-functions**.

### **fdon-base** :

- A **value** is a **literal**, an **object** or an **array**.

- A **literal** is sequence of data characters or any characters enclosed in `'`.

- An **array** is sequence of **value**s enclosed in `[` and `]`.

- An **object** is a collection of name value **pair**s enclosed in `{` and `}`.

- A name value **pair** is a **literal** followed by a **value**.

Example:

``` js
{ name Akritas tags [ human developer ] }
```

Note: The characters `=` and `,` are defined as whitespace, so the following is equivalent:

``` js
{
    name = 'Akritas'
    tags = [ 'human', 'developer' ]
}
```

### **fdon-types** :

- A **type** may be specified to an **object** by prepending the type name followed by `:`.

- A **id** may be specified to an **object** with **type** by prepending the id name followed by `:`.

- A **comment** is sequence of characters which starts with `#` and ends with a new line.

Example:

``` js
DefaultConfig : Config : {
    music 1.0
    sound 1.0
}
```

Note: An object with id also defines a new type which inherits from the its type:

``` js
UserConfig : DefaultConfig : {
    sound 0
}
```

### **fdon-functions** :

- A **function call** is a function name followed by its arguments enclosed in `(` and `)`.

- A **function declaration** is the literal `function` followed by a **function call** followed by a **object** using the argument names.

Example:

``` js
function rgb ( v1 v2 v3 ) = Color : { r v1, g v2, b v3 }

white : rgb ( 255 255 255 )
black : rgb (   0   0   0 )
```

Note: Function declarations do not have to be defined in the fdon document, they can be defined in the parser.

```js
Arc :{  size 10  angle radians(1.5)  }
```

## More

### Examples

- [Simple Examples](Examples/SimpleExamples.md)
- [Complex Examples](Examples/ComplexExamples.md)

### Implementations

- [Fdon Java Implementation](https://github.com/MaanooAk/fdon-java)
- [Fdon Go Implementation](https://github.com/MaanooAk/fdon-go)

