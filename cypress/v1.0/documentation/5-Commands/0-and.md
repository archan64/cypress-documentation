excerpt: Enables chaining multiple assertions together
slug: and

#### **New to Cypress?** [Read about assertions first.](assertions) 
[block:api-header]
{
  "type": "basic",
  "title": "New to Cypress? [Read about assertions first.](assertions)"
}
[/block]
### **New to Cypress?** [Writing Assertions](doc:writing-assertions) 
[block:code]
{
  "codes": [
    {
      "code": "cy\n  // subject is now <a>\n  .get(\"a\")\n\n  // assert <a> contains text: \"Edit User\"\n  // subject is still the <a>\n  .should(\"contain\", \"Edit User\")\n\n  // assert subject has 'href' attribute\n  // subject now changes to return value from the 'href' attribute\n  .and(\"have.attr\", \"href\")\n\n  // assert that the string returned from 'href'\n  // matches the RegExp /users/\n  // the subject is still the same string\n  .and(\"match\", /users/)\n\n  // assert that the string does not\n  // have a '#' character within it\n  .and(\"not.include\", \"#\")",
      "language": "javascript",
      "name": null
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic"
}
[/block]
***

`cy.and` makes assertions about the current subject.

When chaining multiple assertions together, `cy.and` reads very well.

`cy.and` is identical to [`cy.should`](should).

***

## Chaining Assertions

```js
cy.get("button").should("have.class", "active").and("not.be.disabled")
```

***

## Asserting On Subject Changes

```html
<!-- App Code -->
<ul>
  <li>
    <a href="users/123/edit">Edit User</a>
  </li>
</ul>
```

```js
cy
  // subject is now <a>
  .get("a")

  // assert <a> contains text: "Edit User"
  // subject is still the <a>
  .should("contain", "Edit User")

  // assert subject has 'href' attribute
  // subject now changes to return value from the 'href' attribute
  .and("have.attr", "href")

  // assert that the string returned from 'href'
  // matches the RegExp /users/
  // the subject is still the same string
  .and("match", /users/)

  // assert that the string does not
  // have a '#' character within it
  .and("not.include", "#")
```

***

## Notes

If you've worked in `Chai` before, you will recognize that `cy.and` matches the same fluent assertion syntax.

Take this *explicit* assertion for example:

```js
expect({foo: "bar"}).to.have.property("foo").and.eq("bar")
```

`cy.and` reproduces this same assertion behavior.

***

## Command Log

```js
//
  .find("input[type='checkbox']")
    .should("be.checked")
    .and("not.be.disabled")
```

The commands above will display in the command log as:

<img width="530" alt="screen shot 2015-11-29 at 12 16 46 pm" src="https://cloud.githubusercontent.com/assets/1271364/11458700/36d1e646-9693-11e5-8771-158230530fdc.png">

When clicking on `assert` within the command log, the console outputs the following:

<img width="636" alt="screen shot 2015-11-29 at 12 17 03 pm" src="https://cloud.githubusercontent.com/assets/1271364/11458702/3b6873be-9693-11e5-88f7-a928ebdac80c.png">

***

## Related
1. [should](should)
2. [Assertions](assertions)