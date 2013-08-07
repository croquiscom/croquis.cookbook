---
layout: recipe
title: Array
---

# 배열 묶기(concatenating Arrays)

## 해법 1

배열의 내용을 그대로 둘 경우 Array.prototype.concat을 사용한다.

{% highlight javascript %}
a = [1, 2, 3];
b = [4, 5, 6];
c = a.concat(b); // => [1, 2, 3, 4, 5, 6]
{% endhighlight %}

이때 a, b의 내용은 변하지 않는다.

## 해법 2

현 배열에 다른 배열의 내용을 추가할 경우 Array.prototype.push를 사용한다.

{% highlight javascript %}
a = [1, 2, 3];
b = [4, 5, 6];
Array.prototype.push.apply(a, b); // => 6
a; // => [1, 2, 3, 4, 5, 6]
{% endhighlight %}

push 명령을 다음과 같이 써도 상관없다.

{% highlight javascript %}
a.push.apply(a, b);
// 또는
[].push.apply(a, b);
{% endhighlight %}

하지만 다음은 잘못된 결과를 반환하므로 주의한다.

{% highlight javascript %}
// 잘못된 결과
a.push(b); // => 4
a; // => [1, 2, 3, [4, 5, 6]]
{% endhighlight %}
