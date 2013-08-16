---
layout: recipe
title: Class
---

# 싱글턴(Singleton)

## 해법

{% highlight objectivec %}
+(MyClass *)sharedMyClass {
  static dispatch_once_t once;
  static MyClass *shared = nil;
  dispatch_once(&once, ^{
    shared = [[MyClass alloc] init];
  });
  return shared;
}
{% endhighlight %}

## 다른 해법(느림)

{% highlight objectivec %}
+(MyClass *)sharedMyClass {
  static MyClass *shared = nil;
  @synchronized (self) {
    if (shared==nil) {
      shared = [[MyClass alloc] init];
    }
    return shared;
  }
}
{% endhighlight %}

## 잘못된 해법(스레드 안전이 아님)

{% highlight objectivec %}
+(MyClass *)sharedMyClass {
  static MyClass *shared = nil;
  if (shared==nil) {
    shared = [[MyClass alloc] init];
  }
  return shared;
}
{% endhighlight %}

## 참고

* [Cocoa Samurai: Singletons: You're doing them wrong](http://cocoasamurai.blogspot.com/2011/04/singletons-your-doing-them-wrong.html)
