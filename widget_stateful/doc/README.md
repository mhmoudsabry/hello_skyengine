# Widget StatefulComponent

https://github.com/kyorohiro/hello_skyengine/tree/master/widget_stateful

![](a001.png)![](a002.png)![](a003.png)

```
// following code is checked in 2016/01/13
import 'package:flutter/material.dart';

void main() {
  runApp(new MyStatefulComponent());
}

class MyStatefulComponent extends StatefulComponent {
  State createState() {
    return new MyState();
  }
}

class MyState extends State<MyStatefulComponent> {
  int colorId = 0;
  Color backgroundColor = new Color.fromARGB(0xaa, 0xff, 0xaa, 0xaa);

  MyState() {
    print(">>>> new MyState");
  }

  Widget build(BuildContext context) {
    print(">>>> build");
    BoxDecoration decoration = new BoxDecoration(backgroundColor: backgroundColor);
    Container c = new Container(width: 500.0, height: 500.0, decoration: decoration);
    GestureDetector d = new GestureDetector(onTap: () {
      print(">>>> onTap");
      setState(updateColor);
    }, child: c);
    return new Center(child: d);
  }

  updateColor() {
    print(">>>> updateColor");
    colorId++;
    switch (colorId % 3) {
      case 0:
        backgroundColor = new Color.fromARGB(0xaa, 0xff, 0xaa, 0xaa);
        break;
      case 1:
        backgroundColor = new Color.fromARGB(0xaa, 0xaa, 0xff, 0xaa);
        break;
      case 2:
        backgroundColor = new Color.fromARGB(0xaa, 0xaa, 0xaa, 0xff);
        break;
    }
  }

  @override
  void initState() {
    super.initState();
    print(">>>> initState");
  }

  @override
  void dispose() {
    super.dispose();
    print(">>>> dispose");
  }
}
```
