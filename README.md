# Diagonal Movement Plugin

A JavaScript plugin that detects the direction of the mouse movement (diagonal vs vertical). It can be used when implementing dropdown navigations to differentiate between hovering a new menu item vs moving to a sub-menu.

This is a modified version of the [jQuery-menu-aim plugin](https://github.com/kamens/jQuery-menu-aim)

1. Replaced jQuery with Vanilla JS;
2. Based on the [CodyHouse Framework](https://codyhouse.co/ds/docs/framework) utility functions;
3. Minor changes;

## Here's how you can use the plugin:

```
new menuAim({
  menu: menu, //menu element
  rows: rows, // list items in the menu element
  submenuSelector: submenus, // items that have sub-navigation
  activate: function(row) {
    // function to be executed when hovering over a list item
  },
  deactivate: function(row) {
    // function to be executed when leaving a list item (and its sub-navigation element)
  },
  exitMenu: function(row) {
    // function to be executed when leaving the menu element
  }
});
```

The following options can be passed to menuAim. All functions execute with
the relevant row's HTML element as the execution context ('this'):

```
new menuAim({
  //menu element
  menu: menu,

  // Function to call when a row is purposefully activated. Use this
  // to show a submenu's content for the activated row.
  activate: function() {},

  // Function to call when a row is deactivated.
  deactivate: function() {},

  // Function to call when mouse enters a menu row. Entering a row
  // does not mean the row has been activated, as the user may be
  // mousing over to a submenu.
  enter: function() {},

  // Function to call when mouse exits a menu row.
  exit: function() {},

  // Function to call when mouse exits the entire menu. If this returns
  // true, the current row's deactivation event and callback function
  // will be fired. Otherwise, if this isn't supplied or it returns
  // false, the currently activated row will stay activated when the
  // mouse leaves the menu entirely.
  exitMenu: function() {},

  // Elements in the menu that are rows
  rows: false, //if false, get direct children

  // You may have some menu rows that aren't submenus and therefore
  // shouldn't ever need to "activate." If so, filter submenu rows w/
  // this selector. Defaults to "*" (all elements).
  submenuSelector: "*",

  // Direction the submenu opens relative to the main menu. This
  // controls which direction is "forgiving" as the user moves their
  // cursor from the main menu into the submenu. Can be one of "right",
  // "left", "above", or "below". Defaults to "right".
  submenuDirection: "right"
});
```

menu-aim assumes that you are using a menu with submenus that expand
to the menu's right. It will fire events when the user's mouse enters a new
dropdown item *and* when that item is being intentionally hovered over.

## Want an example to learn from?
Here's a [dropdown navigation](https://codyhouse.co/ds/components/app/dropdown) where the plugin is used.

## More Info 
See the [Diagonal Movement Info](https://codyhouse.co/ds/components/info/diagonal-movement) page on [Codyhouse.co](https://codyhouse.co/).