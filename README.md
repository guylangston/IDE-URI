# Feature Request: Hyperlink to Visual Studio from Browser
### For use with Markdown, Resharper in generating 'live' code documentation

I want to be able to document my code in a markdown file, but reference namespaces, projects, classes and methods using namespace.dot.notation. 
Clicking on that link would navigate to that link in visual studio.

## URI

codelink-{ide}://Some.NameSpace.SomeClass.SomeMethod()?hint-path=SomeAssembley.dll
- where {ide}='vs' for Visual Studio,
- and the query ?-onwards is entirely optional

## Example
```
Our calculations are controller by the class OurCompanyNamespace.Logic.Components.MasterComponent,
which has the key method OurCompanyNamespace.Logic.Components.MasterComponent.Process()  
```
### Which would rendered as:
```
Our calculations are controller by the class <a href="vs-code-link://OurCompanyNamespace.Logic.Components.MasterComponent" tooltip="OurCompanyNamespace.Logic.Components.MasterComponent">MasterComponent</a>,
which has the key method <a href="vs-code-link://OurCompanyNamespace.Logic.Components.MasterComponent.Process()" tooltip="OurCompanyNamespace.Logic.Components.MasterComponent.Process()">MasterComponent.Process(...)</a>
```
## Patterns to match

Cannonical:
- NameSpace: Root.Inner.Other.*
- Class: Root.Inner.Other.ClassName
- Method: Root.Inner.Other.ClassName.MethodName(string, bool, int) or

Lossy:
- JustClassName (must have CammelCase)
- JustClassName.MethodName() (where overloading applies)
- Root.Inner.Other.ClassName.MethodName(name1, name2, name3)


Where namespace is ```OurCompanyNamespace.Logic.Components``` and Class is ```MasterComponent``` and method ```Process(...)```

A post-processor should scan the links and turn then into a-tags with am appropriate application-registered href (see the example above)

Clicking this link in a brower will take you to this link.

## Tooling
- IDE Right-Click on any class or method > Get Hyperlink URI. Will place an appropriately formatted URI onto the clipboard.
- Refactor-Rename would sync in MarkDown files 

---------------------------------
JetBrains Resharper support request: (https://resharper-support.jetbrains.com/hc/en-us/requests/613319)

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/FeatureRequest?src=hash">#FeatureRequest</a> <a href="https://twitter.com/resharper">@Resharper</a> Hyperlink to Visual Studio from Browser/IDE using namespace pattern matching. See <a href="https://t.co/q5ofEjZuLb">https://t.co/q5ofEjZuLb</a></p>&mdash; Guy Langston (@guy_langston) <a href="https://twitter.com/guy_langston/status/687316620180635648">January 13, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

