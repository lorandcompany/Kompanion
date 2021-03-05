# How to Use the Docs
***
# Implementing Kompanion Features

On each feature, there is a link that you can open using a Kustom `Touch Action`. The link follow the standard URL layout. The link looks like this: 
```http
kompanion://edit/something?key1=value1&key2=value2
```
Lets break it down into parts
```
[kompanion://edit/something] [  ?  ] [key1=value1] [    &    ] [key2=value2]
      Feature Link            Query   Parameter 1   Separator   Parameter 2
```
1. Feature Links
-  These are indicated at the very start of the feature documentation. Some feature links have 2 types: `Edit (kompanion://edit/something)` and `Open (kompanion://open/something)`. The `App Link` feature uses this in order to indicate if you want to open an app or edit it.
2. Query Sign
-  If the feature is asking for some information, add this before adding parameters. Some features such as `Icon Packs` don't need this. Almost all of them do, though.
3. Parameters
-  Has 2 parts: the `Key` and the `Value`. The `Key` is what Kompanion asks of and the `Value` is what you specify. All the keys are indicated in the documentation. Some features will refuse to work and throw an error when some values aren't specified. Some values tagged `[OPTIONAL]` are optional and have their own default values (which will be also indicated in the feature documentation) if not specified. An example of this would be the `name` parameter which will be used in order to get values that Kompanion returns so make sure to keep track of them.
4. Parameter Separator
-  If there are 2 or more parameters in the link, separate them with the separator `&`

***

# Getting Values from Kompanion Features

You will be using the `br(Kompanion, <something>)` Kustom formula for getting values. This *something* will be indicated on the feature documentation.

They will usually look like this in the documentation: 
```txt
image_[name]
```
If something is enclosed in `[]`, you will be replacing that with the value of the key you indicated. *(Check Implementing Kompanion Features)*. 

For example, you used the `Global Text` feature which requires 2 parameters: `name` and `text`. You enter these values like so:
```
kompanion://edit/globa?name=sampleglobal&text=something
```
In order to get the value you entered in the textbox, the documentation tells you to use this pattern:
```
global_[name]
```
Because `name` is surrounded by `[]`, you replace it with the value you entered on the parameter, in this case it's `sampleglobal`. It will now look like this.
```
global_sampleglobal
```
These return values can be empty. Please have someting as fallback when it happens.