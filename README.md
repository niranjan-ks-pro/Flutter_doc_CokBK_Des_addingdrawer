# Flutter_doc_CokBK_Des_addingdrawer
 https://docs.flutter.dev/cookbook/design/drawer
 Add a drawer to a screen
========================

1.  [Cookbook](https://docs.flutter.dev/cookbook)
2.  [Design](https://docs.flutter.dev/cookbook/design)
3.  [Add a drawer to a screen](https://docs.flutter.dev/cookbook/design/drawer)

In apps that use Material Design, there are two primary options for navigation: tabs and drawers. When there is insufficient space to support tabs, drawers provide a handy alternative.

In Flutter, use the [`Drawer`](https://api.flutter.dev/flutter/material/Drawer-class.html) widget in combination with a [`Scaffold`](https://api.flutter.dev/flutter/material/Scaffold-class.html) to create a layout with a Material Design drawer. This recipe uses the following steps:

1.  Create a `Scaffold`.
2.  Add a drawer.
3.  Populate the drawer with items.
4.  Close the drawer programmatically.

[](https://docs.flutter.dev/cookbook/design/drawer#1-create-a-scaffold)1\. Create a `Scaffold`
----------------------------------------------------------------------------------------------

To add a drawer to the app, wrap it in a [`Scaffold`](https://api.flutter.dev/flutter/material/Scaffold-class.html) widget. The `Scaffold` widget provides a consistent visual structure to apps that follow the Material Design Guidelines. It also supports special Material Design components, such as Drawers, AppBars, and SnackBars.

In this example, create a `Scaffold` with a `drawer`:

content_copy

```
Scaffold(
  drawer: // Add a Drawer here in the next step.
);
```

[](https://docs.flutter.dev/cookbook/design/drawer#2-add-a-drawer)2\. Add a drawer
----------------------------------------------------------------------------------

Now add a drawer to the `Scaffold`. A drawer can be any widget, but it's often best to use the `Drawer` widget from the [material library](https://api.flutter.dev/flutter/material/material-library.html), which adheres to the Material Design spec.

content_copy

```
Scaffold(
  drawer: Drawer(
    child: // Populate the Drawer in the next step.
  ),
);
```

[](https://docs.flutter.dev/cookbook/design/drawer#3-populate-the-drawer-with-items)3\. Populate the drawer with items
----------------------------------------------------------------------------------------------------------------------

Now that you have a `Drawer` in place, add content to it. For this example, use a [`ListView`](https://api.flutter.dev/flutter/widgets/ListView-class.html). While you could use a `Column` widget, `ListView` is handy because it allows users to scroll through the drawer if the content takes more space than the screen supports.

Populate the `ListView` with a [`DrawerHeader`](https://api.flutter.dev/flutter/material/DrawerHeader-class.html) and two [`ListTile`](https://api.flutter.dev/flutter/material/ListTile-class.html) widgets. For more information on working with Lists, see the [list recipes](https://docs.flutter.dev/cookbook#lists).

content_copy

```
Drawer(
  // Add a ListView to the drawer. This ensures the user can scroll
  // through the options in the drawer if there isn't enough vertical
  // space to fit everything.
  child: ListView(
    // Important: Remove any padding from the ListView.
    padding: EdgeInsets.zero,
    children: [
      const DrawerHeader(
        decoration: BoxDecoration(
          color: Colors.blue,
        ),
        child: Text('Drawer Header'),
      ),
      ListTile(
        title: const Text('Item 1'),
        onTap: () {
          // Update the state of the app.
          // ...
        },
      ),
      ListTile(
        title: const Text('Item 2'),
        onTap: () {
          // Update the state of the app.
          // ...
        },
      ),
    ],
  ),
);
```

[](https://docs.flutter.dev/cookbook/design/drawer#4-close-the-drawer-programmatically)4\. Close the drawer programmatically
----------------------------------------------------------------------------------------------------------------------------

After a user taps an item, you might want to close the drawer. You can do this by using the [`Navigator`](https://api.flutter.dev/flutter/widgets/Navigator-class.html).

When a user opens the drawer, Flutter adds the drawer to the navigation stack. Therefore, to close the drawer, call `Navigator.pop(context)`.

content_copy

```
ListTile(
  title: const Text('Item 1'),
  onTap: () {
    // Update the state of the app
    // ...
    // Then close the drawer
    Navigator.pop(context);
  },
),
```

`\
`

[](https://docs.flutter.dev/cookbook/design/drawer#interactive-example)
-----------------------------------------------------------------------
