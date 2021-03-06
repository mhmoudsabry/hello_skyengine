# Widget Scaffold

https://github.com/kyorohiro/hello_skyengine/tree/master/widget_scaffold

![](screen.png)

```
// following code is checked in 2016/01/13
import 'package:flutter/material.dart';

void main() {
  MyBody body = new MyBody();
  //Widget statusBar = new Text("--status bar--",style:new TextStyle(fontSize:10.0));
  Widget toolBar = new ToolBar(
    center: new Text("center"),
    left: new Text("left"),
    right: [
      new Text("right1"),
      new Text("right2"),
      new Text("right3")],
    backgroundColor: new Color.fromARGB(0xff, 0xff, 0xaa, 0xaa)
  );
  // .package/material_design_icons/lib/icons/content/drawable-hdpi/ic_add_black_24dp.png
  Widget floatingActionButton = new FloatingActionButton(
    child: new Icon(
      icon: 'content/add',
      size: IconSize.s24
    ),
    backgroundColor: new Color.fromARGB(0xff, 0xaa, 0xff, 0xaa),
    onPressed: (){
      print("pressed");
      body.text += "\n hello";
      body.update();
    }
  );
  Scaffold s = new Scaffold(
    toolBar:toolBar,
    body:body,
    floatingActionButton:floatingActionButton//,
    //bottomSheet:statusBar
  );

  // 2015/10/26 if use IconButton's icon option, need MatrialApp?
  runApp(new MaterialApp(
      title: "Scaffold",
      routes: <String, RouteBuilder>{
        '/': (RouteArguments args) {
          return s;
        },
      }));
  //runApp(s);
}

class MyBody extends StatefulComponent {
  String text = "--hello--";
  State<MyBody> current = null;
  State createState() {
    current = new MyBodyState();
    return current;
  }
  update() {
    if(current != null) {
      current.setState((){});
    }
  }
}

class MyBodyState extends State<MyBody> {
  Widget build(BuildContext context) {
    return new Material(
      child: new Center(
        child: new Text(config.text)
      )
    );
  }
}

```

```
# flutter.yaml
material-design-icons:
  - name: action/account_balance
  - name: action/assessment
  - name: action/help
  - name: action/search
  - name: action/settings
  - name: action/thumb_down
  - name: action/thumb_up
  - name: content/add
  - name: navigation/arrow_back
  - name: navigation/menu
  - name: navigation/more_vert
```
