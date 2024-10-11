---
title: C# null值使用ToString 报错处理
date: 2020-04-15 21:54:02
tag: code
category: .Net
---
**报错如下：**
**Object reference not set to an instance of an object.**
**原由:**
**获取到的Value为Null**
**代码又是这样的**
**string test = null.ToString();**

**这样是有问题的哦**
**处理办法：**
**Convert.ToString(null)**
**测试代码1；**

```
static void Main(string[] args)
{
  string msg = null;
  Console.WriteLine(Convert.ToString(msg));
  Console.ReadKey();
}

```

**测试代码2：**

```
static void Main(string[] args)
{
  string msg = null;
  //Console.WriteLine(Convert.ToString(msg));
  Console.WriteLine(msg.ToString());
  Console.ReadKey();
}
```

**1不报错**
**2报错**
