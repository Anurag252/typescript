# typescript

globally install typescript 

`npm install -g typescript`

`tsc --version`
generate js using `tsc hello_typescript.ts`

The use of the backtick ( ` ) to delineate strings gives us the ability to inject values directly into the string, as follows:

`var version = `es6`;
console.log(`hello ${version} TypeScript`);`

The use of template strings is actually valid JavaScript, but there is a significant catch to using them. Template strings have only been introduced into later versions of the JavaScript standard, in particular ES2015, also known as the 6th Edition, or just ES6. This means that you need an ES6-capable JavaScript runtime in order to use template strings. TypeScript, however, will generate JavaScript based on the version of the JavaScript runtime you are targeting.

ypeScript will generate JavaScript based on the target version of JavaScript that you specify. We can therefore write TypeScript code using any of the newest JavaScript standards, and TypeScript will correctly generate the equivalent JavaScript

`tsc --init`
This --init option will automatically generate a tsconfig.json file within the current directory, which is used, amongst other things, to specify the target JavaScript version.

tsc
Here, the TypeScript compiler is reading the tsconfig.json file, and applying the compilation values that it finds there, to any .ts file that it finds in either the current directory, or any sub-directories. This means that in order to compile a TypeScript project that may contain many files in many sub-directories, we just need to type tsc in the root directory of the project.

Watching files for changes
TypeScript also has a handy option that will watch an entire directory tree, and if a file changes, it will automatically recompile the entire project. Let's run the TypeScript compiler in this mode as follows:

`tsc -w`

 let's focus on four common types, namely string, number, boolean, and array
 
 `var myBoolean : boolean = true;
var myNumber : number = 1234;
var myStringArray : string[] = [`first`, `second`, `third`];`

Inferred typing
TypeScript also uses a technique called inferred typing, or type inference, to determine the type of a variable.

Duck typing
TypeScript also uses a method called duck typing for more complex variable types. Duck typing suggests that "if it looks like a duck, and quacks like a duck, then it probably is a duck." In other words, two variables are considered to have the same type if they have the same properties and methods. Let's test this theory out with the following code:

`var nameIdObject = { name: "myName", id: 1, print() { } };
nameIdObject = { id: 2, name: "anotherName", print() { } };`

Note that these errors will occur if the name of a property, the type of a property, or the number of properties are not exactly the same when assigning a value to an object.

sample function declaartion :-

`function printString(a: string) : void {
    console.log(a);
}
var returnedValue : string = printString("this is a string");`


1
Up and Running Quickly
So, what exactly is TypeScript? And how can we use it? Well, it really is as simple as "TypeScript generates JavaScript", to quote Anders Hejlsberg, the designer of the TypeScript language. Wherever we see a use for JavaScript in the modern world, we can generate this JavaScript using TypeScript.

JavaScript is being used everywhere – the more you look, the more JavaScript you find running in the most unlikely of places. Just about every website that you visit is using JavaScript to make the site more responsive, more readable, or more attractive to use. The power and flexibility of JavaScript also means that more and more tools are moving on-line. Where we once needed to download and install a program to write a document, or draw a diagram, we can now do this all from within the confines of our humble web browser.

The popularity and simplicity of JavaScript has inspired a whole host of runtime environments that can now run on a server, through Node.js (or simply Node), in the cloud through serverless technologies, or even on embedded devices with purpose-built microcontroller chips. Apache Cordova is a fully fledged web server that runs as a native mobile phone application, meaning that JavaScript, HTML, and CSS can be used to create mobile applications. Even desktop applications can be built using JavaScript, such as the popular editors Visual Studio Code and Atom. These desktop projects use the Electron framework and, as such, are fully fledged desktop applications that can run on Windows, macOS, or Linux.

Building JavaScript applications, therefore, means that what you build could be run on just about any operating system, use any architectural framework, or be used in any embedded device.

It is in the building of these JavaScript applications where TypeScript comes into its own. JavaScript is an interpreted language, and as such has benefits, but also has its drawbacks. Interpreted languages do not have a compilation step, and therefore cannot check that all code written has no minor mistakes in spelling or syntax before it is actually run. TypeScript is a strongly typed, object-oriented language that uses a compiler to generate JavaScript. The compiler will identify errors within the code base even before it is run in an interpreter.

This chapter is an introduction to the TypeScript language, and will focus on getting up and running in order to generate JavaScript as quickly as possible. We will be comparing some JavaScript code to the equivalent TypeScript code in this chapter, in order to explain why writing JavaScript using TypeScript is so beneficial. Your JavaScript code will become more robust, be less prone to errors, easier to read, easier to maintain, and easier to refactor.

We will cover the following topics in this chapter:

Setting up a simple TypeScript IDE
Generating different versions of JavaScript
Configuring a TypeScript project
Type syntax and basic types
Function signatures
Using third-party libraries
An introduction to declaration files
Let's dive right in and set up a TypeScript development environment.

A simple TypeScript IDE
TypeScript generates JavaScript through what is called a compilation step. This means that once you have written some TypeScript code, you will need to compile, or, more correctly, transpile this code, which will generate JavaScript. In order to do this compilation step, you will need a Node environment, and the TypeScript compiler itself. In this section of the chapter, we will explore the setup of a simple TypeScript IDE.

Node is a JavaScript runtime environment. Similar to how a web browser can interpret and run JavaScript code, Node can do the same thing. It is a command-line driven environment, which means that all you need is a standard command prompt in order to run JavaScript.

Installing Node is as simple as downloading the Node installer package from the Node website (https://nodejs.org) for your operating system of choice, and running it. As it is an open source package, so you can also download the source code, and compile it from scratch on your system if you are so inclined. We will not run through the installation process here, and will simply assume that the Node packages have been correctly installed on your operating system. To verify that Node is installed, open up a command prompt and type:

node --version
If Node has been installed correctly, you should see something similar to the following output on the console:

v15.12.0
Here, we can see that Node has output its version number to the console, which, as of the time of writing, is version v15.12.0.

Using npm
Node includes a command-line program called the Node Package Manager (npm), in order to download, and make available a whole host of runtime libraries, of which TypeScript is one. These packages can either be installed globally, and therefore usable throughout your system, or can be installed locally. Locally installed Node packages will be installed within a sub-directory named node_modules, and globally installed Node packages will be installed in the system-wide node_modules directory. To check that npm has been installed correctly, type the following in the command prompt:

npm --version
The output of this command should be similar to the following:

7.6.3
Here, we can see that the npm version on our system is at version 7.6.3.

To install the TypeScript compiler globally, type the following in your command prompt:

npm install -g typescript
Here, we are installing the typescript Node package globally, using the -g option. Although the Node package is named typescript, it makes a Node executable available named tsc that will invoke the TypeScript compiler. To verify that TypeScript has been installed correctly, type the following into the command prompt:

tsc --version
Here, we are invoking the TypeScript command-line compiler (tsc), and using the --version argument to report the current version of the compiler. The output should be similar to the following:

Version 4.2.3
Here, we can see that the version of TypeScript installed on our system, and used throughout this book, is version 4.2.3.

Hello TypeScript
Let's dive right in and generate some JavaScript from a TypeScript file. In order to do this, we will need a text editor, and none fits the bill better than Microsoft's Visual Studio Code, or simply VS Code. VS Code was built using TypeScript, and was built for editing TypeScript. It has the ability to use third-party plugins, and can therefore be used as an IDE for a variety of programming languages, including Java, C, and C++. It is free to use, and uses the Electron framework, meaning that it can be run on Windows, Linux or macOS. Installation is as simple as downloading the installer from https://code.visualstudio.com/download and running it.

Assuming that you have successfully installed VS Code, we can set up a new project directory from a command prompt, and launch VS Code as follows:

mkdir ch01
cd ch01
touch hello_typescript.ts
code .
Here, we have created a new directory named ch01, changed into that directory, and created a new file named hello_typescript.ts. We have then launched VS Code with the command code .. The dot in this command refers to the current directory. This will launch VS Code as follows:


Figure 1.1: The Visual Studio Code editing window

The layout of VS Code is very similar to other text editors, with an Explorer window on the left, and a Source Code view on the right. Let's now write some TypeScript in the hello_typescript.ts file, as follows:

console.log(`hello TypeScript`);
This single line of code is the equivalent to the "Hello World" example that you will find in any other textbook on any other language. We are calling the log function on a globally available object named console, and giving it a string value of `hello TypeScript`. We can now generate a JavaScript file from this TypeScript file by executing the tsc command from the console as follows:

tsc hello_typescript.ts
Here, we are invoking the TypeScript compiler with a single command-line argument, which is the name of the TypeScript file we wish to generate JavaScript from. This will now generate a new JavaScript file named hello_typescript.js. We can execute this JavaScript using Node with the following command:

node hello_typescript.js
Here, we have invoked the Node runtime environment, and asked it to execute the JavaScript it finds in the file hello_typescript.js. The output of this command will be:

hello TypeScript
And that's it. It's as simple as creating a TypeScript file, generating JavaScript from it using the TypeScript compiler (tsc), and executing the resulting JavaScript using Node.

Now that we have an IDE set up, and can compile JavaScript from TypeScript, let's take a look at how we can generate different versions of JavaScript from the same TypeScript source files.

Template strings and JavaScript versions
In order to introduce how the TypeScript compiler can make our JavaScript development easier, let's take a quick look at something called template strings, or template literals. In the previous code snippet, you may have noticed that we used the backtick ( ` ) as a string delimiter for the text `hello TypeScript`. If we take a look at the generated JavaScript file (hello_typescript.js), we will see that the TypeScript compiler has modified this line of code to use double quotes, as follows:

console.log("hello TypeScript");
The use of the backtick ( ` ) to delineate strings gives us the ability to inject values directly into the string, as follows:

var version = `es6`;
console.log(`hello ${version} TypeScript`);
Here, we have declared a local variable named version, which holds a string with the value of `es6`. We have then modified the string that we are printing on the console to inject the value of the version string into the middle of the output by using the ${ ... variable name ... } syntax. If we compile this file, and take a look at the generated JavaScript, we will see that this now becomes:

var version = "es6";
console.log("hello " + version + " TypeScript");
Here, we can see that TypeScript has interpreted our template string, and generated the equivalent JavaScript, which uses double quotes ( " ) to surround each string, and the plus sign ( + ) to concatenate strings.

The use of template strings is actually valid JavaScript, but there is a significant catch to using them. Template strings have only been introduced into later versions of the JavaScript standard, in particular ES2015, also known as the 6th Edition, or just ES6. This means that you need an ES6-capable JavaScript runtime in order to use template strings. TypeScript, however, will generate JavaScript based on the version of the JavaScript runtime you are targeting.

If you are a little confused about JavaScript versions, don't worry, it is still a hotly debated topic. To simplify things, just bear in mind that any internet browser out in the wild will support at least ES3, or, to give it its full name, ECMA-262, 3rd Edition, which was published in 1999, 22 years ago.

As JavaScript is so widely used, its language features are published as a global standard, which is called the ECMAScript Standard. This standard has, at least historically, taken an extremely long time to update. After ES3 was published in 1999, it took a further 10 years to publish the next version, ES5, and a further 6 years to publish ES6. Since the 6th Edition was published in 2015, however, new standards have been published on a yearly basis.

Just bear in mind, however, that even though a new standard has been published, this does not mean that all internet browsers, or, more correctly, all JavaScript runtimes will support the new standard immediately.

Most modern internet browsers now support the ES5 standard. Unfortunately, we will have to wait for a number of years before we can say that most modern internet browsers support the ES6 standard. This means that we must be mindful of our target audience, and target runtime, if we attempt to use any ES6 features, such as template strings, within code that will be running within a browser. Older browsers, which could be found on older mobile phones, for example, will support at least the ES3 standard.

As mentioned earlier, TypeScript will generate JavaScript based on the target version of JavaScript that you specify. We can therefore write TypeScript code using any of the newest JavaScript standards, and TypeScript will correctly generate the equivalent JavaScript. Let's explore this concept a little further.

TypeScript project configuration
TypeScript uses a configuration file, named tsconfig.json, that holds a number of compilation options. We can use the tsc command-line compiler to generate a tsconfig.json file by using the --init command, as follows:

tsc --init
This --init option will automatically generate a tsconfig.json file within the current directory, which is used, amongst other things, to specify the target JavaScript version. Let's take a quick look at this file, as follows:

{
    "compilerOptions": {
        "target": "ES3",
        "module": "commonjs",
        "strict": true,
        "esModuleInterop": true,
        "skipLibCheck": true,
        "forceConsistentCasingInFileNames": true
    }
}
Here, we can see that the tsconfig.json file uses standard JSON syntax to specify an object that has one main property, named compilerOptions, and within this main property, a number of sub-properties named target, module, strict, and so on. The target property is used to specify the JavaScript version that we would like to generate for, and its value can be one of a number of options. If we double-click on the ES3 value, hit the Delete key, and then hit Ctrl+Space, VS Code will show us the valid values that can be used for this property as follows:


Figure 1.2: Visual Studio Code showing the available options for the JavaScript target version

Here, we can see that VS Code is using its IntelliSense, or code completion logic, to suggest what the valid values for the target property are. Let's modify this value to ES6, and see what the generated JavaScript looks like.

With a tsconfig.json file in place, we do not need to specify the name of the TypeScript file that we would like to compile; we can simply type tsc on the command line, as follows:

tsc
Here, the TypeScript compiler is reading the tsconfig.json file, and applying the compilation values that it finds there, to any .ts file that it finds in either the current directory, or any sub-directories. This means that in order to compile a TypeScript project that may contain many files in many sub-directories, we just need to type tsc in the root directory of the project.

Now that we have changed the target version of JavaScript that we wish to generate for, which is now ES6, let's take a look at the output of the compiler, in the file hello_typescript.js, as follows:

"use strict";
var version = `es6`;
console.log(`hello ${version} typescript`);
Ignoring the "use strict" line at the top of this file, we can see that the generated JavaScript has not changed from our original TypeScript file. This shows that the compiler is correctly generating ES6-compatible JavaScript, even though we have not modified our original TypeScript file.

Note that we will explore the various options in the tsconfig.json file, and how they affect our code in a later chapter.

Watching files for changes
TypeScript also has a handy option that will watch an entire directory tree, and if a file changes, it will automatically recompile the entire project. Let's run the TypeScript compiler in this mode as follows:

tsc -w
Here, we have added the -w command-line option to our tsc command. The output will now become:

[3:13:43 PM] Starting compilation in watch mode...
[3:13:43 PM] Found 0 errors. Watching for file changes.
Here, we can see that the TypeScript compiler is now in watch mode, and is watching files in our project directory for any changes.

Now that we have a simple, bare-bones development environment set up, let's start to explore some of the main features of TypeScript and start to see how it makes writing JavaScript better.

TypeScript basics
JavaScript is not strongly typed. It is a language that is very dynamic, as it allows for objects to change their types, properties, and behavior on the fly. TypeScript, however, is strongly typed, and as such will enforce rules that govern how we use variables, functions, and objects.

In this section of the chapter, we will work through the basics of the TypeScript language. We will start with the concepts of strong typing, or static typing as it is also known. We will then move on to exploring some of the basic types that the language uses, and how the language can detect what type a variable is, based on how and where it is used within our code. We will then tackle the basics of function signatures, show how to debug our code with VS Code, and finally see how to import and use third-party JavaScript libraries.

Strong typing
Strong typing, or static typing as it is also known, means that when we create a variable, or define a parameter in a function, we specify what type it is. Once this type has been specified, we cannot change it. Loose typing is the exact opposite of this concept, and JavaScript is a loosely typed language.

As an example of loose typing in JavaScript, let's create a JavaScript file named test_javascript.js, and add the following code:

var test = "a string";
console.log("test = " + test);
test = 1;
console.log("test = " + test);
test = function (a, b) {
    return a + b;
}
console.log("test = " + test);
On the first line of this code snippet, we have declared a local variable named test, and assigned a string value of "a string" to it. We then use our handy console.log function to print its value to the console. We then assign a numeric value of 1 to the test variable, and again print its value to the console. Finally, we assign a function that takes two parameters, named a and b, to the test variable, and print its value to the console. If we run this code, by typing node test_javascript.js, we will get the following results:

test = a string
test = 1
test = function (a, b) {
    return a + b;
}
Here, we can clearly see the changes that we are making to the test variable. It changes from a string value to a numeric value, and then finally becomes a function.

Unfortunately, changing the type of a variable at runtime can be a very dangerous thing to do. If your code is expecting a variable to be a number, and tries to perform calculations on it, the results of these calculations may be unexpected if the variable held a string. In a similar way, if a variable is a function that does something, and someone inadvertently changes that variable into a string, a whole block of functionality has suddenly become lost.

TypeScript is a strongly typed language. This means that if you declare a variable to be of type string, then you need to treat it as a string throughout your code base. So how do we declare that a variable should be of a particular type? Well, TypeScript introduces a simple notation using the colon ( : ) symbol to indicate what type a variable should be, as follows:

var myString: string = `this is a string`;
Here, we can see that we have declared a variable named myString, and then followed it by a colon and the string keyword, before we assign a value. This technique is called type annotation, and it sets the type of the myString variable to be of type string. If we were to now try and assign a number to it, as follows:

myString = 1;
TypeScript will generate a compilation error, as follows:

hello_typescript.ts:6:1 - error TS2322: Type '1' is not assignable to type 'string'.
6 myString = 1;
  ~~~~~~~~
Here, we have a TS2322 error, which indicates that the type '1' (which is of type number) is not assignable to a variable that has been specified as being of type string. Note that the output of the compiler will let us know which line is generating this error, as well as where in the line the error is occurring.

Basic types
TypeScript provides a number of basic types that can be used for type annotation. As an example of these types, let's focus on four common types, namely string, number, boolean, and array. We will cover the rest of these basic types, such as any, null, never, and others, in a later chapter, but for now, let's use these four basic types as follows:

var myBoolean : boolean = true;
var myNumber : number = 1234;
var myStringArray : string[] = [`first`, `second`, `third`];
Here, we have declared a variable named myBoolean, which is of type boolean, and is set to the value true. We have then declared a variable named myNumber, which is of type number, and is set to the value 1234. Finally, we have declared a variable named myStringArray, which is of type string array, using the [] array syntax. All of the following statements are now invalid:

myBoolean = myNumber;
myStringArray = myNumber;
myNumber = myStringArray[0];
Here, we are attempting to assign the value of myNumber to the myBoolean variable, and then we are attempting to assign the value of myNumber to the myStringArray variable. Finally, we are attempting to assign the value of the first element of myStringArray to the myNumber variable. The following errors will be produced:

error TS2322: Type 'number' is not assignable to type 'boolean'.
error TS2322: Type 'number' is not assignable to type 'string[]'.
error TS2322: Type 'string' is not assignable to type 'number'.
This output is clearly telling us that we are not allowed to assign values from one type to another. Let's fix this code as follows:

myBoolean = myNumber === 456;
myStringArray = [myNumber.toString(), `5678`];
myNumber = myStringArray.length;
console.log(`myBoolean = ${myBoolean}`);
console.log(`myStringArray = ${myStringArray}`);
console.log(`myNumber = ${myNumber}`);
Here, we are assigning the value of the statement myNumber === 456 to the myBoolean variable. The type of the equals expression is boolean, as it will result in either true or false. So in this case, the right-hand side of the assignment is of the same type as the left-hand side of the assignment, and is therefore valid TypeScript.

In the same manner, we are then converting the myNumber variable into a string using the .toString() function, and creating an array out of it, with the value "5678" by enclosing both in two square brackets [ and ]. Finally, we are assigning the length property of the myStringArray array to the myNumber variable. Again, this is allowed, since the length property of an array is of type number. The output of this code is as follows:

myBoolean = false
myStringArray = 1234,5678
myNumber = 2
Here, we can see that the console.log statements are producing the expected results. The myNumber variable is not equal to the value 456, hence the myBoolean variable is set to false. The value of the myStringArray variable is now 1234 and 5678, and the value of the myNumber variable is the length of the myStringArray array, which is 2.

Inferred typing
TypeScript also uses a technique called inferred typing, or type inference, to determine the type of a variable. This means that even if we do not explicitly specify the type of a variable, the compiler will determine its type based on when it was first assigned. Again, once the variable has a type, normal type comparisons will be used. As an example of this, consider the following code:

var inferredString = "this is a string";
var inferredNumber = 1;
inferredNumber = inferredString;
Here, we have created two variables named inferredString and inferredNumber, and assigned a string value to the first variable, and a numeric value to the second. We are then attempting to assign the value of inferredString to the variable inferredNumber. This code will generate the following error:

error TS2322: Type 'string' is not assignable to type 'number'.
What this error is telling us is that TypeScript has inferred that the type of the variable inferredString is of type string, even though we have not used the explicit : string type syntax. In the same manner, TypeScript has inferred that the type of the variable inferredNumber is of type number, hence the error.

VS Code will show the type of a variable if you hover your mouse over it when editing. This feature is pretty handy when dealing with inferred types.

Duck typing
TypeScript also uses a method called duck typing for more complex variable types. Duck typing suggests that "if it looks like a duck, and quacks like a duck, then it probably is a duck." In other words, two variables are considered to have the same type if they have the same properties and methods. Let's test this theory out with the following code:

var nameIdObject = { name: "myName", id: 1, print() { } };
nameIdObject = { id: 2, name: "anotherName", print() { } };
Here, we have defined a variable called nameIdObject, which is a standard JavaScript object, and has a name property, an id property, and a print function. We then reassign the value of this variable to another object that also has a name property, an id property, and a print function. The compiler will use duck typing in this instance to figure out if this assignment is valid. In other words, if an object has the same set of properties and functions, then they are considered to be of the same type.

To further illustrate this technique, let's see how the compiler reacts if we attempt to break this rule, as follows:

nameIdObject = { id: 3, name: "thirdName" };
Here, we are attempting to assign an object to nameIdObject that does not have all of the required properties. TypeScript will generate the following error:

error TS2741: Property 'print' is missing in type '{ id: number; name: string; }' but required in type '{ name: string; id: number; print(): void; }'.
Here, we can see that the error message clearly states that the print property is missing, as TypeScript is using duck typing to ensure type safety.

Note that these errors will occur if the name of a property, the type of a property, or the number of properties are not exactly the same when assigning a value to an object.

Let's take a look at a slightly different example of duck typing, as follows:

var obj1 = { id: 1, print() { } };
var obj2 = { id: 2, print() { }, select() { } }
obj1 = obj2;
obj2 = obj1;
Here, we have two objects, named obj1 and obj2, which are identical except that obj2 has an extra select function. We then assign the value of obj2 to obj1. This will not generate an error, as the type of obj2 has all of the properties of the type of obj1. This means that the duck typing method is checking whether obj2 has at least the properties of obj1, which it does.

The last line of this code snippet, where we assign the value of obj1 to obj2, will generate an error as follows:

Property 'select' is missing in type '{ id: number; print(): void; }' but required in type '{ id: number; print(): void; select(): void; }'
Here, we can see that the compiler has correctly identified that the type of obj1 does not have at least all of the properties of obj2, as it is missing the select function.

Remember that the duck typing examples used here are also using inferred typing, so the type of an object is inferred from when it is first assigned.

Function signatures and void
Thus far, we have had a quick tour of the basics of the TypeScript language, how it introduces type annotations for variables, and how it uses inferred typing and duck typing to check for valid assignments. One of the best features of using type annotations in TypeScript is that they can also be used to strongly type function signatures.

To explore this feature a little further, let's write a JavaScript function to perform a calculation, as follows:

function calculate(a, b, c) {
    return (a * b) + c;
}
console.log("calculate() = " + calculate(2, 3, 1));
Here, we have defined a JavaScript function named calculate that has three parameters, a, b, and c. Within this function, we are multiplying a and b, and then adding the value of c. The output of this code is what we expect, as follows:

calculate() = 7
The result is correct, as 2 * 3 = 6, and 6 + 1 = 7. Now, let's see what happens if we incorrectly call the function with strings, instead of numbers, as follows:

console.log("calculate() = " + calculate("2", "3", "1"));
The output of this code sample is:

calculate() = 61
The result of 61 is very different from the expected result of 7. So what is going on here?

If we take a closer look at the code in the calculate function, we can figure out what JavaScript does when it tries to mix variables of different types. The product of two numbers, that is, ( a * b ), will generate a numeric value. So even though our values of a and b are strings, JavaScript will attempt to convert these to numbers before multiplying them together. So we end up with 3 * 2 = 6. Unfortunately, the + operator can be used on both numbers and strings, and if one of the arguments is a string, JavaScript will convert both to strings prior to addition. This results in the string "6" being appended to the string "1", resulting in the string "61".

This code snippet is an example of how JavaScript can modify the type of a variable depending on how it is actually used. This means that in order to work effectively with JavaScript, we need to be aware of this sort of type conversion, and understand when and where it could take place. Obviously, these sorts of automatic type conversions can cause unwanted behavior in our code.

Let's now write the equivalent function in TypeScript, but this time specify that all arguments must be of type number, as follows:

function calculate(a: number, b: number, c: number): number {
    return (a * b) + c;
}
console.log(`calculate() = ${calculate(3, 2, 1)}`);
Here, we have specified that the arguments a, b, and c in our TypeScript version of the calculate function must all be of type number. In addition to this, we can see that we have specified the return type of the entire function to be of type number, by placing a type annotation at the end of the function definition, that is, : number { ... }.

This also ensures that the caller of this function knows that the function will return a value of type number.

With our function definition now specifying a type for each argument, attempting to call this function with strings will fail, as follows:

console.log(`calculate() = ${calculate("3", "2", "1")}`);
Here, TypeScript will generate the following error:

error TS2345: Argument of type '"3"' is not assignable to parameter of type 'number'.
This error message clearly tells us that we cannot use a string as an argument where a numeric argument is expected. We also cannot use the value that is returned by the function incorrectly as follows:

var returnedValue: string = calculate(3, 2, 1);
This statement will generate the following error:

error TS2322: Type 'number' is not assignable to type 'string'.
So the TypeScript compiler is also telling us that the return value of the calculate function is of type number, and so we cannot assign it to a variable that is of type string.

So, what about functions that do not return a value? This is where the TypeScript keyword void comes in handy. Consider the following code:

function printString(a: string) : void {
    console.log(a);
}
var returnedValue : string = printString("this is a string");
Here, we have defined a function named printString that takes a single parameter named a, which is of type string. We have also specified that this function will not return a value, by using the return type of void. The last line of this code snippet will therefore generate the following error:

error TS2322: Type 'void' is not assignable to type 'string'.
This error message is telling us that the printString function does not return anything, and therefore returns a type of void. If we attempt to assign something of a void type to a string, we will generate this type of error.

VS Code IntelliSense
The ability to add type annotations to variables and functions means that the TypeScript compiler knows how each portion of our code should be used. Once the code has been parsed by the compiler, it makes these annotations available through the TypeScript Language Service. VS Code, and indeed other editors, can access this Language Service in real time, and build up code completion hints, or IntelliSense.

Let's take a quick look at how the VS Code editor gives us type information. If we want to call the calculate function that we created earlier, all we need to do is to start typing a part of the word calculator, and VS Code will show us what it knows about this function, as follows:


Figure 1.3: VS Code IntelliSense showing the definition of a function

Here, we can see that VS Code is telling us that the calculate function has three arguments, which are all of type number, and that it returns a number.

This sort of information is incredibly useful to a modern programmer, and makes writing and understanding code so much easier, and less prone to errors. We can also document the functions we are writing using JSDoc-style comments, and this JSDoc documentation will be included in the IntelliSense information, as shown in the following screenshot:


Figure 1.4: VS Code IntelliSense showing documentation from JSDoc-style comments

Here, we have updated the printString function, and included some JSDoc-style comments in the comment immediately preceding the function definition itself. In these comments, we are able to provide a description of the function, and we are also able to provide a description for each of the function parameters. VS Code will now include this documentation whenever we invoke the IntelliSense options in our IDE.

VS Code debugging
Using an IDE such as VS Code allows us to debug our code pretty easily. In order to do this, we will need to modify the TypeScript compilation options, found in tsconfig.json, and add the sourceMap property as follows:

`sourcemap:true`

This compiler option will now generate a .map file as well as a .js file for each of our TypeScript files. Remember that Node is a JavaScript runtime, and will only execute JavaScript code. The VS Code editor, therefore, needs to know how to map the executing JavaScript code back to our TypeScript source. This is what the .map file is used for.


see launch.js

## exploring type system 

 Once we have set a type for a variable, the compiler will ensure that this type is maintained throughout our code base. Unfortunately, this means that we cannot re-create JavaScript where the JavaScript does not match these strict type rules. Consider the following JavaScript code:
 
 any 
 var item1 = <any>{ id: 1, name: "item1" }
 casting 
 
 Another variant of this casting technique is to use the as keyword, as follows:

var item1 = { id: 1, name: "item1" } as any;
item1 = { id: 2 };
Union types

type guards
function addWithUnion(
    arg1: string | number,
    arg2: string | number
) {
    return arg1 + arg2;
}

function addWithTypeGuard(
    arg1: string | number,
    arg2: string | number
) {
    if (typeof arg1 === "string") {
        // arg 1 is treated as a string
        console.log(`arg1 is of type string`);
        return arg1 + arg2;
    }
    if (typeof arg1 === "number" && typeof arg2 === "number") {
        // both are numbers
        console.log(`arg1 and arg2 are numbers`);
        return arg1 + arg2;
    }
    console.log(`default return treat both as strings`)
    return arg1.toString() + arg2.toString();
}

type aliases


type StringOrNumber = string | number;
function addWithTypeAlias( 
    arg1: StringOrNumber,
    arg2: StringOrNumber
    ) {
    return arg1.toString() + arg2.toString();
}


One last note on enums is that we can set the numerical value of an enum value to whatever we like, as shown in the following code:

enum DoorStateSpecificValues {
    Open = 3,
    Closed = 7,
    Unspecified = 256
}


String enums
A further variant of the enum type is what is known as a string enum, where the numerical values are replaced with strings, as follows:

enum DoorStateString {
    OPEN = "Open",
    CLOSED = "Closed"
}
console.log(`OPEN = ${DoorStateString.OPEN}`);


Const enums
The final variant of the enum family is called the const enum, which adds the const keyword before the enum definition, as follows:

const enum DoorStateConst {
    Open = 10,
    Closed = 20
}
console.log(`const Closed = ${DoorStateConst.Open}`);


`let array = ["123", "456", "789"];
delete array[0];
for (let i = 0; i < array.length; i++) {
    console.log(`array[${i}] = ${array[i]}`);
}`

array[0] = undefined
array[1] = 456
array[2] = 789

As we can see, the array still has three elements, but the first element has been set to undefined, which is the result of deleting this array element.

Null
Along with undefined, JavaScript also allows values to be set to null. Setting a value to null is intended to indicate that the variable is known, but has no value, as opposed to undefined, where the variable has not been defined in the current scope. Consider the following code:

Nullish coalescing

`function nullishCheck(a: number | undefined | null) {
    console.log(`a : ${a ?? `undefined or null`}`);
}`

Null or undefined operands

`function testNullOperands(a: number, b: number | null | undefined) {
    let addResult = a + (b ?? 0);
}`

Definite assignment


The second place that we can use the definite assignment assertion syntax is in the definition of the variable itself, as follows:

var globalString!: string;

Object
TypeScript introduces the object type to cover types that are not primitive types. This includes any type that is not number, boolean, string, null, symbol, or undefined. Consider the following code:

let structuredObject: object = {
    name: "myObject",
    properties: {
        id: 1,
        type: "AnObject"
    }
}
function printObjectType(a: object) {
    console.log(`a: ${JSON.stringify(a)}`);
}

Unknown
TypeScript introduces a special type into its list of basic types, which is the type unknown. The unknown type can be seen as a type-safe alternative to the type any. A variable marked as unknown can hold any type of value, similar to a variable of type any. The difference between the two, however, is that a variable of type unknown cannot be assigned to a known type without explicit casting.

Never
The final primitive type in the TypeScript collection is a type of never. This type is used to indicate instances where something should never occur. Even though this may sound confusing, we can often write code where this occurs. Consider the following code:


function can never return anythiing

Object spread
When working with basic JavaScript objects, we often need to copy the properties of one object to another, or do some mixing and matching of properties from various objects. In TypeScript, we can use an ES7 technique known as object spread to accomplish this. Consider the following code:

`let firstObj: object = { id: 1, name: "firstObj" };
let secondObj: object = { ...firstObj };
console.log(`secondObj : ${JSON.stringify(secondObj)}`);`

`let nameObj: object = { name: "nameObj name" };
let idObj: object = { id: 1 };
let obj3 = { ...nameObj, ...idObj };
console.log(`obj3 = ${JSON.stringify(obj3)}`);`

Spread precedence
When using object spread, properties will be copied incrementally. In other words, if two objects have a property with the same name, then the object that was specified last will take precedence. As an example of this, consider the following:

`let objPrec1: object = { id: 1, name: "obj1 name" };
let objPrec2: object = { id: 1001, desc: "obj2 description" };
let objPrec3 = { ...objPrec1, ...objPrec2 };
console.log(`objPrec3 : ${JSON.stringify(objPrec3, null, 4)}`);`

Spread with arrays
Interestingly, the spread syntax can also be used with arrays. Consider the following code:

`let firstArray = [1, 2, 3];
let secondArray = [3, 4, 5];
let thirdArray = [...firstArray, ...secondArray];
console.log(`third array = ${thirdArray}`);`

Tuples
Tuples are a method of defining a type that has a finite number of unnamed properties, with each property having an associated type. When using a tuple, all of the properties must be provided. This can best be explained in an example, as follows:

`let tuple1: [string, boolean];
tuple1 = ["test", true];
tuple1 = ["test"]; //error`

Tuple destructuring
As tuples use the array syntax, they can be destructured or disassembled in two ways. The first way of destructuring a tuple uses the simple array syntax, as follows:

`let [tupleString, tupleBoolean] = tuple1;
console.log(`tupleString = ${tupleString}`);
console.log(`tupleBoolean = ${tupleBoolean}`);`

Optional tuple elements
Note that tuple elements can be marked optional by using the question mark (?) after the type, as follows:

`let tupleOptional: [string, boolean?]; //optional
tupleOptional = ["test", true];
tupleOptional = ["test"];
console.log(`tupleOptional[0] : ${tupleOptional[0]}`);
console.log(`tupleOptional[1] : ${tupleOptional[1]}`);`

Tuples and spread syntax
We are also able to use spread syntax to define a tuple that can have a variable number of elements. Consider the following code:

let tupleRest: [number, ...string[]];
tupleRest = [1];
tupleRest = [1, "string1"];
tupleRest = [1, "string1", "string2"];

Object destructuring
In a similar way to tuples, standard objects can be also be destructured. Consider the following example:

let complexObject = {
    aNum: 1,
    bStr: "name",
    cBool: true
}
`let { aNum, bStr, cBool } = complexObject;`

Note that we are also able to rename the variable names during the destructuring step as follows:

`let { aNum: objId, bStr: objName, cBool: isValid } 
    = complexObject;
console.log(`objId : ${objId}`);
console.log(`objName : ${objName}`);
console.log(`isValid : ${isValid}`);`

Functions
In this section of the chapter, we will take a look at functions and their definitions, and how the TypeScript language can be used to introduce further type safety whenever functions are used. Functions can use many of the concepts that we have already discussed, including optional parameters and spread syntax. We will also discuss how we can define a function signature in such a manner that if a function defines another function as a parameter, we can make sure that the function we pass in has the correct parameters. Finally, we will take a look at how to define function overrides.

Optional parameters

2
Exploring the Type System
Thus far, we have covered the basic principles of using types in TypeScript. We already know how to define a type for a variable or a function argument, and some of the rules that the compiler uses in order to ensure strongly typed code. We have discussed some of the basic, or primitive, types (number, string, and boolean), as well as the array type. However, we have only just skimmed the surface of the TypeScript type system.

In this chapter, we will explore all of the primitive types that are available, as well as some language elements that we can use to better describe how to use these types. We will discuss when and where to use these types and language elements, and even when not to use some types.

This chapter is broken up into five main sections. In the first section, we will explore the any type, the let and const keywords, and union types. The concept of union types feeds directly into a discussion on type guards, and type aliases. We will round this first section off with a discussion on enums, including string enums and const enums.

The second section of this chapter will work through the remainder of the primitive types that are available for use, including undefined, null, object, and unknown. There are also language features that help us when we have to work with values that could be undefined or null, including optional chaining, nullish coalescing, and definite assignment. We will also discuss the never type, and how it can be used to identify logic errors.

In the third section of this chapter, we will discuss the object spread syntax, which is used to combine properties of one object with the properties of another. We will see how this spread syntax can also be used with arrays as a handy syntax for combining arrays and array values.

The fourth section of this chapter is all about tuples, what they are, and how they can be used.

The fifth and final section of this chapter deals with the use of types within functions and function signatures. We will see how we can use optional parameters in a function, default parameters, and rest syntax. We will also show how we can define a function signature as a function parameter, in order to ensure that any function provided as a callback function has the correct parameters and parameter types.

There is a lot of ground to cover in this chapter. It will, however, give us a great understanding of the TypeScript type system. We will explore what types are available for use, how and where these types can be used, and what language features are available to help with our use of types.

Let's explore the TypeScript type system.

any, let, unions, and enums
We have already seen how TypeScript introduced a simple type annotation syntax in order to promote strong typing, which helps us ensure that we are using variables as they are intended to be used within our code. We also know that TypeScript generates JavaScript, and as such must be able to mimic what JavaScript can do. Unfortunately, matching what JavaScript can do may also include relaxing the strict typing rules, and allowing a string value to be assigned to a numeric value, for example. In this section of the chapter, we will introduce the any type, which completely removes the strict type rules associated to a variable, and allows the fluid and unconstrained use of variables, like in JavaScript. We will also strongly recommend not using the any type, as much as possible.

We will also explore the let and const keywords, which are language elements introduced in later versions of the ECMAScript standard, and take a look at how they can be used in TypeScript. We will then take a look at union types, type guards, and type aliases, which allow us to clearly define how we would like our code to manage groups of types. Finally, we will discuss enums, which are a mechanism to replace magic strings, or magic numbers, with human-readable values.

The any type
We have already seen how TypeScript uses the type annotation syntax to define what type a particular variable or function parameter should be. Once we have set a type for a variable, the compiler will ensure that this type is maintained throughout our code base. Unfortunately, this means that we cannot re-create JavaScript where the JavaScript does not match these strict type rules. Consider the following JavaScript code:

var item1 = { id: 1, name: "item 1" };
item1 = { id: 2 };
Here, we create a variable named item1 and assign to it an object value that has an id and name property. We then reassign this variable to an object that only has an id property. This is valid JavaScript code, and therefore, if we are using TypeScript to generate JavaScript, we will need to be able to mimic this functionality.

TypeScript introduces the any type for such occasions. Specifying that an object has a type of any will, in essence, remove the TypeScript strict type checking. The following TypeScript code shows how to use the any type to mimic our original JavaScript code, as follows:

var item1: any = { id: 1, name: "item1" }
item1 = { id: 2 };
Here, we have specified that the type of the item1 variable is any. The any type then allows a variable to follow JavaScript's loosely defined typing rules so that anything can be assigned to anything. Without the type specifier of any, the second line of this code snippet would normally generate an error.

While the any type is a necessary feature of the TypeScript language, and is used for backward compatibility with JavaScript, its usage should be limited as much as possible. As we have seen with untyped JavaScript, excessive use of the any type will quickly lead to coding errors that will be difficult to find. Rather than using the any type, try to figure out the correct type of the object that you are using, and then use this type instead.

We will discuss the concept of interfaces in the next chapter, which are a way of defining custom types. Using interfaces allows us to cover almost every possible combination of types, meaning that using the any type, in most cases, is unnecessary.

We use an acronym within our programming teams, which is: Simply Find an Interface for the Any Type (S.F.I.A.T), pronounced sveat, or sweat. While this may sound rather odd, it simply brings home the point that the any type can and should be defined as an interface, so simply find it.

In short, avoid the any type at any cost.

Explicit casting
As with any strongly typed language, there comes a time when we need to explicitly specify the type of an object. This is generally used when working with object-oriented concepts, such as classes, abstract classes, and interfaces, but this technique can be used on primitive TypeScript types as well.

Let's rewrite our previous example using explicit casting, as follows:

var item1 = <any>{ id: 1, name: "item1" }
item1 = { id: 2 };
Here, we have replaced the : any type specifier on the left-hand side of the assignment operator with an explicit cast of <any> on the right-hand side of the assignment operator. This explicit casting technique uses the angled bracket syntax, that is, < and >, surrounding the name of the type. In essence, this syntax is equivalent to our earlier example, and specifies that the type of the item1 variable is any.

Another variant of this casting technique is to use the as keyword, as follows:

var item1 = { id: 1, name: "item1" } as any;
item1 = { id: 2 };
Here, we have defined the variable named item1, similar to our earlier definitions, but have appended the keyword as and then named the type that this variable should be treated as, which in this case is any. This example, and the previous example, are equivalent in outcome, as the item1 variable is of type any no matter which version of the explicit casting syntax we use.

Hopefully, this will be one of the last times that we use the type of any. Remember that using the type of any removes all strict type checking, and is therefore the antithesis of TypeScript. There may be very specific edge cases where we will still need to use the any type, but these should be few and far between.

The let keyword
The fluid nature of JavaScript variables can sometimes cause errors when we inadvertently define variables with the same name, but in a different scope within a code block. Consider the following TypeScript code:

var index: number = 0;
if (index == 0) {
    var index: number = 2;
    console.log(`index = ${index}`);
}
console.log(`index = ${index}`);
Here, we define a variable named index of type number using the var keyword, and assign it a value of 0. We then test if this value is equal to 0, and if it is, we enter a code block. The first statement in this code block defines a variable named index, of type number, and assigns the value 2 to it. We then print the value of the index variable both inside this code block and outside of it. The output of this code is as follows:

index = 2
index = 2
What this is showing us is that even though we thought we created a new variable within the if code block named index, this variable re-declaration actually points to the original index variable and does not create a new one. So, setting the value of the index variable within the code block will modify the value of the index variable outside of the code block as well. This is not what was intended.

The ES6 JavaScript specification introduces the let keyword to prevent this from happening. Let's refactor the preceding code using the let keyword, as follows:

let index: number = 0;
if (index == 0) {
    let index: number = 2;
    console.log(`index = ${index}`);
}
console.log(`index = ${index}`);
Here, we are defining the index variable by using the let keyword instead of the var keyword, both in the original declaration and within the if code block. No other change to the code is necessary. The output of this code is as follows:

index = 2
index = 0
Here, we can see that modifying the variable named index inside of our if code block does not affect the variable named index that is defined outside of the code block. They are seen as two separate variables.

It is best practice to use the let keyword to define variables, and not to use the var keyword at all. By using let, we are being more explicit about the intended use of these variables, which will help the compiler to pick up any mistakes in our code where these rules are broken.

Const values
When working with variables, it sometimes helps to indicate that the variable's value cannot be modified after is has been created with a specific value. TypeScript uses the const keyword, which was introduced in ES6, in order to accomplish this. Consider the following code:

const constValue = "this should not be changed";
constValue = "updated";
Here, we have defined a variable named constValue and indicated that its value cannot be changed using the const keyword. Attempting to compile this code will result in the following error:

error TS2588: Cannot assign to 'constValue' because it is a constant.
This error is being generated because of the second line in this code snippet. We are attempting to modify the value of the constValue variable, which is not allowed.

It is best practice to identify constant variables within our code and explicitly mark them as const. The use of const and let clearly indicates to the reader of the code the intent of the variable. A variable marked as const cannot be changed, and a variable declared with let is a block-scoped temporary variable.

Union types
TypeScript allows us to express a type as a combination of two or more other types. These types are known as union types, and they use the pipe symbol ( | ) to list all of the types that will make up this new type. Consider the following code:

function printObject(obj: string | number) {
    console.log(`obj = ${obj}`);
}
printObject(1);
printObject("string value");
Here, we have defined a function named printObject that has a single parameter named obj. Note how we have specified that the obj parameter can be either of type string or of type number by listing them as a union type with a pipe separator. The last two lines of the code call this function with a number, and then with a string. The output of this code is as follows:

obj = 1
obj = string value
Here, we can see that the printObject function will work with either a string or a number.

Type guards
When working with union types, the compiler will still apply its strong typing rules to ensure type safety. As an example of this, consider the following code:

function addWithUnion(
    arg1: string | number,
    arg2: string | number
) {
    return arg1 + arg2;
}
Here, we have defined a function named addWithUnion that accepts two parameters and returns their sum. The arg1 and arg2 parameters are union types, and can therefore hold either a string or a number. Unfortunately, this code will generate the following error:

error TS2365: Operator '+' cannot be applied to types 'string | number' and 'string | number'
What the compiler is telling us here is that it cannot tell what type it should use when it attempts to add arg1 to arg2. Is it supposed to add a string to a number, or a string to a string? As we discussed in Chapter 1, Up and Running Quickly, the effects of adding a string and a number in JavaScript can lead to unwanted results.

This is where type guards come in. A type guard is an expression that performs a check on our type, and then guarantees that type within its scope. Let's re-write our previous function with a type guard as follows:

function addWithTypeGuard(
    arg1: string | number,
    arg2: string | number
) {
    if (typeof arg1 === "string") {
        // arg 1 is treated as a string
        console.log(`arg1 is of type string`);
        return arg1 + arg2;
    }
    if (typeof arg1 === "number" && typeof arg2 === "number") {
        // both are numbers
        console.log(`arg1 and arg2 are numbers`);
        return arg1 + arg2;
    }
    console.log(`default return treat both as strings`)
    return arg1.toString() + arg2.toString();
}
Here, we have added two if statements within the body of our code. The first if statement uses the JavaScript typeof keyword to test what type the arg1 argument is. The typeof operator will return a string depending on what the value of the argument is at runtime. This can be one of the following possible values: "number", "string", "boolean", "object", or "undefined". If the type of the arg1 argument is a string, then the first code block will execute. Within this code block, the compiler knows that arg1 is of type string, and will therefore treat arg1 to be of type string within the code block. Our type guard, therefore, is the code block after the check for the type of string.

Our second if statement has two typeof checks and is checking whether both the arg1 and arg2 arguments are of type number. If they are both numbers, then both arg1 and arg2 are treated as type number within the code block. This type guard, therefore, will treat both the arg1 and arg2 arguments as type number within this code block.

Let's test this function as follows:

console.log(` "1", "2" = ${addWithTypeGuard("1", "2")}`);
console.log(`  1 ,  2  = ${addWithTypeGuard(1, 2)}`);
console.log(`  1 , "2" = ${addWithTypeGuard(1, "2")}`);
Here, we call the addWithTypeGuard function three times: once with both arguments of type string, once with both arguments of type number, and the third time with a number and a string. The output of this code is as follows:

arg1 is of type string
 "1", "2" = 12
arg1 and arg2 are numbers
  1 ,  2  = 3
default return treat both as strings
  1 , "2" = 12
Here, we can see that our first call to the addWithTypeGuard function is using two arguments that are strings. The code identifies the first argument as being of type string and therefore enters the first if statement block.

The concatenation of the string "1" with the string "2" results in the string "12". The second call to the addWithTypeGuard function uses two numbers as arguments, and our code therefore identifies both arguments as numbers, and as such adds the value 1 and the value 2, resulting in 3. The third call to the addWithTypeGuard function uses a number as the first argument and a string as the second. The code therefore falls through to our default code, and treats both arguments as strings.

Type aliases
TypeScript introduces the concept of a type alias, where we can create a named type that can be used as a substitute for a type union. Type aliases can be used wherever normal types are used and are denoted by using the type keyword, as follows:

type StringOrNumber = string | number;
function addWithTypeAlias( 
    arg1: StringOrNumber,
    arg2: StringOrNumber
    ) {
    return arg1.toString() + arg2.toString();
}
Here, we have defined a type alias named StringOrNumber by using the type keyword and assigning a type union of string or number to it. We then use this StringOrNumber type in our function definition for the addWithTypeAlias function. Note that both the arg1 and arg2 arguments are of type StringOrNumber, which will allow us to call this function with either strings or numbers.

Type aliases are a handy way of specifying a type union and giving it a name, and are particularly useful when the type union is used over and over again.

Enums
Enums are a special type whose concept is similar to other languages such as C#, C++, or Java, and provides the solution to the problem of special numbers, or special strings. Enums are used to define a human-readable name for a specific number or string. Consider the following code:

enum DoorState {
    Open,
    Closed
}
function checkDoorState(state: DoorState) {
    console.log(`enum value is : ${state}`);
    switch (state) {
        case DoorState.Open:
            console.log(`Door is open`);
            break;
        case DoorState.Closed:
            console.log(`Door is closed`);
            break;
    }
}
Here, we start by using the enum keyword to define an enum named DoorState. This enum has two possible values, either Open or Closed. We then have a function named checkDoorState that has a single parameter named state, of type DoorState. This means that the correct way to call this function is with one of the values that the DoorState enum provides us. This function starts by logging the actual value of the state parameter to the console, and then executes a switch statement. This switch statement simply logs a message to the console depending on the value of the state parameter that was passed in.

We can now run this code as follows:

checkDoorState(DoorState.Open);
checkDoorState(DoorState.Closed);
Here, we are calling the checkDoorState function, once for each possible value within the DoorState enum. The output of this code is as follows:

enum value is : 0
Door is open
enum value is : 1
Door is closed
Here, we can clearly see that the compiler has generated a numerical value for each of our defined enum values. The numerical value for the enum value DoorState.Open is 0, and likewise, the numerical value of DoorState.Closed has been set to 1. This all occurs under the hood.

Using enums helps us to provide a clear set of values for a variable or function parameter. They also provide a tried and tested way of eliminating so called magic numbers by defining a limited number of possible values.

One last note on enums is that we can set the numerical value of an enum value to whatever we like, as shown in the following code:

enum DoorStateSpecificValues {
    Open = 3,
    Closed = 7,
    Unspecified = 256
}
Here, we have defined an enum named DoorStateSpecificValues that has three possible values, Open, Closed, and Unspecified. We have also overridden the default values for this enum such that the Open value will be 3, the Closed value will be 7, and the Unspecified value will be 256.

String enums
A further variant of the enum type is what is known as a string enum, where the numerical values are replaced with strings, as follows:

enum DoorStateString {
    OPEN = "Open",
    CLOSED = "Closed"
}
console.log(`OPEN = ${DoorStateString.OPEN}`);
Here, we have an enum named DoorStateString and have replaced the numerical values with string values for each of the defined enum values. We then log a message to the console with the value of the DoorStateString.OPEN enum. The output of this code is as follows:

OPEN = Open
As expected, the compiler is resolving the enum value of DoorStateString.OPEN to the "Open" string.

Const enums
The final variant of the enum family is called the const enum, which adds the const keyword before the enum definition, as follows:

const enum DoorStateConst {
    Open = 10,
    Closed = 20
}
console.log(`const Closed = ${DoorStateConst.Open}`);
Here, we have defined a const enum named DoorStateConst, which has provided two possible values. We then log the value of the DoorStateConst.Open enum value to the console.

const enums have been introduced for performance reasons. To see what happens under the hood, we will need to view the JavaScript that this code produces. Firstly, let's take a look at the JavaScript implementation of the DoorState enum that we were discussing earlier. As the DoorState enum has not been marked as const, its JavaScript implementation is as follows:

var DoorState;
(function (DoorState) {
    DoorState[DoorState["Open"] = 0] = "Open";
    DoorState[DoorState["Closed"] = 1] = "Closed";
})(DoorState || (DoorState = {}));
Here, we have some pretty complex-looking JavaScript. We will not discuss this implementation here, but instead we'll take a look at what this structure becomes when we examine it in a debugger, such as the one in VSCode, as shown in the following screenshot:


Figure 2.1: VSCode debugging window showing the internal structure of an enum

Here, we are viewing the object named DoorState within the VSCode debugger. We can see the DoorState object has four properties, named Closed, Open, 0, and 1. It also has a number of functions that have been attached to the object prototype, including a constructor and the hasOwnProperty and toString functions, to name a few. The purpose of this exercise was to show that when we create an enum, the compiler will generate a fully fledged JavaScript object, complete with properties and functions for the enum's implementation.

Let's now look at the generated JavaScript for a const enum:

console.log("const Closed = " + 10 /* Open */);
Here, we find that there is no actual implementation of the enum itself at all. The compiler has simply substituted the JavaScript code of 10 /* Open */ wherever we have used the const enum value of DoorStateConst.Open. This reduces the size of code that is generated, as the JavaScript runtime does not need to work with a full-blown JavaScript object in order to check a value.

More primitive types
In the last chapter, we discussed a few of the basic, or primitive, types that are available in TypeScript. We covered numbers, strings, and booleans, which are part of the group of primitive types, and we also covered arrays. While these represent some of the most basic and widely used types in the language, there are quite a few more of these primitive types, including undefined, null, unknown, and never. Related to these primitive types, we also have some language features, such as conditional expressions and optional chaining, that provide a convenient short-hand method of writing otherwise rather long-winded code. We will explore the remainder of the primitive types, as well as these convenient language features, in this part of the chapter.

Undefined
There are a range of circumstances where the value of something in JavaScript is undefined. Let's take a look at an example of this, as follows:

let array = ["123", "456", "789"];
delete array[0];
for (let i = 0; i < array.length; i++) {
    console.log(`array[${i}] = ${array[i]}`);
}
Here, we start by declaring a variable that holds an array of strings named array. We then delete the first element of this array. Finally, we use a simple for loop to loop through the elements of this array and print the value of the array element to the console. The output of this code is as follows:

array[0] = undefined
array[1] = 456
array[2] = 789
As we can see, the array still has three elements, but the first element has been set to undefined, which is the result of deleting this array element.

In TypeScript, we can use the undefined type to explicitly state that a variable could be undefined, as follows:

for (let i = 0; i < array.length; i++) {
    checkAndPrintElement(array[i]);
}
function checkAndPrintElement(arrElement: string | undefined) {
    if (arrElement === undefined)
        console.log(`invalid array element`);
    else
        console.log(`valid array element : ${arrElement}`);
}
Here, we are looping through our array and calling a function named checkAndPrintElement. This function has a single parameter named arrayElement, and is defined as allowing it to be of type string or undefined. Within the function itself, we are checking if the array element is, in fact, undefined, and are logging a warning message to the console. If the parameter is not undefined, we simply log its value to the console. The output of this code is as follows:

invalid array element
valid array element : 456
valid array element : 789
Here, we can see the two different messages being logged to the console.

The undefined type, therefore, allows us to explicitly state when we expect a variable to be undefined. We are essentially telling the compiler that we are aware that a variable may not yet have been defined a value, and we will write our code accordingly.

Null
Along with undefined, JavaScript also allows values to be set to null. Setting a value to null is intended to indicate that the variable is known, but has no value, as opposed to undefined, where the variable has not been defined in the current scope. Consider the following code:

function printValues(a: number | null) {
    console.log(`a = ${a}`);
}
printValues(1);
printValues(null);
Here, we have defined a function named printValues, which has a single parameter named a, which can be of type number or of type null. The function simply logs the value to the console. We then call this function with the values of 1 and null. The output of this code is as follows:

a = 1
a = null
Here, we can see that the console logs match the input values that we called the printValues function with. Again, null is used to indicate that a variable has no value, as opposed to the variable not being defined in the current scope.

The use of null and undefined has been debated for many years, with some arguing that null is not really necessary and that undefined could be used instead. There are others that argue the exact opposite, stating that null should be used in particular cases. Just remember that TypeScript will warn us if it detects that a value could be null, or possibly undefined, which can help to detect unwanted issues with our code.

Conditional expressions
One of the features of newer JavaScript versions that we are able to use in the TypeScript language is a simple, streamlined version of the if then else statement, which uses a question mark ( ? ) symbol to define the if statement and a colon ( : ) to define the then and else path. These are called conditional expressions. The format of a conditional expression is as follows:

(conditional) ? ( true statement )  :  ( false statement );
As an example of this syntax, consider the following code:

const value : number = 10;
const message : string = value > 10 ?
    "value is larger than 10" : "value is 10 or less";
console.log(message);
Here, we start by declaring a variable named value, of type number, that is set to the value of 10. We then create a variable named message, which is of type string, and uses the conditional expression syntax to check whether the value of the value variable is greater than 10. The output of this code is as follows:

value is 10 or less
Here, we can see that the message variable has been set to the string value of "value is 10 or less", because the value > 10 conditional check returned false.

Conditional expressions are a very handy syntax to use in place of the long-winded syntax we would normally have to use in order to code a simple if then else statement.

Conditional expressions can be chained together, so either the truth statement or the false statement, or both, can include another conditional expression.

Optional chaining
When using object properties in JavaScript, and in particular nested properties, it is important to ensure that a nested property exists before attempting to access it. Consider the following JavaScript code:

var objectA = {
    nestedProperty: {
        name: "nestedPropertyName"
    }
}
function printNestedObject(obj) {
    console.log("obj.nestedProperty.name = "
        + obj.nestedProperty.name);
}
printNestedObject(objectA);
Here, we have an object named objectA that has a nested structure. It has a single property named nestedProperty, which holds a child object with a single property called name. We then have a function called printNestedObject that has a single parameter named obj, which will log the value of the obj.nestedProperty.name property to the console. We then invoke the printNestedObject function and pass in objectA as the single argument. The output of this code is as follows:

obj.nestedProperty.name = nestedPropertyName
As expected, the function works correctly. Let's now see what happens if we pass in an object that does not have the nested structure that we were expecting, as follows:

console.log("calling printNestedObject");
printNestedObject({});
console.log("completed");
The output of this code is as follows:

calling printNestedObject
TypeError: Cannot read property 'name' of undefined
    at printNestedObject (javascript_samples.js:28:67)
    at Object.<anonymous> (javascript_samples.js:32:1)
Here, our code has logged the first message to the console, and has then caused a JavaScript runtime error. Note that the final call to log the "completed" message to the console has not even executed, as the entire program crashed while attempting to read the 'name' property on an object that is undefined.

This is obviously a situation to avoid, and it can actually happen quite often. This sort of nested object structure is most often seen when working with JSON data. It is best practice to check that the properties that you are expecting to find are actually there, before attempting to access them. This results in code that's similar to the following:

function printNestedObject(obj: any) {
    if (obj != undefined
        && obj.nestedProperty != undefined
        && obj.nestedProperty.name) {
        console.log(`name = ${obj.nestedProperty.name}`)
    } else {
        console.log(`name not found or undefined`);
    }
}
Here, we have modified our printNestedObject function, which now starts with a long if statement. This if statement first checks whether the obj parameter is defined. If it is, it then checks if the obj.nestedProperty property is defined, and finally if the obj.nestedProperty.name property is defined. If none of these return undefined, the code prints the value to the console. Otherwise, it logs a message to state that it was unable to find the whole nested property.

This type of code is fairly common when working with nested structures, and must be put in place to protect our code from causing runtime errors.

The TypeScript team, however, have been hard at work in driving a proposal in order to include a feature named optional chaining into the ECMAScript standard, which has now been adopted in the ES2020 version of JavaScript. This feature is best described through looking at the following code:

function printNestedOptionalChain(obj: any) {
    if (obj?.nestedProperty?.name) {
        console.log(`name = ${obj.nestedProperty.name}`)
    } else {
        console.log(`name not found or undefined`);
    }
}
Here, we have a function named printNestedOptionalChain that has exactly the same functionality as our previous printNestedObject function. The only difference is that the previous if statement, which consisted of three lines, is now reduced to one line. Note how we are using the ?. syntax in order to access each nested property. This has the effect that if any one of the nested properties returns null or undefined, the entire statement will return undefined.

Let's test this theory by calling this function as follows:

printNestedOptionalChain(undefined);
printNestedOptionalChain({
    aProperty: "another property"
});
printNestedOptionalChain({
    nestedProperty: {
        name: null
    }
});
printNestedOptionalChain({
    nestedProperty: {
        name: "nestedPropertyName"
    }
});
Here, we have called our printNestedOptionalChain function four times. The first call sets the entire obj argument to undefined. The second call has provided a valid obj argument, but it does not have the nestedProperty property that the code is looking for. The third call has the nestedProperty.name property, but it is set to null. Finally, we call the function with a valid object that has the nested structure that we are looking for. The output of this code is as follows:

name not found or undefined
name not found or undefined
name not found or undefined
name = nestedPropertyName
Here, we can see that the optional chaining syntax will return undefined if any of the properties within the property chain is either null or undefined.

Optional chaining has been a much-anticipated feature, and the syntax is a welcome sight for developers who are used to writing long-winded if statements to ensure that code is robust and will not fail unexpectedly.

Nullish coalescing
As we have just seen, it is a good idea to check that a particular variable is not either null or undefined before using it, as this can lead to errors. TypeScript allows us to use a feature of the 2020 JavaScript standard called nullish coalescing, which is a handy shorthand that will provide a default value if a variable is either null or undefined. Consider the following code:

function nullishCheck(a: number | undefined | null) {
    console.log(`a : ${a ?? `undefined or null`}`);
}
nullishCheck(1);
nullishCheck(null);
nullishCheck(undefined);
Here, we have a single function named nullishCheck that accepts a single parameter named a that can be either a number, undefined, or null. This function then logs the value of the a variable to the console, but uses a double question mark ( ?? ), which is the nullish coalescing operator. This syntax provides an alternative value, which is provided on the right hand side of the operator, to use if the variable on the left hand side is either null or undefined. We then call this function three times, with the values 1, null, and undefined. The output of this code is as follows:

a : 1
a : undefined or null
a : undefined or null
Here, we can see that the first call to the nullishCheck function provides the value 1, and this value is printed to the console untouched. The second call to the nullishCheck function provides null as the only argument, and therefore the function will substitute the string undefined or null in place of the value of a. The third call uses undefined, and as we can see, the nullish check will fail over to undefined or null in this case as well.

We can also use a function on the right-hand side of the nullish coalescing operator, or indeed a conditional statement as well, as long as the type of the value returned is correct.

Null or undefined operands
TypeScript will also apply its checks for null or undefined when we use basic operands, such as add ( + ), multiply ( * ), divide ( / ), or subtract ( - ). This can best be seen using a simple example, as follows:

function testNullOperands(a: number, b: number | null | undefined) {
    let addResult = a + b;
}
Here, we have a function named testNullOperands that accepts two parameters. The first, named a, is of type number. The second parameter, named b, can be of type number, null, or undefined. The function creates a variable named addResult, which should hold the result of adding a to b. This code will, however, generate the following error:

error TS2533: Object is possibly 'null' or 'undefined'
This error occurs because we are trying to add two values, and one of them may not be a numeric value. As we have defined the parameter b in this function to be of type number, null, or undefined, the compiler is picking up that we cannot add null to a number, nor can we add undefined to a number, hence the error.

A simple fix to this function may be to use the nullish coalescing operator as follows:

function testNullOperands(a: number, b: number | null | undefined) {
    let addResult = a + (b ?? 0);
}
Here, we are using the nullish coalescing operator to substitute the value of 0 for the value of b if b is either null or undefined.

Definite assignment
Variables in JavaScript are defined by using the var keyword. Unfortunately, the JavaScript runtime is very lenient on where these definitions occur, and will allow a variable to be used before it has been defined. Consider the following JavaScript code:

console.log("aValue = " + aValue);
var aValue = 1;
console.log("aValue = " + aValue);
Here, we start by logging the value of a variable named aValue to the console. Note, however, that we only declare the aValue variable on the second line of this code snippet. The output of this code will be as follows:

aValue = undefined
aValue = 1
As we can see from this output, the value of the aValue variable before it had been declared is undefined. This can obviously lead to unwanted behavior, and any good JavaScript programmer will check that a variable is not undefined before attempting to use it. If we attempt the same thing in TypeScript, as follows:

console.log(`lValue = ${lValue}`);
var lValue = 2;
The compiler will generate the following error:

error TS2454: Variable 'lValue' is used before being assigned
Here, the compiler is letting us know that we have possibly made a logic error by using the value of a variable before we have declared the variable itself.

Let's consider another, more tricky case of where this could happen, where even the compiler can get things wrong, as follows:

var globalString: string;
setGlobalString("this string is set");
console.log(`globalString = ${globalString}`);
function setGlobalString(value: string) {
    globalString = value;
}
Here, we start by declaring a variable named globalString, of type string. We then call a function named setGlobalString that will set the value of the globalString variable to the string provided. Then, we log the value of the globalString variable to the console. Finally, we have the definition of the setGlobalString function that just sets the value of the globalString variable to the parameter named value. This looks like fairly simple, understandable code, but it will generate the following error:

error TS2454: Variable 'globalString' is used before being assigned
According to the compiler, we are attempting to use the value of the globalString variable before it has been given a value. Unfortunately, the compiler does not quite understand that by invoking the setGlobalString function, the globalString variable will actually have been assigned a value before we attempt to log it to the console.

To cater for this scenario, as the code that we have written will work correctly, we can use the definite assignment assertion syntax, which is to append an exclamation mark (!) after the variable name that the compiler is complaining about. There are actually two places to do this.

Firstly, we can modify the code on the line where we use this variable for the first time, as follows:

console.log(`globalString = ${globalString!}`);
Here, we have placed an exclamation mark after the use of the globalString variable, which has now become globalString!. This will tell the compiler that we are overriding its type checking rules, and are willing to let it use the globalString variable, even though it thinks it has not been assigned.

The second place that we can use the definite assignment assertion syntax is in the definition of the variable itself, as follows:

var globalString!: string;
Here, we have used the definite assignment assertion operator on the definition of the variable itself. This will also remove the compilation error.

While we do have the ability to break standard TypeScript rules by using definite assignment operators, the most important question is why? Why do we need to structure our code in this way? Why are we using a global variable in the first place? Why are we using the value of a variable where if we change our logic, it could end up being undefined? It certainly would be better to refactor our code so that we avoid these scenarios.

The only place that the author has found where it makes sense to use definite assignment is when writing unit tests. In a unit test scenario, we may be testing the boundaries of a specific code path, and are purposefully bending the rules of TypeScript in order to write a particular test. All other cases of using definite assignment should really warrant a review of the code to see if it can be structured in a different way.

Object
TypeScript introduces the object type to cover types that are not primitive types. This includes any type that is not number, boolean, string, null, symbol, or undefined. Consider the following code:

let structuredObject: object = {
    name: "myObject",
    properties: {
        id: 1,
        type: "AnObject"
    }
}
function printObjectType(a: object) {
    console.log(`a: ${JSON.stringify(a)}`);
}
Here, we have a variable named structuredObject that is a standard JavaScript object, with a name property, and a nested property named properties. The properties property has an id property and a type property. This is a typical nested structure that we find used within JavaScript, or a structure returned from an API call that returns JSON. Note that we have explicitly typed this structuredObject variable to be of type object.

We then define a function named printObjectType that accepts a single parameter, named a, which is of type object. The function simply logs the value of the a parameter to the console. Note, however, that we are using the JSON.stringify function in order to format the a parameter into a human-readable string. We can then call this function as follows:

printObjectType(structuredObject);
printObjectType("this is a string");
Here, we call the printObjectType function with the structuredObject variable, and then attempt to call the printObjectType function with a simple string. This code will produce an error, as follows:

error TS2345: Argument of type '"this is a string"' is not assignable to parameter of type 'object'.
Here, we can see that because we defined the printObjectType function to only accept a parameter of type object, we cannot use any other type to call this function. This is due to the fact that object is a primitive type, similar to string, number, boolean, null, or undefined, and as such we need to conform to standard TypeScript typing rules.

Unknown
TypeScript introduces a special type into its list of basic types, which is the type unknown. The unknown type can be seen as a type-safe alternative to the type any. A variable marked as unknown can hold any type of value, similar to a variable of type any. The difference between the two, however, is that a variable of type unknown cannot be assigned to a known type without explicit casting.

Let's explore these differences with some code as follows:

let a: any = "test";
let aNumber: number = 2;
aNumber = a;
Here, we have defined a variable named a that is of type any, and set its value to the string "test". We then define a variable named aNumber, of type number, and set its value to 2.

We then assign the value of a, which is the string "test", to the variable aNumber. This is allowed, since we have defined the type of the variable a to be of type any. Even though we have assigned a string to the a variable, TypeScript assumes that we know what we are doing, and therefore will allow us to assign a string to a number.

Let's rewrite this code but use the unknown type instead of the any type, as follows:

let u: unknown = "an unknown";
u = 1;
let aNumber2: number;
aNumber2 = u;
Here, we have defined a variable named u of type unknown, and set its value to the string "an unknown". We then assign the numeric value of 1 to the variable u. This shows that the unknown type mimics the behavior of the any type in that it has relaxed the normal strict type checking rules, and therefore this assignment is allowed.

We then define a variable named aNumber2 of type number and attempt to assign the value of the u variable to it. This will cause the following error:

error TS2322: Type 'unknown' is not assignable to type 'number'
This is a very interesting error, and highlights the differences between the any type and the unknown type. While the any type in effect relaxes all type checking, the unknown type is a primitive type and follows the same rules that are applied to any of the primitive types, such as string, number, or boolean.

This means that we must cast an unknown type to another primitive type before assignment. We can fix the preceding error as follows:

aNumber2 = <number>u;
Here, we have used explicit casting to cast the value of u from type unknown to type number. Because we have explicitly specified that we are converting an unknown type to a number type, the compiler will allow this.

Using the unknown type forces us to make a conscious decision when using these values. In essence, we are letting the compiler know that we know what type this value should be when we actually want to use it. This is why it is seen as a type-safe version of any, as we need to use explicit casting to convert an unknown type into a known type before using it.

Never
The final primitive type in the TypeScript collection is a type of never. This type is used to indicate instances where something should never occur. Even though this may sound confusing, we can often write code where this occurs. Consider the following code:

function alwaysThrows() {
    throw new Error("this will always throw");
    return -1;
}
Here, we have a function named alwaysThrows, which will, according to its logic, always throw an error. Remember that once a function throws an error, it will immediately return, and no other code in the function will execute. This means that the second line of this function, which returns a value of -1, will never execute.

This is where the never type can be used to guard against possible logic errors in our code. Let's change the function definition to return a type of never, as follows:

function alwaysThrows(): never {
    throw new Error("this will always throw");
    return -1;
}
With the addition of the return type of never for this function, the compiler will now generate the following error:

error TS2322: Type '-1' is not assignable to type 'never'
This error message is clearly telling us that the function, which returns a type of never, is attempting to return the value of -1. The compiler, therefore, has identified a flaw in our logic.

Never and switch
A more advanced use of the never type can be used to trap logic errors within switch statements. Consider the following code:

enum AnEnum {
    FIRST,
    SECOND
}
function getEnumValue(enumValue: AnEnum): string {
    switch (enumValue) {
        case AnEnum.FIRST: return "First Case";
    }
    let returnValue: never = enumValue;
    return returnValue;
}
Here, we start with a definition of an enum named AnEnum, which has two values, FIRST and SECOND. We then define a function named getEnumValue, which has a single parameter named enumValue of type AnEnum and returns a string. The logic within this function is pretty simple and is designed to return a string based on the enumValue passed in.

Note, however, that the switch statement only has a case statement for the FIRST value of the enum, but does not have a case statement for the SECOND value of the enum. This code, therefore, will not work correctly if we call the function with AnEnum.SECOND.

This is where the last two lines of this function come in handy. The error message that is generated for this code is as follows:

error TS2322: Type 'AnEnum.SECOND' is not assignable to type 'never'
Let's take a closer look at this code. After our switch statement, we define a variable named returnValue, which is of type never. The trick in this code is that we assign the value of the incoming parameter, enumValue, which is of type AnEnum, to the returnValue variable, which is of type never. This statement is generating the error.

The TypeScript compiler, then, is examining our code, and determining that there is a case statement missing for the AnEnum.SECOND value. In this case, the logic falls through the switch statement, and then attempts to assign the AnEnum.SECOND value to a variable of type never, hence the error.

This code can be easily fixed, as follows:

function getEnumValue(enumValue: AnEnum): string {
    switch (enumValue) {
        case AnEnum.FIRST: return "First Case";
        case AnEnum.SECOND: return "Second Case";
    }
    let returnValue: never = enumValue;
    return returnValue;
}
Here, we have simply added the missing case statement to handle the AnEnum.SECOND value. With this in place, the error is resolved. While this may be fairly easy to spot in a simple example like this, this sort of error is commonplace when working with large code bases. Over time, developers often add values to an enum to get their unit tests to work, but can easily miss these missing case statements. Using the never type here safeguards our code so that we can pick up these errors earlier.

Object spread
When working with basic JavaScript objects, we often need to copy the properties of one object to another, or do some mixing and matching of properties from various objects. In TypeScript, we can use an ES7 technique known as object spread to accomplish this. Consider the following code:

let firstObj: object = { id: 1, name: "firstObj" };
let secondObj: object = { ...firstObj };
console.log(`secondObj : ${JSON.stringify(secondObj)}`);
Here, we have defined a variable named firstObj that is of type object and has an id property and a name property. We then define a variable named secondObj and use the object spread syntax of three dots ( ... ) to assign a value to it. The value we are assigning is an object that is made up of the firstObj variable, that is { ...firstObj }. The output of this code is as follows:

secondObj : {"id":1,"name":"firstObj"}
Here, we can see that the id and name properties and values have been copied into the new secondObj variable.

We can also use this technique to combine multiple objects together. Consider the following code:

let nameObj: object = { name: "nameObj name" };
let idObj: object = { id: 1 };
let obj3 = { ...nameObj, ...idObj };
console.log(`obj3 = ${JSON.stringify(obj3)}`);
Here, we have define a variable named nameObj that has a single property called name. We then have a variable named idObj that has a single property named id. Note how we are using the spread syntax to create a variable named obj3 that is the result of combining the properties of nameObj and the properties of the idObj variables. The output of this code is as follows:

obj3 = {"name":"nameObj name","id":1}
This output shows us that the properties of both objects have been merged into the obj3 variable, using the object spread syntax.

Spread precedence
When using object spread, properties will be copied incrementally. In other words, if two objects have a property with the same name, then the object that was specified last will take precedence. As an example of this, consider the following:

let objPrec1: object = { id: 1, name: "obj1 name" };
let objPrec2: object = { id: 1001, desc: "obj2 description" };
let objPrec3 = { ...objPrec1, ...objPrec2 };
console.log(`objPrec3 : ${JSON.stringify(objPrec3, null, 4)}`);
Here, we have defined two variables named objPrec1 and objPrec2. Both of these objects have an id property; however, objPrec1 has a name property, and objPrec2 has a desc property. We then create a variable named objPrec3 that is a combination of these two objects. Finally, we print the value of the objPrec3 object to the console. The output of this code is as follows:

objPrec3 : {
    "id": 1001,
    "name": "obj1 name",
    "desc": "obj2 description"
}
Here, we can see that the spread operator has combined the properties of both original objects into the objPrec3 variable. This new object has all three properties, id, name, and desc. Note that the id property was common between both original objects, and that the value of 1001 has taken precedence in this case, as it has been taken from the object that was specified last.

Spread with arrays
Interestingly, the spread syntax can also be used with arrays. Consider the following code:

let firstArray = [1, 2, 3];
let secondArray = [3, 4, 5];
let thirdArray = [...firstArray, ...secondArray];
console.log(`third array = ${thirdArray}`);
Here, we have defined two arrays, named firstArray and secondArray. We then use the spread syntax to combine these two arrays into another variable named thirdArray. We then print the value of the thirdArray variable to the console. The output of this code is as follows:

third array = 1,2,3,3,4,5
Here, we can see that the contents of the two arrays have been combined into the thirdArray variable. Interestingly, the new array contains the value 3 twice, as it was present in both arrays. Note that this syntax can be used on arrays of any type.

The spread syntax can also appear in any order. Consider the following code:

let objArray1 = [
    { id: 1, name: "first element" },
]
let objArray2 = [
    { id: 2, name: "second element" }
]
let objArray3 = [
    ...objArray1,
    { id: 3, name: "third element" },
    ...objArray2
]
console.log(`objArray3 = ${JSON.stringify(objArray3, null, 4)}`);
Here, we have defined two arrays named objArray1 and objArray2, each with a single array element, that has both an id property and a name property. We then create a third variable named objArray3, which uses object spread to create a third array. Note that we are building the objArray3 array out of the objArray1 array, then adding an element, and then including the contents of the ojbArray2 array. The output of this code is as follows:

objArray3 = [
    {
        "id": 1,
        "name": "first element"
    },
    {
        "id": 3,
        "name": "third element"
    },
    {
        "id": 2,
        "name": "second element"
    }
]
Here, we can see that the objArray3 variable contains all of the elements of both the objArray1 and objArray2 arrays, as well as the element with id : 3 , and name : "third element" that we injected into the middle of the array using spread syntax.

Tuples
Tuples are a method of defining a type that has a finite number of unnamed properties, with each property having an associated type. When using a tuple, all of the properties must be provided. This can best be explained in an example, as follows:

let tuple1: [string, boolean];
tuple1 = ["test", true];
tuple1 = ["test"];
Here, we have defined a variable named tuple1, whose type is defined as an array of types. The first type is a string, and the second type is a boolean. We then assign a value to the tuple1 variable that contains an array with two values, the first of type string and the second of type boolean.

Note that the last line of this code attempts to assign a value to the tuple1 variable that does not have all of the properties that are required. This last line will generate an error as follows:

error TS2741: Property '1' is missing in type '[string]' but required in type '[string, boolean]'
What this error is telling us is that the number and types defined in a tuple must be provided when we assign anything to a tuple.

Tuple destructuring
As tuples use the array syntax, they can be destructured or disassembled in two ways. The first way of destructuring a tuple uses the simple array syntax, as follows:

console.log(`tuple1[0] : ${tuple1[0]}`);
console.log(`tuple1[1] : ${tuple1[1]}`);
Here, we are logging the values of the tuple1 variable to the console by referencing its index within the array, that is, tuple1[0] and tuple1[1]. The output of this code is as follows:

tuple1[0] : test
tuple1[1] : true
Here, we can see that we can access each of the values in the tuple by using the array destructuring syntax. Note that the compiler knows that there are only two elements of this array, and if we attempt to access the third value within this tuple, that is, tuple1[2], the compiler will generate an error.

Another way of destructuring a tuple is to use the array syntax to create an array of named elements and then assign the value of the tuple to this variable, as follows:

let [tupleString, tupleBoolean] = tuple1;
console.log(`tupleString = ${tupleString}`);
console.log(`tupleBoolean = ${tupleBoolean}`);
Here, we have used the array syntax to create a tuple out of two variable names, that is, tupleString and tupleBoolean. We then assign the value of our original tuple, that is, tuple1, to this array of named variables. We can then use these named variables instead of needing to access them using the standard array syntax, that is, tuple1[0]. The output of this code is as follows:

tupleString = test
tupleBoolean = true
Here, we can see that the tuple has been correctly destructured into our two named variables, tupleString and tupleBoolean.

Using the named variable syntax to destructure tuples is a better way of constructing your code, as you can name the variable according to how it will be used. We will see some practical examples of using tuples in Chapter 9, Using Observables to Transform Data, where we use the RxJS library to initiate multiple API calls to retrieve JSON data.

Optional tuple elements
Note that tuple elements can be marked optional by using the question mark (?) after the type, as follows:

let tupleOptional: [string, boolean?];
tupleOptional = ["test", true];
tupleOptional = ["test"];
console.log(`tupleOptional[0] : ${tupleOptional[0]}`);
console.log(`tupleOptional[1] : ${tupleOptional[1]}`);
Here, we have defined a tuple named tupleOptional that consists of two elements, a string, and an optional boolean value. We then assign the value of ["test", true] to this tuple, and then we assign just the value ["test"] to this tuple. As the second element has been marked as optional, we do not need to specify it. We then log the values of the tuple elements to the console, using array syntax. The output of this code is as follows:

tupleOptional[0] : test
tupleOptional[1] : undefined
Here, we can see that the tuple value at index 0 has been set to the value of "test", but that the tuple value at index 1 is undefined as it was not specified in our last assignment statement.

Tuples and spread syntax
We are also able to use spread syntax to define a tuple that can have a variable number of elements. Consider the following code:

let tupleRest: [number, ...string[]];
tupleRest = [1];
tupleRest = [1, "string1"];
tupleRest = [1, "string1", "string2"];
Here, we are using spread syntax to indicate that the variable named tupleRest has a number element, followed by a variable number of string elements. We then assign values to this tuple, starting with a single numerical value, and then a numerical value and a variable number of string values. All of these assignments are valid.

Object destructuring
In a similar way to tuples, standard objects can be also be destructured. Consider the following example:

let complexObject = {
    aNum: 1,
    bStr: "name",
    cBool: true
}
let { aNum, bStr, cBool } = complexObject;
Here, we have defined an object named complexObject that has three properties, aNum, bStr, and cBool. Each of these properties has been assigned a value. We then destructure this object into three separate variables, named aNum, bStr, and cBool, in a similar manner to how we destructured tuples. We can now use these variables as follows:

console.log(`aNum : ${aNum}`);
console.log(`bStr : ${bStr}`);
console.log(`cBool : ${cBool}`);
Here, we are using the aNum, bStr, and cBool variables that we created when destructuring the complexObject object. The output of this code is as follows:

aNum : 1
objId : 1
objName : name
As we can see from this output, we are able to destructure simple objects into a series of variables, which allows us to access the value of these properties through our standard variable naming syntax.

Note that we are also able to rename the variable names during the destructuring step as follows:

let { aNum: objId, bStr: objName, cBool: isValid } 
    = complexObject;
console.log(`objId : ${objId}`);
console.log(`objName : ${objName}`);
console.log(`isValid : ${isValid}`);
Here, we are destructuring the complexObject into a series of variables. Note the use of the colon (:) in this example. We are using the colon to rename the aNum property into the objId variable, using the syntax aNum: objId. Similarly, the bStr property is renamed to a variable named objName, and the cBool property is renamed to a variable named isValid. The colon (:) symbol as used here is not specifying a type as it normally would, but instead is used to rename the variable name used in destructuring.

Functions
In this section of the chapter, we will take a look at functions and their definitions, and how the TypeScript language can be used to introduce further type safety whenever functions are used. Functions can use many of the concepts that we have already discussed, including optional parameters and spread syntax. We will also discuss how we can define a function signature in such a manner that if a function defines another function as a parameter, we can make sure that the function we pass in has the correct parameters. Finally, we will take a look at how to define function overrides.

Optional parameters
Similar to how we have seen tuples using optional elements, we can specify that a function can have optional elements in the same way, using the question mark (?). Consider the following code:

`function concatValues(a: string, b?: string) {
    console.log(`a + b = ${a + b}`);
}`




Default parameters
A variant of the optional parameter syntax allows us to specify a default value for a parameter, if it has not been supplied. Consider the following code:

`function concatWithDefault(a: string, b: string = "default") {
    console.log(`a + b = ${a + b}`);
}`

function testArguments() {
    for (var i = 0; i < arguments.length; i++) {
        console.log("argument[" + i + "] = " + arguments[i]);
    }
}
testArguments(1, 2);
testArguments("first", "second", "third");

In order to express the equivalent function definition in TypeScript, we will need to use rest syntax, as follows:

function testArguments(...args: string[] | number[]) {
    for (let i in args) {
        console.log(`args[${i}] = ${args[i]}`);
    }
}


Function callbacks
One of the most powerful features of JavaScript, and in fact the technology that NodeJS was built on, is the concept of callback functions. A callback function is a function that is passed in as an argument to another function, and is then generally invoked within the original function. In other words, we are calling a function and telling it to go and do what it needs to do, and when it is finished, to call the function that we have supplied.


Function signatures as parameters

function myCallback(text: string): void {
    console.log(`myCallback called with ${text}`);
}
function withCallbackArg(
    message: string,
    callbackFn: (text: string) => void
) {
    console.log(`withCallback called, message : ${message}`);
    callbackFn(`${message} from withCallback"`);
}

Function overrides
TypeScript provides an alternative to union types when defining a function and allows a function signature to provide different parameter types. Consider the following code:

function add(a: string, b: string): string;
function add(a: number, b: number): number;
function add(a: any, b: any) {
    return a + b;
}



Literals
TypeScript also allows us to use what are known as literals, which are almost a hybrid of enums and type aliases. A literal will limit the allowed values to a set of values specified. A literal can be made of string, number, or boolean values. Consider the following code:

`type AllowedStringValues = "one" | "two" | "three";
type AllowedNumericValues = 1 | 20 | 65535;
function withLiteral(input: 
    AllowedStringValues | AllowedNumericValues) {
    console.log(`called with : ${input}`);
}`
Here, we have defined a literal named AllowedStringValues, as well as a literal named AllowedNumericValues. The syntax used for literals is very similar to the syntax of a type alias, where we use the type keyword followed by a set of allowed values. Unlike type aliases, however, we are not specifying a set of different types. We are specifying a set of allowed values, which is similar in concept to an enum.


`withLiteral("one")
withLiteral("two");
withLiteral("three");
withLiteral(65535);
withLiteral("four");
withLiteral(2);`


## Interfaces, Classes, Inheritance, and Modules

This interface describes an object that has an id property of type number, and a name property of type string. Once we have defined an interface, we can use it in the same way as a primitive type, as follows:

`let idObject: IIdNameObject = {
    id: 2
}`

implementing interface as above

Optional properties
Interface definitions may also include optional properties, in a similar way that functions may specify optional parameters, using the question mark (?) syntax. Consider the following interface:

interface IOptional {
    id: number;
    name?: string;
}

Here, we have an interface named IOptional, which has defined an id property of type number, and an optional property named name of type string. We can now define objects as follows:

`let optionalId: IOptional = {
    id: 1
}
let optionalIdName: IOptional = {
    id: 2,
    name: "optional name"
}`

Interfaces do not generate any JavaScript code. This means that interfaces are a construct only used in the TypeScript compilation step and language services, and are there to ensure type safety

Interface naming
The TypeScript team have a coding standard for contributions to the TypeScript code base that prohibits the use of the letter I for prefixing interfaces. In the code samples that we have seen thus far, we have used the interface names IIdName and IOptional, which, according to the TypeScript teams standard, should just have been named IdName and Optional.

Weak types
When we define an interface where all of its properties are optional, this is considered to be a weak type. In other words, we have defined an interface, but none of the properties of the interface are mandatory. Let's see what happens if we create a weak type, and then try to bend the standard type rules, as follows:

`interface IWeakType {
    id?: number,
    name?: string
}
let weakTypeNoOverlap: IWeakType = {
    description: "a description"
} //error `


The in operator // js syntax

function printNameOrValue(
    obj: IIdName | IDescrValue): void {
    if ('id' in obj) {
        console.log(`obj.name : ${obj.name}`);
    }
    if ('descr' in obj) {
        console.log(`obj.value : ${obj.value}`);
    }
}

keyof //ts prop
TypeScript allows us to iterate through the properties of a type and extract the names of its properties through the keyof keyword, which we can use as a string literal type. Let's explore this concept and how it applies to interfaces, as follows:

interface IPerson {
    id: number;
    name: string;
}
type PersonPropertyName = keyof IPerson;

result is type PersonPropertyLiteral = "id" | "name";

Classes
A class is the definition of an object, what data it holds, and what operations it can perform. Classes and interfaces form the cornerstone of object-oriented programming. Let's take a look at a simple class definition, as follows:

The this keyword
As we have seen, a class definition specifies both the properties of a class, and the functions that it implements. Within the class, if we need to access a property of the class instance, we need to use the this keyword, as follows:

Implementing interfaces
`interface IPrint {
    print(): void;
}
function printClass(a: IPrint) {
    a.print();
}`

`class ClassA implements IPrint {
    print(): void {
        console.log(`ClassA.print() called.`)
    };
}
class ClassB implements IPrint {
    print(): void {
        console.log(`ClassB.print() called.`)
    };
}`


Class constructors
Class constructors can accept arguments during their initial construction. This allows us to combine the creation of a class and the setting of its parameters into a single line of code. Consider the following class definition:

`class ClassWithConstructor {
    id: number;
    constructor(_id: number) {
        this.id = _id;
    }
}`

Class modifiers
TypeScript introduces the public and private access modifiers to indicate whether a class variable or function can be accessed from outside the class itself. Additionally, we can also use the protected access modifier, which we will discuss a little later.

Class functions and properties are public by default. The use of class access modifiers is a tool that we can use when writing TypeScript code and helps to protect variables from accidental assignment. These access modifiers, however, will not appear in the JavaScript that is generated from our code. The compiler will, in fact, remove any of these constraints when generating JavaScript.


JavaScript private fields
An experimental proposal to the ECMAScript standard introduces the concept of a private field, by using the hash ( # ) symbol before a property name. This means that if we are targeting a runtime that supports it, such as Node v12, we can write a JavaScript class as follows:

`class ClassES6Private {
    #id: number;
    constructor(id: number) {
        this.#id = id;
    }
}`


let es6PrivateClass = new ClassES6Private(10);
es6PrivateClass.#id = 20;


Constructor parameter properties
TypeScript also introduces a shorthand version for access modifiers that can be applied to parameters in a constructor function. As an example of this, consider the following code:

`class ClassWithCtorMods {
    constructor(public id: number, private name: string) {
    }
}
let myClassMod = new ClassWithCtorMods(1, "test");
console.log(`myClassMod.id = ${myClassMod.id}`);
console.log(`myClassMod.name = ${myClassMod.name}`);  //error`

Readonly
In addition to the public and private access modifiers, we can also mark a class property as readonly. This is similar to the concept of the const keyword, and means that once a value has been assigned to a readonly property, it is not allowed to be modified, as follows:

class ClassWithReadonly {
    readonly name: string;
    constructor(_name: string) {
        this.name = _name;
    }
    setNameValue(_name: string) {
        this.name = _name;
    }
}

Get and set // js feature
ECMAScript 5 introduced the concept of property accessors, or get and set functions. A property accessor is simply a function that is called when a user of our class gets the value of a property, or sets its value.

By using a function instead of a simple property, we can detect when someone modifies or accesses a property, which we can use to trigger other logic. Consider the following example:
`class ClassWithAccessors {
    private _id: number = 0;
    get id(): number {
        console.log(`get id property`);
        return this._id;
    }
    set id(value: number) {
        console.log(`set id property`);
        this._id = value;
    }
}`

Static functions
A class can mark a function with the static keyword, meaning that there will only be a single instance of this function available throughout the code base. When using a static function, we do not need to create an instance of the class in order to invoke this function, as follows:

`class StaticFunction {
    static printTwo() {
        console.log(`2`)
    }
}
StaticFunction.printTwo();`

Static properties
In a similar manner to static functions, classes can also have static properties. If a class property has been marked as static, then there will only be a single instance of this property throughout the code base. Consider the following code:

 `class StaticProperty {
    static count = 0;
    updateCount() {
        StaticProperty.count++;
    }
}`



Namespaces
When working within large projects, and particularly when working with large numbers of external libraries, there may come a time when two classes or interfaces share the same name. TypeScript uses what are known as namespaces to cater for these situations, as follows:

`namespace FirstNameSpace {
    export class NameSpaceClass {} //only this is exported
    class NotExported {}
}`

Iheritance :-

`interface IBase {
    id: number;
}
interface IDerivedFromBase extends IBase {
    name: string;
}
class IdNameClass implements IDerivedFromBase {
    name: string = "nameString";
}`

JavaScript does not support the concept of multiple inheritance when it comes to classes. This means that a class can only inherit from one other class. Interfaces, however, do support multiple inheritance, as we have seen earlier.

`interface IFirstInterface {
    id: number;
}
interface ISecondInterface {
    name: string;
}
class MultipleInterfaces implements
    IFirstInterface,
    ISecondInterface
{
    id: number = 0;
    name: string = "nameString";
}`


3
Interfaces, Classes, Inheritance, and Modules
We have already seen a variety of language enhancements that TypeScript brings to modern JavaScript development. This includes the primitive types, like string, number, boolean, undefined, and never, as well as features brought in from multiple ECMAScript standards, like let, const, and optional chaining. TypeScript, therefore, allows us to use these enhanced language features from future JavaScript standards in our code right now, and it takes care of generating the correct JavaScript based on our runtime target.

The ECMAScript standard published in 2015, known as ES6, introduced the concept of classes and inheritance. JavaScript programmers, however, have been able to create classes and use object-oriented programming techniques for many years, by using what is known as the closure design pattern and the prototype design pattern. The creation of JavaScript objects through closures, however, has been more by convention than being baked directly into the language.

TypeScript has supported the object-oriented concepts of interfaces, classes, and inheritance since its earliest versions. Remember that it generates JavaScript, and as such, is capable of converting the classes that you construct today into older style JavaScript closures, if we are targeting older versions of the JavaScript runtime. This means that no matter what JavaScript runtime you are targeting, the TypeScript compiler will take care of generating the correct JavaScript.

In this chapter, we will discuss all things object-oriented, as follows:

Interfaces
Classes
Inheritance
Modules
Interfaces
In Chapter 1, Up and Running Quickly, we discussed how TypeScript uses duck typing to assess if two objects are compatible. These typing rules govern whether an object can be assigned to another and compares the properties of one object to the other.

Interfaces provide us with a mechanism to define what properties an object must implement and is, therefore, a way for us to define a custom type. By defining an interface, we are describing the properties and functions that an object is expected to have in order to be used by our code.

To illustrate these concepts, consider the following code:

interface IIdName {
    id: number;
    name: string;
}
Here, we have used the interface keyword to define a TypeScript interface named IIdName. This interface describes an object that has an id property of type number, and a name property of type string. Once we have defined an interface, we can use it in the same way as a primitive type, as follows:

let idObject: IIdNameObject = {
    id: 2
}
Here, we have created a variable named idObject, and specified that its type is the interface IIdName. We have, however, only specified a single property named id, and have not specified the name property, which therefore means that our object does not match the properties we are expecting according to the interface definition. This code will generate the following error:

error TS2741: Property 'name' is missing in type '{ id: number; }' but required in type 'IIdName'
Here, we can see that the compiler is treating our interface definition just like it would treat a standard type. We are stating that the object idObject implements the IIdNameObject interface, but have not provided the name property that is required, hence the error.

To remove this error, we need to define both properties on our object, as required by the interface, as follows:

let idObject: IIdName = {
    id: 2,
    name : "this is a name"
}
Here, our object idObject provides both the id and the name properties correctly.

TypeScript will treat interfaces in the same way as it treats primitive types, and it will use duck typing to ensure that when we say that an object matches an interface, then it really does match the interface, with no property left behind.

Optional properties
Interface definitions may also include optional properties, in a similar way that functions may specify optional parameters, using the question mark (?) syntax. Consider the following interface:

interface IOptional {
    id: number;
    name?: string;
}
Here, we have an interface named IOptional, which has defined an id property of type number, and an optional property named name of type string. We can now define objects as follows:

let optionalId: IOptional = {
    id: 1
}
let optionalIdName: IOptional = {
    id: 2,
    name: "optional name"
}
Here, we have two objects named optionalId and optionalIdName that both implement the IOptional interface. As the name property has been marked optional, both of these objects correctly implement the interface.

Interfaces are compiled away
Interfaces do not generate any JavaScript code. This means that interfaces are a construct only used in the TypeScript compilation step and language services, and are there to ensure type safety. The JavaScript that is generated for our code thus far is as follows:

var idObject = {
    id: 2,
    name: "this is a name"
};
var optionalId = {
    id: 1
};
var optionalIdName = {
    id: 2,
    name: "optional name"
};
Here, we can see that the interface definitions that we have been using have all been removed during the compilation step, and all we are left with in this generated JavaScript are the objects themselves.

Interface naming
The TypeScript team have a coding standard for contributions to the TypeScript code base that prohibits the use of the letter I for prefixing interfaces. In the code samples that we have seen thus far, we have used the interface names IIdName and IOptional, which, according to the TypeScript teams standard, should just have been named IdName and Optional.

The reason for this standard boils down to two things. Firstly, an interface defines the shape of an object, and is therefore really just a type, in the same manner as a string is a type or a number is a type. When comparing types, the TypeScript compiler will use duck typing to check whether the shape of one object is compatible with another, so therefore there is no distinction between an interface and a class.

Secondly, the TypeScript language does not generate any code related to interfaces, so we cannot interrogate an interface at runtime, and ask questions such as "what properties does this interface define?". Other languages, such as C#, use a technique called reflection, which allows code to query an interface, and gather information on the available properties, and their types at runtime.

So an interface is just a name for a type, in the same way that a type alias is a name for a type. We do not, however, prefix type aliases with the letter A, or classes with the letter C, so why should we prefix interface names with the letter I ?

There are, however, some reasons why using a prefix with the letter I does make sense. If you or your team are migrating from languages like C# or Java, then this naming convention will seem familiar, and natural. It also helps when reading code outside of an IDE such as VSCode, which has access to the TypeScript language service, and can give you hints as to when an interface is used. Reading code in a code review tool, for example, does not have this contextual help, and can therefore lead to confusion around whether a type is an interface or something else.

For the purpose of this chapter, we will continue to distinguish between interfaces and other types by using an I prefix for interfaces, where it helps within the code samples. This serves to make it explicit when we are using an interface as opposed to a class or any other type. The rule that the TypeScript team has adopted is a rule for their particular development team, and you should adopt it if it makes sense within your code base, or within your team itself. Once you have decided on a particular naming convention, then stick with it, as there are pros and cons to either naming standard.

Weak types
When we define an interface where all of its properties are optional, this is considered to be a weak type. In other words, we have defined an interface, but none of the properties of the interface are mandatory. Let's see what happens if we create a weak type, and then try to bend the standard type rules, as follows:

interface IWeakType {
    id?: number,
    name?: string
}
let weakTypeNoOverlap: IWeakType = {
    description: "a description"
}
Here, we have defined an interface name IWeakType, which has an id property of type number, and a name property of type string. Both of these properties have been marked as optional. We then create a variable named weakTypeNoOverlap, which implements the IWeakType interface, and has a single property named description. This code generates the following error:

error TS2322: Type '{ description: string; }' is not assignable to type 'IWeakType'.
  Object literal may only specify known properties, and 'description' does not exist in type 'IWeakType'
Here, we can see that the compiler is detecting that the weakTypeNoOverlap object has not implemented the IWeakType interface, as it does not have either an id or a name property. We can see, therefore, that TypeScript will strongly type even weak types.

Note that while we are able to create weak types in TypeScript, they are really just an edge case in terms of usage. We should really be thinking differently about our interface definitions, if all properties become optional, and we are introducing a weak type.

The in operator
JavaScript allows us to interrogate an object and see if it has a property using the in operator. Let's explore this operator with the following interfaces:

interface IIdName {
    id: number;
    name: string;
}
interface IDescrValue {
    descr: string;
    value: number;
}
Here, we have two interfaces. The first is named IIdName, and contains an id property of type number, and a name property of type string. The second interface is named IDescrValue, and contains a descr property of type string, and a value property of type number. Note that these interfaces describe completely different objects, and have no overlapping properties whatsoever. We can now write a function that will distinguish between these two interfaces using the in operator as follows:

function printNameOrValue(
    obj: IIdName | IDescrValue): void {
    if ('id' in obj) {
        console.log(`obj.name : ${obj.name}`);
    }
    if ('descr' in obj) {
        console.log(`obj.value : ${obj.value}`);
    }
}
Here, we have a function named printNameOrValue that has a single parameter named obj, which can either be of the type IIdName, or of the type IDescrValue. Note how we are then using an if statement to create a type guard that checks for the property id using the in operator. In other words, if the object has a property named id, then enter the if block. Within this if block, the object will be treated as implementing the IIdName interface, and this code block is acting as a type guard. We then log the value of the obj.name property, which is also part of the IIdName interface, to the console.

The second if statement in this function is again using the in operator, but this time using the descr property to detect if the object implements the IDescrValue interface. If it does implement this interface, we then log the value of the obj.value property, which is part of the IDescrValue interface, to the console.

We can now use this function as follows:

printNameOrValue({
    id: 1,
    name: "nameValue"
});
printNameOrValue({
    descr: "description",
    value: 2
});
Here, we are calling the printNameOrValue function with two different objects. The structure of the first object conforms to the IIdName interface, and the structure of the second objects conforms to the IDescrValue interface. The compiler will let us know if we call this function with anything that does not match either of these interfaces. The output of this code is as follows:

obj.name : nameValue
obj.value : 2
Here, we can see the function printNameOrValue is detecting the properties of each of these objects using the in operator, and entering the type guard code block depending on what properties it finds. Note that if an object implements both interfaces, or has properties that match both of these interfaces, then both type guards will be executed, as we have two if statements, and not an if else statement.

keyof
TypeScript allows us to iterate through the properties of a type and extract the names of its properties through the keyof keyword, which we can use as a string literal type. Let's explore this concept and how it applies to interfaces, as follows:

interface IPerson {
    id: number;
    name: string;
}
type PersonPropertyName = keyof IPerson;
Here, we have defined an interface named IPerson that defines two properties named id and name. We are then creating a string literal type for the valid properties of this interface named PersonPropertyName. Note that here, we are simply using the keyof keyword to generate a string literal type for the properties found in the IPerson interface. This is equivalent to the following string literal:

type PersonPropertyLiteral = "id" | "name";
We can now use this type as follows:

function getProperty(key: PersonPropertyName, value: IPerson) {
    console.log(`${key} = ${value[key]}`);
}
getProperty("id",
    { id: 1, name: "firstName" }
);
getProperty("name",
    { id: 2, name: "secondName" }
);
getProperty("telephone",
    { id: 3, name: "thirdName" }
);
Here, we have defined a function named getProperty that has two parameters, named key of type PersonPropertyName, and value of type IPerson. This function is using the string literal PersonPropertyName that was constructed using the keyof keyword. The function itself simply logs the name of the property key provided, and the value of the corresponding property, to the console. We are then invoking the function three times.

The first call to the getProperty function will output the value of the "id" property, and the second call to the getProperty function will output the value of the "name" property. The third call, however, will generate the following error:

error TS2345: Argument of type '"telephone"' is not assignable to parameter of type '"id" | "name"'.'
Here, we can see that the compiler is correctly identifying that we are not allowed to call this function with the first argument of "telephone", as this argument is not part of our string literal type.

Using the keyof keyword will generate a string literal that automatically includes all of the properties of an interface. This technique is obviously preferable to having to maintain string literals manually.

In this first section of the chapter, we have explored interfaces, and seen that they behave just like other types in TypeScript. We can use them to define custom types, and bring structure to nested objects. We know that they are a language construct only, as the TypeScript compiler will "compile away" any of our interfaces. The use of interfaces, however, becomes very powerful when used with other object-oriented programming concepts, such as classes, which we will discuss next.

Classes
A class is the definition of an object, what data it holds, and what operations it can perform. Classes and interfaces form the cornerstone of object-oriented programming. Let's take a look at a simple class definition, as follows:

class SimpleClass {
    id: number;
    print(): void {
        console.log(`SimpleClass.print() called.`);
    }
}
Here, we have defined a class, using the class keyword, which is named SimpleClass, and has an id property of type number, and a print function, which just logs a message to the console. Notice anything wrong with this code? Well, the compiler will generate an error message as follows:

error TS2564: Property 'id' has no initializer and is not definitely assigned in the constructor
What this error is indicating is that if we create an instance of this class, then the newly created class will not have the id property initialized, and it will therefore be undefined. If our code is expecting the id property to have a value, then we might be surprised when it returns undefined, and the compiler is warning us of this potential error. There are two ways to fix this compiler error. We could set it to a default value such as 0, or we could simply make the id property a type union, as follows:

id: number | undefined;
Here, we specified that the id property could be a number, or it could be undefined. We are therefore making a conscious decision within our code that we are prepared for this value to be undefined.

In order to use our SimpleClass class definition, we will need to create an instance of this class as follows:

let mySimpleClass = new SimpleClass();
mySimpleClass.print();
Here, we have defined a variable named mySimpleClass, and set it to a new instance of the SimpleClass class by using the new keyword. Once the instance of this class has been created, we call the print function. The output of this code is as follows:

SimpleClass.print() called.
The this keyword
As we have seen, a class definition specifies both the properties of a class, and the functions that it implements. Within the class, if we need to access a property of the class instance, we need to use the this keyword, as follows:

class SimpleClass {
    id: number | undefined;
    print(): void {
        console.log(`SimpleClass.id = ${this.id}`);
    }
}
Here, we have modified the print function to print the value of the id property to the console, within the template string, ${this.id}. Note how we need to prefix the id property with the keyword this in order to access it within a class. We can now test this code as follows:

let mySimpleClass = new SimpleClass();
mySimpleClass.id = 2020;
mySimpleClass.print();
Here, we have modified our earlier code sample, and assigned the value of 2020 to the id property of the variable mySimpleClass. We then call the print function of this class, which will give us the following output:

SimpleClass.id = 2020
Here, the print function is accessing the value of the internal class property named id, and correctly printing the value of 2020 to the console.

Implementing interfaces
There is a very strong relationship between classes and interfaces, particularly in object-oriented design patterns. An interface describes a custom type and can include both properties and functions. A class is the definition of an object, also including its properties and functions. This allows us to use interfaces to describe some common behavior within a set of classes, and write code that will work with this set of classes. As an example of this, consider the following class definitions:

class ClassA {
    print(): void {
        console.log(`ClassA.print() called.`)
    };
}
class ClassB {
    print(): void {
        console.log(`ClassB.print() called.`)
    };
}
Here, we have class definitions for two classes, named ClassA and ClassB. Both of these classes have a print function. Now suppose that we want to write some code that did not really care what type of class we used, all it cared about was whether the class implemented a print function. We can easily create an interface describing the behavior we need, as follows:

interface IPrint {
    print(): void;
}
function printClass(a: IPrint) {
    a.print();
}
Here we have defined an interface named IPrint that contains a single function named print and returns void. We then have a function named printClass that takes a single parameter named a, and is of type IPrint. We are using the interface IPrint in this function definition to describe the attributes of an object that can be passed in as a parameter. We can now update our class definitions, and mark them as being usable by the printClass function, as follows:

class ClassA implements IPrint {
    print(): void {
        console.log(`ClassA.print() called.`)
    };
}
class ClassB implements IPrint {
    print(): void {
        console.log(`ClassB.print() called.`)
    };
}
Here, we are using the TypeScript keyword implements to state that both ClassA and ClassB implement the IPrint interface, and are therefore usable by our printClass function. We can now use this function as follows:

let classA = new ClassA();
let classB = new ClassB();
printClass(classA);
printClass(classB);
Here, we have created an instance of each of our classes, and assigned them to the variables classA and classB. We then pass these variables into our printClass function as arguments. The output of this code is as follows:

ClassA.print() called.
ClassB.print() called.
Interfaces, therefore, can be seen as a type of contract that classes must implement, if they are expected to provide certain properties and certain behaviors.

Note that TypeScript's duck typing rules will ensure that a particular class has the correct shape when used, even if it does not implement the interface as described. As an example of this, consider the following code:

class ClassC {
    print(): void {
        console.log(`ClassC.print() called.`)
    };
}
let classC = new ClassC();
printClass(classC);
Here, we have defined a class named ClassC that has the print function that is required by the IPrint interface, but it does not explicitly state that it implements the IPrint interface. Note how we are missing the code implements IPrint. We are still able to use the instance of this class, named classC, however, in a call to the printClass function, on the last line of this snippet. This is a further example of TypeScript's duck typing rules, making sure that the shape of the type used is correct for a call to the printClass function. Defining interfaces, and using them in our code, however, ensures that when changes are made to class definitions, or interface definitions, we are able to trap any possible errors early.

Class constructors
Class constructors can accept arguments during their initial construction. This allows us to combine the creation of a class and the setting of its parameters into a single line of code. Consider the following class definition:

class ClassWithConstructor {
    id: number;
    constructor(_id: number) {
        this.id = _id;
    }
}
Here, we have defined a class named ClassWithConstructor that has a single property named id of type number. We then have a function definition for a function named constructor, with a single parameter named _id of type number. Within this constructor function, we are setting the value of the internal id property to the value of the _id parameter that was passed in.

Note the definition of the id property in this class. Previously, we needed to define a property as being of the type number | undefined. Here, however, because we are initializing the property via the constructor, it will always be defined when an instance of the class is initialized.

We can construct an instance of this class as follows:

let classWithConstructor = new ClassWithConstructor(10);
console.log(`classWithConstructor = 
    ${JSON.stringify(classWithConstructor)}`);
Here, we have created an instance of the ClassWithConstructor class, and passed in the argument of 10 to the constructor. We then simply log the value of this class instance to the console. The output of this code is as follows:

classWithConstructor = {"id":10}
Another aspect to note about class constructors, is that TypeScript understands the scoping rules of class properties, and the scoping rules of parameters. Our earlier class definition can be rewritten slightly as follows:

class ClassWithConstructor {
    id: number;
    constructor(id: number) {
        this.id = id;
    }
}
Here, we have the same class definition as used earlier, with a subtle difference. Note how the constructor function now accepts a parameter named id, instead of _id, as we used earlier. This is possible, as the scope of the id parameter, as passed into the constructor function, is different to scope of the class instance property named id. Using this.id to access the class instance property clearly distinguishes it from the id function parameter.

Class modifiers
TypeScript introduces the public and private access modifiers to indicate whether a class variable or function can be accessed from outside the class itself. Additionally, we can also use the protected access modifier, which we will discuss a little later.

A public property can be accessed by any calling code, as follows:

class ClassWithPublicProperty {
    public id: number | undefined;
}
let publicAccess = new ClassWithPublicProperty();
publicAccess.id = 10;
Here, we have defined a class named ClassWithPublicProperty, which has a single property named id that has been marked as public. This means that we are able to set the value of the id property once we have created an instance of this class, which in this instance has been set to the value 10.

Let's now explore how marking a property private will affect access to this property, as follows:

class ClassWithPrivateProperty {
    private id: number;
    constructor(id: number) {
        this.id = id;
    }
}
let privateAccess = new ClassWithPrivateProperty(10);
privateAccess.id = 20;
Here, we have defined a class named ClassWithPrivateProperty that has a single property named id, which has been marked as private. This class also has a constructor function, which will set the value of the internal id property to the value of the id argument that was passed in. We then create an instance of this class, and attempt to assign the value of 20 to the private id property. This code will generate the following error:

error TS2341: Property 'id' is private and only accessible within class 'ClassWithPrivateProperty'
Here, we can see that because we have marked the id property as private, we cannot access it outside the class itself. Note, however, that within the constructor function, which is inside the class itself, we are able to set the value of the private id property.

Class functions and properties are public by default. The use of class access modifiers is a tool that we can use when writing TypeScript code and helps to protect variables from accidental assignment. These access modifiers, however, will not appear in the JavaScript that is generated from our code. The compiler will, in fact, remove any of these constraints when generating JavaScript.

JavaScript private fields
An experimental proposal to the ECMAScript standard introduces the concept of a private field, by using the hash ( # ) symbol before a property name. This means that if we are targeting a runtime that supports it, such as Node v12, we can write a JavaScript class as follows:

class ClassES6Private {
    #id: number;
    constructor(id: number) {
        this.#id = id;
    }
}
let es6PrivateClass = new ClassES6Private(10);
es6PrivateClass.#id = 20;
Here, we have used the hash symbol as a prefix to the id property in our class definition, which has become #id. The rest of the class is identical to the previous class definition that used the private keyword, and will work in the same way. Note that on the last line of this code snippet, we are attempting to assign the value of 20 to the private #id property of our class instance. This will generate the following error:

error TS18013: Property '#id' is not accessible outside class 'ClassES6Private' because it has a private identifier.
There are pros and cons to using TypeScript's access modifiers versus ES6 private fields. Thus far, we have only worked with the public and private modifiers, but TypeScript enhances these modifiers with both readonly and protected, which we will cover a bit later.

Just remember that the access modifiers used in TypeScript are compiled away in the resulting JavaScript. JavaScript private fields, however, will still translate into the generated JavaScript.

Constructor parameter properties
TypeScript also introduces a shorthand version for access modifiers that can be applied to parameters in a constructor function. As an example of this, consider the following code:

class ClassWithCtorMods {
    constructor(public id: number, private name: string) {
    }
}
let myClassMod = new ClassWithCtorMods(1, "test");
console.log(`myClassMod.id = ${myClassMod.id}`);
console.log(`myClassMod.name = ${myClassMod.name}`);
Here, we have defined a class named ClassWithCtorMods that has a single constructor function. This constructor function has two parameters. The first is named id and is of type number, and the second is named name, and is of type string. Note, however, that we have marked the id property as public within the constructor function definition, and we have marked the name property as private. This shorthand automatically creates an internal id property, and a name property on the class itself, which can be used as standard properties.

We then create an instance of this class, and assign it to a variable named myClassMod. We are then logging the value of both the id property and the name property to the console. This code, however, will generate the following error:

error TS2341: Property 'name' is private and only accessible within class 'ClassWithCtorMods'
This error is telling us that the automatically created property named name is marked as private and is, therefore, not accessible outside of the class itself.

This shorthand syntax is only available for use within the constructor function itself, and not in any other functions of a class.

Readonly
In addition to the public and private access modifiers, we can also mark a class property as readonly. This is similar to the concept of the const keyword, and means that once a value has been assigned to a readonly property, it is not allowed to be modified, as follows:

class ClassWithReadonly {
    readonly name: string;
    constructor(_name: string) {
        this.name = _name;
    }
    setNameValue(_name: string) {
        this.name = _name;
    }
}
Here, we have a class named ClassWithReadonly that has a single property named name, of type string, that has been marked as readonly. We then have a constructor function, that accepts a single parameter named _name. Note how we are assigning the value of the incoming _name parameter to the internal readonly name property of our class. readonly properties are only allowed to set within the constructor function.

We then have a function named setNameValue that is attempting to set the value of the internal name property, but is not a constructor function. This code will generate the following error:

error TS2540: Cannot assign to 'name' because it is a read-only property.
This error occurs when we attempt to assign a value to the name property within the setNameValue member function. As this error shows, we can only set a value for a readonly property within the class constructor function.

Note that readonly can also be used within interface definitions, and that it is also excluded from the generated JavaScript.

Get and set
ECMAScript 5 introduced the concept of property accessors, or get and set functions. A property accessor is simply a function that is called when a user of our class gets the value of a property, or sets its value.

By using a function instead of a simple property, we can detect when someone modifies or accesses a property, which we can use to trigger other logic. Consider the following example:

class ClassWithAccessors {
    private _id: number = 0;
    get id(): number {
        console.log(`get id property`);
        return this._id;
    }
    set id(value: number) {
        console.log(`set id property`);
        this._id = value;
    }
}
Here, we have defined a class named ClassWithAccessors that has a single private property named _id, of type number. We then define a function named id, that logs a message to the console, and then returns the value of the _id property. Note that this function has been marked as a get function, using the get keyword. We then define a set function, also with the name id, that will set the value of the internal _id property.

Note that the get function and the set function are both named id. We can now use this class as follows:

let classWithAccessors = new ClassWithAccessors();
classWithAccessors.id = 10;
console.log(`classWithAccessors.id = ${classWithAccessors.id}`);
Here, we have created a variable named classWithAccessors, which holds an instance of the ClassWithAccessors class. This class instance exposes what looks like a normal property named id. We set the value of this property to 10, and then print the value of the property to the console.

The get and set functions, therefore, are exposing what looks like a property to the outside world, named id, but internally within the class, they are actually functions and not properties. The output of this code is as follows:

set id property
get id property
classWithAccessors.id = 10
Here, we can indeed see that the get and set functions were invoked, even though, to users of this class, it looks like a single id property.

Static functions
A class can mark a function with the static keyword, meaning that there will only be a single instance of this function available throughout the code base. When using a static function, we do not need to create an instance of the class in order to invoke this function, as follows:

class StaticFunction {
    static printTwo() {
        console.log(`2`)
    }
}
StaticFunction.printTwo();
Here, we have the definition of a class named StaticFunction. This class has a single function name printTwo that has been marked as static. This function simply prints the value 2 to the console.

Note, however, the way that we use this function. We do not need to create an instance of this class using the new keyword. We simply call this function by its fully qualified name, that is, <className>.<functionName>, which in this case is StaticFunction.printTwo().

Static properties
In a similar manner to static functions, classes can also have static properties. If a class property has been marked as static, then there will only be a single instance of this property throughout the code base. Consider the following code:

class StaticProperty {
    static count = 0;
    updateCount() {
        StaticProperty.count++;
    }
}
Here, we have defined a class named StaticProperty that has a single property named count that has been marked as static. We have then defined a function named updateCount that will increase the value of the static count property by one each time it is called. Consider how this class is used, as follows:

let firstInstance = new StaticProperty();
let secondInstance = new StaticProperty();
firstInstance.updateCount();
console.log(`StaticProperty.count = ${StaticProperty.count}`);
secondInstance.updateCount();
console.log(`StaticProperty.count = ${StaticProperty.count}`);
Here, we have created two variables named firstInstance and secondInstance that hold instances of the StaticProperty class. We then call the updateCount function on the firstInstance variable, and log the value of the count property of the StaticProperty class to the console.

We then use the secondInstance variable to again call the updateCount function, this time on another instance of the StaticProperty class. The output of this code is as follows:

StaticProperty.count = 1
StaticProperty.count = 2
Here, we can see that both calls to the updateCount function, whether it be from the firstInstance variable, or the secondInstance variable, have updated the value of the static property count. This shows that if a class property has been marked as static, then there will only be a single instance of this property throughout the code base.

Namespaces
When working within large projects, and particularly when working with large numbers of external libraries, there may come a time when two classes or interfaces share the same name. TypeScript uses what are known as namespaces to cater for these situations, as follows:

namespace FirstNameSpace {
    export class NameSpaceClass {}
    class NotExported {}
}
Here, we have used the namespace keyword to create a namespace named FirstNameSpace. This namespace covers all class or interface definitions that fall within its code block. Within the FirstNameSpace code block, we are defining two classes, named NameSpaceClass and NotExported. Note how we have used the export keyword for the NameSpaceClass.

The export keyword will make this class available outside of the namespace itself. As an example of this, consider the following code:

let nameSpaceClass = new FirstNameSpace.NameSpaceClass();
let notExported = new FirstNameSpace.NotExported();
Here, we have created two variables, named nameSpaceClass and notExported. We then create instances of the classes held within the FirstNameSpace namespace. Note how we need to prefix the class name that we are trying to instantiate with the name of the namespace itself, that is, FirstNameSpace.NameSpaceClass. This code, however, will generate the following error:

error TS2339: Property 'NotExported' does not exist on type 'typeof FirstNameSpace'
This error is clearly telling us that the NotExported class is not made available for use outside of the namespace, as it has not been marked with the export keyword.

By making us refer to a class that is within a namespace by its fully qualified name, the compiler will ensure that we have unique class names across our code base.

In this section of the chapter, we have covered the usage of classes, how they are constructed, and how they can be used. We took a look at constructor functions, constructor parameter properties, and the use of getter and setter functions. We then explored static functions and static properties. In the next section of this chapter, we will explore inheritance.

Inheritance
Inheritance is another paradigm that is one of the cornerstones of object-oriented programming. Inheritance allows us to create an object based on another object, thereby inheriting all of its characteristics, including properties and functions. In TypeScript, inheritance can be used by classes and interfaces. In this section of the chapter, we will take a closer look at inheritance, and what it means for both classes and interfaces.

When discussing inheritance, it is important to clearly distinguish between the class that forms the basis of the inheritance structure, and the class that is doing all of the inheriting. We will use the term "base class," or "base interface," to denote the class or interface that forms the base of the inheritance structure, and the term "derived class," or "derived interface," to denote the class or interface that is doing the inheriting.

TypeScript uses the keyword extends to implement inheritance.

Interface inheritance
One interface can form the base interface for one or many other interfaces. As an example of this, consider the following code:

interface IBase {
    id: number;
}
interface IDerivedFromBase extends IBase {
    name: string;
}
class IdNameClass implements IDerivedFromBase {
    name: string = "nameString";
}
Here, we have defined an interface named IBase that has a single property, named id of type number. We then define a second interface named IDerivedFromBase that is using the extends keyword to inherit from IBase. We then define a class named IdNameClass that implements the IDerivedFromBase interface, and has a single property named name of type string. Note that this code will generate the following error:

error TS2420: Class 'IdNameClass' incorrectly implements interface 'IDerivedFromBase'.
  Property 'id' is missing in type 'IdNameClass' but required in type 'IDerivedFromBase'.
Here, we can see that the compiler is telling us that the IDerivedFromBase interface has both a name and an id property, as it inherits the id property from the IBase interface. As we have not defined the id property in our class definition, the class is not correctly implementing the interface, hence the error. We can fix this class definition as follows:

class IdNameClass implements IDerivedFromBase {
    id: number = 0;
    name: string = "nameString";
}
Here, we have added the id property on the class definition for IdNameClass, and are therefore correctly implementing the IDerivedFromBase interface.

When using interface inheritance, we can also narrow a type on a derived interface. Consider the following two interfaces:

interface IBaseStringOrNumber {
    id: string | number;
}
interface IDerivedFromBaseNumber
    extends IBaseStringOrNumber {
    id: number;
}
Here, we have an interface named IBaseStringOrNumber, which has a single property named id that is of type string or number. We then define a second interface that derives from it named IDerivedFromBaseNumber, which has a single property named id that is of type number. So in essence, we have narrowed the type of the id property from string or number to just number in our derived interface.

Interfaces also support multiple inheritance. Consider the following code:

interface IMultiple extends
    IDerivedFromBase,
    IDerivedFromBaseNumber 
{
    description: string;
}
let multipleObject: IMultiple = {
    id: 1,
    name: "myName",
    description: "myDescription"
};
Here, we have defined an interface named IMultiple, which derives from both the IDerivedFromBase and the IDerivedFromBaseNumber interfaces, using a comma separated list. It also defines a property named description of type string. We then define an object named multipleObject that implements this interface. According to our inheritance rules, this IMultiple interface therefore has three properties – an id property of type number from the IDerivedFromBaseNumber interface, a name property from the IDerivedFromBase interface, and also the description property. This multipleObject object, therefore, must provide a property for each of the properties found in the interface.

Class inheritance
Classes can also use the extends keyword to create an inheritance structure. Using our existing definitions for the IBase and IDerivedFromBase interfaces, the following code shows an example of class inheritance:

class BaseClass implements IBase {
    id: number = 0;
}
class DerivedFromBaseClass
    extends BaseClass
    implements IDerivedFromBase 
{
    name: string = "nameString";
}
Here, we have defined a class named BaseClass that implements the IBase interface, and therefore must define an id property of type number. We then have a class definition for a class named DerivedFromBaseClass, which inherits from BaseClass (using the extends keyword), and also implements the IDerivedFromBase interface. As BaseClass already has an id property, the only other property that DerivedFromBaseClass needs to implement is the name property.

JavaScript does not support the concept of multiple inheritance when it comes to classes. This means that a class can only inherit from one other class. Interfaces, however, do support multiple inheritance, as we have seen earlier.

A class, however, can implement multiple interfaces, as follows:

interface IFirstInterface {
    id: number;
}
interface ISecondInterface {
    name: string;
}
class MultipleInterfaces implements
    IFirstInterface,
    ISecondInterface
{
    id: number = 0;
    name: string = "nameString";
}
Here, we have two interfaces that are independent of each other. IFirstInterface has a single property named id of type number, and ISecondInterface has a single property named name of type string. We then define a class named MultipleInterfaces that implements both interfaces, by simply naming them in a comma separated list.

As the MultipleInterfaces class implements both independent interfaces, it must define both an id property and a name property.

The super function
When using inheritance, it is quite common for a base class and a derived class to implement the same method. This is seen most often with class constructors. If a derived class has a constructor, then this constructor must call the base class constructor using the super keyword, or TypeScript will generate an error, as follows:


class BaseClassWithCtor {
    private id: number;
    constructor(id: number) {
        this.id = id;
    }
}
class DerivedClassWithCtor extends BaseClassWithCtor {
    private name: string;
    constructor(id: number, name: string) {
        super(id);
        this.name = name;
    }
}

Function overriding
When a derived class defines a method that has the same name as a base class method, this technique is known as function overriding. The derived class can determine whether or not to call the implementation of the function in the base class. Let's take a look at this technique, as follows:


class BaseClassWithFn {
    print(text: string) {
        console.log(`BaseClassWithFn.print() : ${text}`)
    }
}
class DerivedClassFnOverride extends
    BaseClassWithFn {
    print(text: string) {
        console.log(`DerivedClassFnOverride.print(${text})`);
    }
}

Abstract classes
An abstract class is a class that cannot be instantiated. In other words, it is a class that is designed to be derived from. The purpose of abstract classes is generally to provide a set of basic properties or functions that are shared across a group of similar classes. Abstract classes are marked with the abstract keyword.

`abstract class EmployeeBase {
    public id: number;
    public name: string;
    constructor(id: number, name: string) {
        this.id = id;
        this.name = name;
    }
}
class OfficeWorker extends EmployeeBase {
}
class OfficeManager extends OfficeWorker {
    public employees: OfficeWorker[] = [];
}`

abstract class  need not have any abstract method
but
abstract class methods are not allowed to provide a function implementation. As an example of this, let's update our EmployeeBase class as follows:

`abstract class EmployeeBase {
    public id: number;
    public name: string;
    abstract doWork(): void;
    constructor(id: number, name: string) {
        this.id = id;
        this.name = name;
    }
}`

instanceof
JavaScript provides the instanceof operator to test whether the given function name appears in the prototype of an object. In TypeScript terms, the use of this keyword allows us to detect whether an object is an instance of a class, or whether it has been derived from a particular class. This is best illustrated with an example, as follows:

`class A { }
class BfromA extends A { }
class CfromA extends A { }
class DfromC extends CfromA { }`


Interfaces extending classes
On a final note with regard to interface and class definitions, note that an interface can derive from a class definition, as can be seen in the following example:

`class BaseInterfaceClass {
    id: number = 0;
    print() {
        console.log(`this.id = ${this.id}`);
    }
}
interface IBaseInterfaceClassExt
    extends BaseInterfaceClass {
    setId(id: number): void;
}`


### Modules

Exporting modules
There are two things that we need in order to write and use modules. Firstly, a module needs to expose something to the outside world in order for it to be consumed. This is called exporting a symbol from a module, and uses the TypeScript keyword export, similar to what we saw with namespaces. As an example of this, let's create a source directory named modules, and within this modules directory, a file name Module1.ts containing the following code:

`export class Module1 {
    print(): void {
        localPrint(`Module1.print() called`);
    }
}
function localPrint(text: string) {
    console.log(`localPrint: ${text}`);
}`

Importing modules
In order to consume a symbol that has been exported, any source file that needs this module must import it using the import keyword. Let's test this import syntax by creating a modules_main.ts class in our project's base directory as follows:

`import { Module1 } from "./modules/Module1";
let mod1 = new Module1();
mod1.print();`

Module renaming
When importing a symbol from a module, we can also choose the name that we want to use when referencing the exported symbols within it, as follows:

`import { Module1 as MyMod1 } from "./modules/Module1";
let myRenamedMod = new MyMod1();
myRenamedMod.print();`

### Multiple exports

`export class MultipleClass1 {}
export class MultipleClass2 {}`

import { MultipleClass1, MultipleClass2 } 
    from "./modules/MultipleExports";
let mc1 = new MultipleClass1();
let mc2 = new MultipleClass2();


Module namespaces
There is, however, another syntax that we can use to import multiple symbols from a module. This syntax will import all available exports from a module, without naming each of them individually, by attaching them to a namespace, as follows:

`import * as MultipleExports from "./modules/MultipleExports";
let meMc1 = new MultipleExports.MultipleClass1();
let meMc2 = new MultipleExports.MultipleClass2();`

Default exports
A module file can also mark an exported item as the default export for the file using the default keyword. While this is generally not used for class definitions, it is sometimes used for function definitions. Let's create a new file named modules/DefaultExport.ts, as follows:

`export default function DefaultAdd(
    a: number, b: number) {
    return a + b;
}
export class ModuleNonDefaultExport { }`









