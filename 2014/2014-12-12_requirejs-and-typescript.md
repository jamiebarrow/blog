# 2014-12-12 RequireJS and TypeScript

tags: RequireJS, TypeScript, Visual Studio, Visual Studio 2013

Here is an example of a [RequireJS](https://requirejs.org/) module:

```javascript
define([], function() {
    function Calculator() {
    }

    Calculator.prototype.calculate = function (x, y) {
        return x + y;
    };
 
    return Calculator;
});
```

To make sure this is compiling through the TypeScript compiler, the first step is to convert it to use modules from TypeScript. The simplest way is:

```typescript
function Calculator() {
}

Calculator.prototype.calculate = function (x, y) {
  return x + y;
};

export = Calculator;
```

To compile this, you then call the compiler with the right module flag, which is AMD for RequireJS:

```shell
tsc Calculator.ts --module amd
```

This will then generate the equivalent JavaScript. You'll notice it adds some extra code that's probably unneccesary, but hey, I'll take that for compile time safety:

```javascript
define(["require", "exports"], function(require, exports) {
    function Calculator() {
    }

    Calculator.prototype.calculate = function (x, y) {
        return x + y;
    };

    return Calculator;
});
```

If you're working in Visual Studio, you might get an error about it not using the module flag. If you're working with an existing codebase, you might find you'll need to add TypeScript support first - adding a new TypeScript file in VS2013 does this by adding some stuff to the CSPROJ file, namely the XML element `TypeScriptToolsVersion`, and will need to reload the project. Afterwards, there should be a new tab for TypeScript Build options in the project properties dialog where you can choose the module style.
