# Ignoring Null - and Five Other Horrible Things Most Developers Do

Hi, thanks for checking out this talk. The files here are static and as-of the delivery of the talk. There is an accompanying blog post that goes with this talk where I can update if needed. You can find it out at https://m.eado.ws/s/2023/stirtrek. You can find any follow-up blog posts to this talk as well as links to my other talks at https://m.eado.ws/blog.

## Files

- [Horrible_Things.pdf](Horrible_Things.pdf)
- [Horrible_Things.pptx](Horrible_Things.pptx)

## Apology (With Details)

I delivered misinformation in the part of my talk referring to autoboxing and autounboxing in Java when passing primitives to a method parameter. I basically asserted this:

```java
void someMethod(int someParameter) {
    ...
}

int someVariable;
someMethod(someVariable); // would result in an autoboxing of someVariable and an autounboxing of someParameter
```

The reality, however, is that's bunk. The above example would pass `someVariable` by value. There is no need to box or unbox. To make a more subtle point, the exmaple blow would result in autoboxing, and if you come across this (probably extremely rare) scenario, it could be an issue with performance. Furthermore, I do still hold to the broader assertion that using more POJOs in a language without a struct type is a good idea, so the alternative POJO approach I provided in the examples would still be my recommendation. I may blog about how structured value types allow for a more functional approach.

```java
void someMethod(Integer someParameter) {
    ...
}

int someVariable;
someMethod(someVariable); // would result in an autoboxing of someVariable to the Integer wrapper type
```

**Here is the apology in full:**

> I research the heck out of my talks and take pride in the quality of the product of that work. I tend to pick topics that require a fair bit of research because that’s what motivates me. **I missed the mark**, however, **when talking about autoboxing and unboxing of primitive types in Java**.  
>The object conversion issue is one that can hurt you in most languages, but I didn’t want this to be just a C# talk. Remembering back to my two years as a Java programmer, this issue came to mind. I searched the web to see if the situation had changed, but **my terminology was not precise enough to give me the answer I needed**. Instead, **I gravitated toward the answer I wanted** (to make my job easier).  
>Just so I can be 100% clear. **Boxing and unboxing primitives in Java happens if the parameter type is mismatched with the variable**. **It is not a normal problem in Java** but can be an insidious one when it occurs. **It certainly doesn’t happen as I described it**.  
>Anyway, because I owe it to the community, I’ll leave this deck otherwise untouched, but will follow up with a detailed blog post for wonks like me. Check https://m.eado.ws/blog for this and other upcoming posts.
