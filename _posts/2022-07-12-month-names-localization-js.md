---
layout: post
title: "How to generate months of the year with localization in Javascript?"
date: 2022-07-12 05:10:08 +0530
categories: javascript
---

If you build a flutter app with swipe gestures for linux, it won't work by default. To make it work, you have to specify a custom scroll behavior as the following snippet.

```dart
class CustomScrollBehavior extends MaterialScrollBehavior {
  @override
  Set<PointerDeviceKind> get dragDevices => {
        PointerDeviceKind.touch,
        PointerDeviceKind.mouse,
      };
}

class App extends StatelessWidget {
  const App({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: const PageWithSwipeGestures(),
      debugShowCheckedModeBanner: false,
      scrollBehavior: CustomScrollBehavior(),
      // showPerformanceOverlay: true,
    );
  }
}
```

Happy coding!
