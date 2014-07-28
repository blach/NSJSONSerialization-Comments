# NSJSONSerialization+Comments

This Objective-C category adds C style comment support to NSJSONSerialization. It allows you to read JSON files with `//` and `/* … */` comments. It is similar to JSONKit's `JKParseOptionComments` option.

# Usage

You can use this category's `JSONObjectWithCommentedData:options:error:` method just like NSJSONSerialization's `JSONObjectWithData:options:error:`:

```Objective-C
id object = [NSJSONSerialization JSONObjectWithCommentedData:data options:0 error:&error];
```

It strips single line and multi-line comments as well as whitespace before it hands over the data to NSJSONSerialization.

The code works directly on UTF-8 data without converting it to an NSString, but also detects UTF-16 and UTF-32 byte order marks (BOM). If a non-UTF-8 BOM is detected, it converts the data to UTF-8. The most efficient encoding to use for parsing is UTF-8.

I've also added the convenience methods `JSONObjectWithCommentedContentsOfURL:options:error:` and `JSONObjectWithCommentedContentsOfFile:options:error:` to load JSON directly from a file or url. 

Finally `stringWithJSONObject:options:error:` is a convenience method around `dataWithJSONObject:options:error:` if you need an NSString instead of NSData.

# License

Code in this repository is licensed under the MIT license (see the LICENSE file).