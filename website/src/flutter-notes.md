# Flutter Notes

## What Is Flutter?
1. Flutter is an an open-source UI framework developed by `Google` to build apps for `mobile` (BOTH `IOS` & `Android`), `web` & `desktop` using a **SINGLE** codebase. Primarily written in `dart`.

1. Who Uses Flutter?
    1. Google: Google Pay, Google Ads, and Stadia.
    1. Alibaba: Used for e-commerce apps.
    1. BMW: My BMW app.

1. Key Features of Flutter:
    1. **Single Codebase for Multiple Platforms**
        1. Write one codebase, and deploy to iOS, Android, web, and desktop (Windows, macOS, Linux).
        1. Reduces development time and maintenance effort.

    1. **Hot Reload & Hot Restart**
        1. Quickly view the results of code changes without restarting the app.
        1. Speeds up development and debugging.

    1. **Extensive Amount of Prebuilt Widgets**
        1. Comes with a wide range of customizable widgets (e.g. date picker, input fields, etc.)
        1. Speeds up development and debugging.

    1. **PERFORMANCE**
        1. Flutter apps are natively compiled, ensuring high performance.
        1. Avoids reliance on web view or platform-specific widgets, using its own rendering engine.

    1. **Control as a developer**
        1. Full control over every pixel.

    1. **IT'S FREE!**
        1. Free to use, with an active community providing packages, plugins, and support.

## Basic Knowledge

## Flutter Development In Anroid Studio
### Widgets
1. Flutter uses `widgets` to display & interact with UI elements. There are 2 types of widgets in flutter:
    1. `Stateless` Widgets 
    1. `Stateful` Widgets

1. `Stateless` Widgets
    1. Does not store any internal state that changes over time. (Variables, Widgets, etc.)

    1. Only rebuilds when parent widget changes.

    1. Lightweight & Effecient. Better performance.

    1. Think of it as `"static"` widgets that are only built ONCE. (e.g a splash screen that displays only an image when app launches)

        ```dart
        class MyStatelessWidget extends StatelessWidget {
            final String text;

            MyStatelessWidget({required this.text});
            
            @override
            Widget build(BuildContext context) {
                return Text(
                    text,
                    style: TextStyle(fontSize: 20),
                ); // Text
            }
        }
        ```

1. `Stateful` Widgets
    1. Requires mutable state. It maintains a `State` object that holds data that can change over time and triggers the UI to rebuild when the state changes.

    1. Can update its appearance based on internal or external changes (e.g., user interaction, API responses).

    1. Maintains a separate State class where the mutable state and logic reside.

    1. Can trigger rebuilds using setState to update the UI.

        ```dart
        class MyStatefulWidget extends StatefulWidget {
            @override
            _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
        }

        class _MyStatefulWidgetState extends State<MyStatefulWidget> {
            int counter = 0;

            void incrementCounter() {
                setState((){counter++;});
            }

            @override
            Widget build(BuildContext context) {
                return Column(
                    children: [
                        Text('Counter: $counter', style: TextStyle(fontSize: 20)),
                        ElevatedButton(
                            onPressed: incrementCounter,
                            child: Text('Increment'),
                        ), // Elevated Button
                    ],
                ); // Column
            }
        }
        ```

### Commonly Used Widgets
1. **Material App**
    1. MaterialApp is a `core widget` that provides the foundation for creating apps using Material Design.
    1. Manages navigation between different screens using named `routes` or `Navigator`.
    1. Defines multiple languages with the `localizationsDelegates` and `supportedLocales` properties.

    1. Some commonly used properties of `Material App`:
    
        | Property    | Description |
        | ------ | ------- |
        | home  | The default screen of the app (usually the first widget to display). |
        | theme | Defines the app's default light theme (colors, fonts, etc.). |
        | darkTheme | Defines the app's default dark theme. |
        | routes | A map of route names and corresponding widgets for navigation. |
        | onGenerateRoute | A callback to dynamically generate routes when the app navigates. |
        | locale | Sets the app's default locale for localization. |
        | debugShowCheckedModeBanner | Shows or hides the debug banner in the top-right corner. |	

1. **Scaffold**
    1. Scaffold widget serves as a framework for implementing `Material Design` layouts.
    1. Offers commonly used visual elements and functionalities out-of-the-box. (e.g. `App Bar`, `Bottom Navigation Bar`, etc.)
    1. It saves developers from manually building basic UI components, providing consistency and convenience.

    1. Some commonly used properties of `Scaffold`:

    | Property    | Description |
    | ------ | ------- |
    | appBar  | Adds an AppBar widget at the top of the screen. |
    | body | The primary content of the screen. |
    | floatingActionButton | A button for the primary action of the screen. |
    | drawer |A side menu that slides in from the left. |
    | bottomNavigationBar | A bar at the bottom for navigation. |
    | backgroundColor | Sets the background color of the scaffold. |
    | resizeToAvoidBottomInset | Determines if the body resizes when the keyboard appears. |	

1. **Padding**
    1. Adds space inside widget boundaries
    1. Can specify padding for all sides or individually for top, bottom, left, and right.
        ``` dart
        Padding(
            padding: EdgeInsets.all(16.0), // 16 pixels of padding on all sides
            child: Text('Hello, Flutter!'),
        )
        ```

1. **Center**
    1. Takes a single child and positions it in the middle of the parent.
        ``` dart
        Center(
            child: Text('Hello, Flutter!'),
        )
        ```

1. **Align**
    1. Takes a single child and aligns it in both `Main & Cross Axis`.
        ``` dart
        Center(
            alignment: Alignment.centerLeft,
            child: Text('Hello, Flutter!'),
        )
        ```

1. **SizedBox**
    1. Create a box with specific dimensions. Often used for spacing, aligning, or constraining child widgets.
        ``` dart
        SizedBox(height: 20.0) // Adds vertical space of 20 pixels.

        // Creates an ElevatedButton with dimmensions 100px x 50px
        SizedBox(
            width: 100,
            height: 50,
            child: ElevatedButton(
                onPressed: () {},
                child: Text('Click Me'),
            ),
        )
        ```

1. **Column**
    1. The Column widget arranges its children in a vertical direction, one below the other.

        | Property    | Description |
        | ------ | ------- |
        | children  | A list of widgets to be arranged vertically in the column. |
        | mainAxisAlignment | Defines how the children are aligned along the main axis (vertical). |
        | crossAxisAlignment | Defines how the children are aligned along the main axis (horizontal). |

    1. Example:
        ```dart
        Column(
            children: [
                Text('Item 1'),
                Text('Item 2'),
                Text('Item 3'),
            ],
        )
        ```

1. **Row**
    1. The Row widget arranges its children in a horizontal direction, side by side.

        | Property    | Description |
        | ------ | ------- |
        | children  | A list of widgets to be arranged vertically in the column. |
        | mainAxisAlignment | Defines how the children are aligned along the main axis (vertical). |
        | crossAxisAlignment | Controls whether the column should occupy all available vertical space or only as much space as its children need. |
    
    1. Example:
        ```dart
        Row(
            children: [
                Text('Item 1'),
                Text('Item 2'),
                Text('Item 3'),
            ],
        )
        ```

1. **SingleChildScrollView**
    1. Allows the user to scroll through the content vertically or horizontally.
    1. Only one child widget can be wrapped inside it.
    1. Useful for layouts that need to adapt to varying screen sizes or content lengths.
    1. `NOTE`: `SingleChildScrollView` should not be used for lists with many items; use `ListView` instead for optimized performance.

        ```dart
        SingleChildScrollView(
            child: Column(
                children: [
                    for (int i = 0; i < 50; i++) Text('Item $i'),
                ],
            ),
        )
        ```

1. **TextButton**
    1. Button that displays text and handle user interactions.

    1. Can be styled using `style: ButtonStyle(...),`
        ```dart
        TextButton(
            onPressed: () {
                print('TextButton Pressed');
            },
            child: Text('Click Me'),
        )
        ```

1. **Checkbox**
    1. used to represent a boolean value, either checked or unchecked, and allows users to toggle this state.
    
        ```dart
        // Simple Checkbox (Tick / Untick only)
        Checkbox(
            value: !isMale,
            activeColor: UtilMethods.hexToColor("#00853F"),
            onChanged: (newValue) {
                setState(() {isMale = false;});
            },
        ),

        // To display checkbox + text side by side, use Row
        Row(
            children: [
                Checkbox(
                    value: isMale,
                    activeColor: UtilMethods.hexToColor("#00853F"),
                    onChanged: (newValue) {
                        setState(() {isMale = true;});
                    },
                ),
                Text("Male"),
            ],
        ),

        // To display multiple checkbox + text side by side, use another Row
        Row(
            mainAxisAlignment: MainAxisAlignment.start,
            children: [
            Row(
                children: [
                Checkbox(
                    value: isMale,
                    activeColor: UtilMethods.hexToColor("#00853F"),
                    onChanged: (newValue) {
                    setState(() {
                        isMale = true;
                    });
                    },
                ),
                Text(AppLocalizations.of(context)!.male),
                ],
            ),
            Row(
                children: [
                Checkbox(
                    value: !isMale,
                    activeColor: UtilMethods.hexToColor("#00853F"),
                    onChanged: (newValue) {
                    setState(() {
                        isMale = false;
                    });
                    },
                ),
                Text(AppLocalizations.of(context)!.female),
                ],
            ),
            ],
        ),
        ```

1. **TextField**
    1. The TextField widget is used to allow users to input text.
        ```dart
        final TextEditingController _controller = TextEditingController();

        TextField(
            controller: _controller,
            decoration: InputDecoration(
                hintText: 'Enter text',
            ),
        )

        // get/set text field
        print(_controller.text);
        _controller.text = "string";
        ```


## Common Flutter Practices