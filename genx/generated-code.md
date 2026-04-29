|  |  |  |
| --- | --- | --- |
| genx - system for framework independent analysis. |
| Prev |  | Next |


---

# <a name="AEN227"></a>Chapter 4. Generated Code

This chapter has three sections the first two describe the code generated
				for SpecTcl and Root.  The last section describes how to build and wrap
				unpackers for SpecTcl and Root so that you can use the same code with both.

All generators are expected to generate their definitions and code
                in a namespace.  By default, this namepace is derived from the
                basename of the output file by removing leading path elements.
                This default namespace can be overidden using the
                namespace directive in the specificationfile.

In our example, we've used the default namespace.

# <a name="AEN233"></a>4.1. Code Generated for SpecTcl

In this section we'll look at the code generated for the SpecTcl target.
					If you're not curious feel free to skip this section and the next as you
					don't really need to know the nitty gritty details of the generated
					code to write an unpacker.

First let's look at what a struct is.   For SpecTcl, a struct becomes
					a C++ struct.  In addition to the data members, each struct has an
					`Initialize` method which takes, as a parameter
					a base name for the members of the struct.   The generated code for
					a struct's `Initialize` method initializes
					all value and array members and invokes the `Initialize`
					method of each struct and each element of a structarray.

SpecTcl naming conventions are used for structarray intializer calls so that
					each element has a numeric parameter name part.  All this may be somewhat
					confusing so let's look at some examples.

<a name="AEN241"></a>**Example 4-1. Initialization of simple struct members for SpecTcl - the declaration**

```
struct Ta  {
    value a
    value b low=-1.5 high=1.5 units=cm
}

					
```

This struct generates the following bit of code in the header:

<a name="AEN245"></a>**Example 4-2. Initialization of simple struct members for SpecTcl - the header**

```
namespace spec  {


/** Data Structure definitions **/

struct Ta {
   CTreeParameter a;
   CTreeParameter b;
   void Initialize(const char* basename);
};
...
}
					
```

The first thing to note is that the structs are generated in a namespace.
					The namespace is derived from the basename of the output file.  You should,
					therefore, use the same output file basename for all targets (pointing each
					target to a different directory e.g.).

Next note that each member generates a tree parameter.  The
					`Initialize` takes a `basename`
					parameter.  This will be either the name of the instance if this
					structure is instantated, or the path to the member if this struct is
					a member of another struct that's instantiated.  More on that later.

The `Initialize` implementation generated is:

<a name="AEN254"></a>**Example 4-3. 
						Initialization of simple struct members for SpecTcl - the implementation
					**

```


void spec::Ta::Initialize(const char* basename)
{
   std::string name(basename);
   a.Initialize(name + '.' + "a", 100, 0, 100, "");
   b.Initialize(name + '.' + "b", 100, -1.5, 1.5, "cm");
}
					
```

The two points to see are how the basename has a period and the member
						name grafted on to each call to the member's own
						`Initialize` member and how the metadata
						for `b` are used to parameterize that
						variable's `Initialize` call.  The
						intermediate code does not provide a distinction between provided
						and not provided metadata, instead it defaults missing metadata as
						SpecTcl itself does if metadata is not proviced.  That's where the
						parameterization of `a`'s
						`Initialize` method comes from.

Let's look at a more complex example:

<a name="AEN264"></a>**Example 4-4. SpecTcl complex struct initialization - definition file:**

```
struct Tb {
    array a[10]
    array b[20]
}

struct Tc {
    struct Tb a
    structarray Tb b[10]
    value c units=megawidgets
    array d[100]
        low = 0 high = 4095 bins=4096.65 units=channels;
}

					
```

This generates a pair of structs.  `Tb`
					has a pair of `CTreeParameterArray` members.
					`Tc` contains a struct an array of structs (both
					`Tb`) a value and an array.  This generates
					the header file segment:

<a name="AEN272"></a>**Example 4-5. SpecTcl complex struct initialization - header file**

```
namespace spec  {

...

struct Tb {
   CTreeParameterArray a;
   CTreeParameterArray b;
   void Initialize(const char* basename);
};

struct Tc {
   struct Tb a;
   struct Tb b[10];
   CTreeParameter c;
   CTreeParameterArray d;
   void Initialize(const char* basename);
};

...
}
						
```

Note how both structs have initialization methods defined.  Let's see
					the code generated for the two `Initialize`
					methods:

<a name="AEN277"></a>**Example 4-6. SpecTcl complex struct initialization - C++ file**

```
void spec::Tb::Initialize(const char* basename)
{
   std::string name(basename);
   a.Initialize(name + '.' + "a", 0, 100, 100, "", 10, 0);
   b.Initialize(name + '.' + "b", 0, 100, 100, "", 20, 0);
}

void spec::Tc::Initialize(const char* basename)
{
   std::string name(basename);
   a.Initialize((name + '.' + "a").c_str());
   for (int i = 0; i < 10; i++) {
      char index[3];
      sprintf(index, "%02d", i);
      std::string elname = name + "." +  "b." + index;
      b[i].Initialize(elname.c_str());
   }
   c.Initialize(name + '.' + "c", 100, 0, 100, "megawidgets");
   d.Initialize(name + '.' + "d", 0, 4095, 4096, "channels", 100, 0);
}

					
```

Note how the `Tb` just initializes the tree parameter
					arrays.  `Tc`, on the other hand initializes each of its
					elements and a loop is generated to create new parameter base names like
					arrays for the structarray element and to initialize each struct in that
					structarray individually.

Finally, SpecTcl does not require any code for
					`SetupEvent` as SpecTcl itself invalidates the
					underlying parameters very efficiently (an O(1) algorithm).  Similarly
					`CommitEvent` requires no code from SpecTcl.
					`Initializee`, however must get the initialization
					ball rolling by initializing all instances.  Those instances in turn,
					if they are structs or structarrays will initialize their members.

Here are the instance declarations:

<a name="AEN288"></a>**Example 4-7. Initialization code for SpecTcl - definition file**

```
value b low=-100.5 high=100 bins=200 units=cm
value a

array c[20]
array d[5] units=furlongs

structinstance Ta stuff
structinstance Tc mystuff
structarrayinstance Tb morestuff[20]
						
					
```

This generates the following in the header:

<a name="AEN292"></a>**Example 4-8. Initialization code for SpecTcl - header**

```
namespaces spec {
...
#ifndef IMPLEMENTATION_MODULE
extern CTreeParameter b;
extern CTreeParameter a;
extern CTreeParameterArray c;
extern CTreeParameterArray d;
extern struct Ta stuff;
extern struct Tc mystuff;
extern struct Tb morestuff[20];

#endif
/** API functions callable by the user **/

void Initialize();
void SetupEvent();
void CommitEvent();
}
					
```

Note the #ifdef that brackets the instance declarations.
					This is because the implementation file will actually define those objects
					and C++ considers it an error to both declare an object as externa dn
					define it locally.  Thus the C++ module will have a
					#define IMPLEMENTATION_MODULE prior to including
					the generated header.

The header also declares the three API functions.

<a name="AEN299"></a>**Example 4-9. Initialization code for SpecTcl - C++ file**

```
namespace spec {
CTreeParameter b;
CTreeParameter a;
CTreeParameterArray c;
CTreeParameterArray d;
struct Ta stuff;
struct Tc mystuff;
struct Tb morestuff[20];
}

...
void spec::SetupEvent() {}
void spec::CommitEvent() {}
void spec::Initialize()
{
  spec::b.Initialize("b", 200, -100.5, 100, "cm");
  spec::a.Initialize("a", 100, 0, 100, "");
  spec::c.Initialize("c", 100, 0, 100, "", 20, 0);
  spec::d.Initialize("d", 100, 0, 100, "furlongs", 5, 0);
  spec::stuff.Initialize("stuff");
  spec::mystuff.Initialize("mystuff");
   for (int i = 0; i < 20; i++)
   {
        char index[3];
        sprintf(index, "%02d", i);
        std::string elname = std::string("morestuff.") + index;
        spec::morestuff[i].Initialize(elname.c_str());
   }
}

					
```

This should be about what you'd expect to see for initialization by now.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Translating structure declaration files into code for a target | Up | Code generated for Root |
