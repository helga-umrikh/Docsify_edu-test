# String

The `String` object is used to represent and manipulate a sequence of characters.

## Description

Strings are useful for holding data that can be represented in text form. Some of the most-used operations on strings are to check their `length`, to build and concatenate them using the `+` and `+=` string operators, checking for the existence or location of substrings with the `indexOf()` method, or extracting substrings with the `substring()` method.

## Creating strings

Strings can be created as primitives, from string literals, or as objects, using the String() constructor:

```javascript
const string1 = "A string primitive";
const string2 = 'Also a string primitive';
const string3 = `Yet another string primitive`;

```

<!-- tabs:start -->

#### **Character access**

There are two ways to access an individual character in a string. The first is the charAt() method:

```javascript
"cat".charAt(1); // gives value "a"

```

The other way is to treat the string as an array-like object, where individual characters correspond to a numerical index:

```javascript
"cat"[1]; // gives value "a"
```

#### **Comparing string**

Use the less-than and greater-than operators to compare strings:

```javascript
const a = "a";
const b = "b";
if (a < b) {
  // true
  console.log(`${a} is less than ${b}`);
} else if (a > b) {
  console.log(`${a} is greater than ${b}`);
} else {
  console.log(`${a} and ${b} are equal.`);
}

```

Note that all comparison operators, including === and ==, compare strings case-sensitively. A common way to compare strings case-insensitively is to convert both to the same case (upper or lower) before comparing them.

```javascript
function areEqualCaseInsensitive(str1, str2) {
  return str1.toUpperCase() === str2.toUpperCase();
}

```

The choice of whether to transform by toUpperCase() or toLowerCase() is mostly arbitrary, and neither one is fully robust when extending beyond the Latin alphabet. For example, the German lowercase letter ß and ss are both transformed to SS by toUpperCase(), while the Turkish letter ı would be falsely reported as unequal to I by toLowerCase() unless specifically using toLocaleLowerCase("tr").

```javascript
const areEqualInUpperCase = (str1, str2) =>
  str1.toUpperCase() === str2.toUpperCase();
const areEqualInLowerCase = (str1, str2) =>
  str1.toLowerCase() === str2.toLowerCase();

areEqualInUpperCase("ß", "ss"); // true; should be false
areEqualInLowerCase("ı", "I"); // false; should be true

```

#### **String coercion**

Many built-in operations that expect strings first coerce their arguments to strings (which is largely why String objects behave similarly to string primitives). The operation can be summarized as follows:

- Strings are returned as-is.

- undefined turns into "undefined".

- null turns into "null".

- true turns into "true"; false turns into "false".

- Numbers are converted with the same algorithm as toString(10).

- BigInts are converted with the same algorithm as toString(10).

- Symbols throw a TypeError.

- Objects are first converted to a primitive by calling its [@@toPrimitive]() (with "string" as hint), toString(), and valueOf() methods, in that order. The resulting primitive is then converted to a string.

<!-- tabs:end -->