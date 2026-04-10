Implement a JSON Parser in Vala
Project Title

Build a JSON Parser in Vala

Your Role

You are going to build a small but real parser in Vala that can read JSON text and turn it into structured in-memory data.

This is not just a syntax exercise. The goal is to help you understand how text becomes data, how parsers work internally, and how to design clean low-level logic in a language that still feels productive.

Why This Project Matters

JSON looks simple when you use it, but implementing support for it teaches several important programming skills:

reading characters one by one
managing position and state
recursive parsing
error reporting
designing data structures
separating lexing/parsing concerns when needed

By the end of this project, you should stop seeing JSON as “magic text” and start seeing it as a format that follows very specific rules.

Project Goal

Create a JSON parser in Vala that accepts a JSON string and produces a tree of values representing:

objects
arrays
strings
numbers
booleans
null

Your parser should also reject invalid JSON with useful error messages.

Learning Objectives

By completing this project, you should be able to:

explain the structure of JSON formally
parse nested data recursively
build and traverse your own value tree
detect malformed input cleanly
think like a compiler/tooling developer rather than just an application developer
What You Are Building

You are building a parser, not a full database, serializer, or schema validator.

The parser’s job is:

take raw text as input
read it according to JSON grammar
construct a structured representation
raise an error if the input is invalid
Functional Requirements

Your parser should support:

Core JSON values
string
number
object
array
true
false
null
Objects
key-value pairs
string keys only
comma-separated entries
nested values allowed
Arrays
comma-separated values
mixed value types allowed
nested arrays/objects allowed
Strings
quoted with double quotes
support common escape sequences
reject invalid or unterminated strings
Numbers
integers
decimals
negative numbers
optionally scientific notation if you want a harder version
Whitespace
ignore valid whitespace between tokens
Errors

Your parser should report:

unexpected end of input
unexpected character
missing colon
missing comma
invalid number
unterminated string
trailing garbage after a valid JSON value
Non-Functional Requirements

Your solution should aim to be:

readable
deliberately structured
easy to debug
modular enough to extend later

Do not write it as one giant function. Even if that works, it misses the point of the exercise.

Suggested Design Direction

A good approach is to think in terms of these parts:

1. Input reader

A small mechanism to:

track the current character
track the current position
move forward safely
peek ahead when needed
2. JSON value model

You need some way to represent parsed values in memory.

Think about how you will represent:

object
array
string
number
boolean
null

This is one of the important design parts of the project.

3. Parser functions

A common structure is to have a main function that parses “a value”, and then helper functions for:

parse_value
parse_object
parse_array
parse_string
parse_number
parse_literal

That structure mirrors the JSON grammar and keeps the code understandable.

Recommended Build Order

Implement this in steps.

Stage 1: Parse literals

Start with:

true
false
null

This gets you comfortable with position tracking and matching fixed text.

Stage 2: Parse strings

Focus on:

opening and closing quotes
collecting characters
basic escape handling

Strings are one of the first places parser bugs show up.

Stage 3: Parse numbers

Handle:

optional minus
digits
optional decimal part

Be strict. JSON is more specific than “anything that looks numeric.”

Stage 4: Parse arrays

Now introduce recursion:

[1, 2, 3]
[true, null, "x"]
nested arrays
Stage 5: Parse objects

Handle:

string key
colon
value
comma-separated members

This combines almost everything you built before.

Stage 6: Full document validation

Make sure:

leading whitespace is allowed
trailing whitespace is allowed
extra junk after a valid value is rejected
Constraints

For this project, try to avoid relying on an existing JSON parsing library.

The point is to understand the internals, not to wrap someone else’s implementation.

You may use standard Vala and its common collections/types, but the parsing logic should be your own.

Expected Output

You should be able to feed the parser examples like:

a simple string value
a flat object
a nested object
an array of objects
mixed nested data

And your program should produce a structured result that can be inspected, printed, or traversed.

Error Handling Expectations

A strong parser does not just fail. It fails helpfully.

At minimum, your error messages should try to say:

what went wrong
where it went wrong
what was expected instead

For example, “expected : after object key at position X” is much better than “parse error”.

Stretch Goals

Once the core parser works, you can level it up with:

line and column tracking instead of only index position
Unicode escape support
scientific notation numbers
pretty-printing the parsed tree
converting the value tree back into JSON
unit tests for valid and invalid cases
a small CLI that reads a file and validates it
Suggested Test Cases

You should test both success and failure.

Valid examples
simple literals
empty object
empty array
nested arrays
nested objects
mixed structures
strings with escapes
numbers with decimals and negatives
Invalid examples
missing closing brace
missing closing bracket
object key without quotes
missing colon
double commas
trailing comma
unclosed string
invalid escape
invalid number format
extra text after valid JSON
What I Will Be Looking For

If I were reviewing this as your teacher, I would care about:

Is the parser logically broken into parts?
Does it correctly handle nesting?
Does it reject invalid input properly?
Are the error messages useful?
Is the code structured so future-you can extend it?

I would care less about making it “clever” and more about making it solid.

Common Mistakes to Avoid
writing one huge parse function
not skipping whitespace consistently
forgetting to validate commas/colons properly
accepting invalid numbers
ignoring trailing input
poor error messages
mixing parsing logic with debug printing everywhere
Deliverables

By the end, you should have:

a Vala project containing your parser
a JSON value representation
a small test harness or CLI entry point
a set of sample inputs
basic documentation explaining your parser design
Definition of Done

This project is done when:

valid JSON parses correctly
invalid JSON fails clearly
nested objects and arrays work
your code is understandable without rereading it five times
you can explain how each parser function contributes to the full grammar
Final Guidance

Treat this like a miniature compiler project.

Do not rush to “make it work somehow.” Build it in layers, test each layer, and keep the structure clean. The real value here is not just ending with a JSON parser — it is learning how to think precisely about syntax, state, and data transformation.