![Imgur](https://i.imgur.com/gT8GfNx.png)

# Lesson 0: Solidity Basics (Part 1)

## Objectives



## Contents

[0.1 Remix Ethereum IDE](#remix) 

## 0.1 Remix Ethereum IDE <a name='remix'></a>

The Remix Ethereum IDE can be accessed [here](https://remix.ethereum.org/). There are also downloadable version of the IDE for all operating systems available [here](https://github.com/ethereum/remix-desktop/releases).

---

## 0.2 Comments

Many times this is the first thing you will see in a contract. Comments are used to annotate code and are note interpreted by the compiler. They are meant to be read by the coder and any other people reading the code. **There have actually been scam tokens that mentioned that the token is a scam in the comments. So this might be a place to look.**

There are four types of comments in Solidity:

- Single-line comments: These comments can only span a single line.
- Multi-line comments: These comments can span several lines
- Single-line and Multi-line Ethereum Natural Specification (NatSpec): These are used for documentation purposes and are beyond the scope of an introductory lesson. You can read more about these [here](https://docs.soliditylang.org/en/develop/natspec-format.html).

---

### 0.2.1 Single-line Comments

Single-line comments start with `//`.

```
// This is a single-line comment
```

Single line comments usually go above the code that is being annotated, or immediately after the line of code being annotated.

```
// This is the pragma line
pragma solidity 0.8.0; // This version is newer that 0.7.0
```

Single-line comments are useful if your are testing code and you want to **comment out** a single line of code so it does not compile.

---

### 0.2.2 Multi-line Comments

Multi-line comments start with `/*` and end with `*/` .

```
/* This
is
a
multi-line
comment */
```

Multi-line comments are used for larger annotations that are not suitable for single-line comments. Multi-line comments can also be used to comment out blocks of code.

---

### 0.2.3 Ethereum Natural Specification (NatSpec)

These comments are too elaborate for an overview. You can read more about them [here](https://docs.soliditylang.org/en/develop/natspec-format.html).  Documentation can be generated automatically with `///` for single-line documentation or `//* ...*  /. Here is an example below:

```
/**
 * @dev Returns the amount of tokens owned by `account`.
 */
function balanceOf(address account) external view returns (uint256);
```

```
/// @dev Returns the amount of tokens owned by `account`.
function balanceOf(address account) external view returns (uint256);
```



---

## 0.3 The Pragma Directive

The pragma directive is often the first line of executable code in a Solidity file. Many times there may be a comment above this line that specifies the licensing of the file. The pragma is a directive that specifies the version of the compiler that must be used to compile the file. With newer compiler versions certain code may be deprecated and new features are added to the language. The syntax for the pragma directive is presented below:

```
pragma solidity <<version x.x.x>>;
```

It is also possible to write a pragma directive to target a specific compiler or a range of compilers as follows:

```
// Use a compiler 0.6.0
pragma solidity >=0.6.0;        

// Use a compiler greater than 0.6.0
pragma solidity 0.6.0;

// Use a compiler greater than or equal to 0.6.0 but less than 0.8.0
pragma solidity >=0.6.0 <0.8.0; 
```

It is also possible to have the pragma directive choose the latest version within a build using a carat `^` before the version.

```
// Use the latest version of compiler 0.8.0
pragma solidity ^0.8.0; 
```

The pragma line above specifies that the latest release of `0.8.0` should be used to compile the contract. As of the time of writing this this would compile using `0.8.6`, but it will compile with `0.8.7` and any subsequent versions as they are released. There is a risk that the code may be deprecated if a `^` is used if part of the code is deprecated in the latest release.

It is possible to have multiple pragma lines in a `.sol` file. The code that follows the pragma line will compile using the specified compiler until the next pragma line.

