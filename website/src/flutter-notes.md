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

        ```java
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

        ```java
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
        ``` java
        Padding(
            padding: EdgeInsets.all(16.0), // 16 pixels of padding on all sides
            child: Text('Hello, Flutter!'),
        )
        ```

1. **Center**
    1. Takes a single child and positions it in the middle of the parent.
        ``` java
        Center(
            child: Text('Hello, Flutter!'),
        )
        ```

1. **Align**
    1. Takes a single child and aligns it in both `Main & Cross Axis`.
        ``` java
        Center(
            alignment: Alignment.centerLeft,
            child: Text('Hello, Flutter!'),
        )
        ```

1. **SizedBox**
    1. Create a box with specific dimensions. Often used for spacing, aligning, or constraining child widgets.
        ``` java
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
        ```java
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
        ```java
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

        ```java
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
        ```java
        TextButton(
            onPressed: () {
                print('TextButton Pressed');
            },
            child: Text('Click Me'),
        )
        ```

1. **Checkbox**
    1. used to represent a boolean value, either checked or unchecked, and allows users to toggle this state.
    
        ```java
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
        ```java
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

        | Property    | Description |
        | ------ | ------- |
        | controller  | A TextEditingController that controls the text being edited. |
        | decoration | Allows customizing the visual appearance of the TextField (e.g., hint, border, icons). |
        | keyboardType | Defines the type of keyboard to be displayed (e.g., TextInputType.number, TextInputType.emailAddress). |
        | textInputAction | Defines what action appears on the keyboard (e.g., TextInputAction.done). |
        | onChanged | A callback triggered when the text changes. |
        | onSubmitted | A callback triggered when the user submits the input (e.g., presses "Enter"). |
        | maxLines | The maximum number of lines that the text field can expand to (for multi-line input). |
        | obscureText | Hides the text (useful for passwords). |
        | autocorrect | Enables or disables autocorrection for text input. |
        | autofocus | Whether the field should automatically gain focus when the widget is displayed. |

## Common Flutter Practices
1. Use `Stateful Widgets` Wisely. Only use StatefulWidget when you need to update the UI based on user interaction or other events.

1. Avoid Large Widgets in Build Methods. Break down large widgets into smaller components to make the code easier to read and maintain.

1. Use `const` Constructors When Possible. It improves performance as it helps Flutter optimize the widget tree and avoid unnecessary rebuilds.

1. Leverage `Async` and `Await` for `Async Operations`. For async operations, always use async/await for better readability and maintainability.

1. Follow the `DRY Principle`. `Don't Repeat Yourself`. Try to `modularize` widgets/methods as much as possible.

1. Use `Responsive Design`. Use `screen width` & `screen height` percentages for positioning & padding. This is to ensure responsiveness in your app.

## Navigator
1. To change pages in your mobile app, I recommend using flutter's built-in `Navigator` class. 
1. `Route`: A route is essentially a screen or a page in your app. In Flutter, each screen is typically represented by a Widget, and routes are managed by the Navigator.
1. `Stack-Based Navigation`: The Navigator uses a stack to manage routes. `Pushing` a new `route` places it at the top of the stack. `Popping` the stack removes the `route` at the top of the stack.

1. Basic implementation of changing page:
    ```java
    Navigator.push(
        context,
        MaterialPageRoute(
            builder: (context) => NewPage(),
        ),
    );
    ```
    1. `context`: The current context, used to find the navigator in the widget tree.
    1. `MaterialPageRoute`: A common type of route that animates with a material-style transition.
    1. `builder`: A function that returns the widget for the new screen.

1. To go back 1 page:
    ```java
    Navigator.pop(context);
    ```
    1. `NOTE`: Be careful when using pop. If you accidently pop the last `route` in the stack, you'll get a black screen.

1. If you'd like to use `named routes` where you assign a string to a page instead, you can do so like so:
    1. Go to your `main.dart` and under the `MaterialApp`, define the `routes` and their associated names:
        ```java
        MaterialApp(
            initialRoute: '/',
            routes: {
                '/': (context) => HomePage(),
                '/new': (context) => NewPage(),
            },
        );
        ```
        `initialRoute`: Sets the first page shown on the application's launch.
        
    1. Use `pushNamed` instead when changing pages:
        ```java
        Navigator.pushNamed(context, '/new');
        ```
    1. `Pop` remains unchanged:
        ```java
        Navigator.pop(context);
        ```
    1. Other commonly used functions:
        1. `pushReplacement()`: Removes the current route from the stack and pushes a new route in its place.
            ```java
            Navigator.pushReplacement(
                context,
                MaterialPageRoute(builder: (context) => NewPage()),
            );
            ```
        1. `pushAndRemoveUntil()`: Pushes a new route onto the stack and removes all the routes until a specific condition is met.
            ```java
            Navigator.pushAndRemoveUntil(
                context,
                MaterialPageRoute(builder: (context) => NewPage()),
                (Route<dynamic> route) => false, // Remove all previous routes
            );
            ```
        1. `popUntil()`: Pops routes until a specific route condition is met, without removing the route you're looking for.
            ```java
            Navigator.popUntil(context, ModalRoute.withName('/home'));
            ```
    1. You can control how new routes are pushed onto the stack, including the transition animations, by using custom PageRoute implementations.
        ```java
        Navigator.push(
            context,
            PageRouteBuilder(
                pageBuilder: (context, animation, secondaryAnimation) => NewPage(),
                transitionsBuilder: (context, animation, secondaryAnimation, child) {
                const begin = Offset(1.0, 0.0);
                const end = Offset.zero;
                const curve = Curves.easeInOut;
                var tween = Tween(begin: begin, end: end).chain(CurveTween(curve: curve));
                var offsetAnimation = animation.drive(tween);

                return SlideTransition(position: offsetAnimation, child: child);
                },
            ),
        );
        ```
        `NOTE`: I recommend seperating the transition into it's own class extending `PageRouteBuilder`. With this, you can use the same transition anytime you want to change your pages like so:

        ```java
        class SlidePageRoute extends PageRouteBuilder {
            final Widget page;
            final double duration;

            SlidePageRoute({required this.page, this.duration = 250})
                : super(
                pageBuilder: (context, animation, secondaryAnimation) => page,
                transitionsBuilder: (context, animation, secondaryAnimation, child) {
                    const begin = Offset(1.0, 0.0);
                    const end = Offset.zero;
                    const curve = Curves.easeInOut;
                    var tween = Tween(begin: begin, end: end).chain(CurveTween(curve: curve));
                    var offsetAnimation = animation.drive(tween);

                    return SlideTransition(position: offsetAnimation, child: child);
                },
                transitionDuration: Duration(milliseconds: duration.toInt()),
            );
        }

        // When changing pages
        Navigator.push(
            context,
            SlidePageRoute(page: const NewPage())
        );
        ```

## Custom Classes & Functions
1. Creating classes is similar to `Java`. You can do it like so:

    ```java
    class MyClass
    {
        int index = 0;
        final bool isMale;
        late String string;

        MyClass({this.index = 0, required this.isMale});

        void printString(){
            string = "Among Us";
            print(string);
        }

        String getString(){
            return string;
        }
    }

    class TestClass
    {
        MyClass myClass = MyClass(isMale: true);
        MyClass myClass1 = MyClass(isMale: true, index: 100);
    }
    ```

    1. However, unlke `Java`, you **MUST** define a value for vairables you create. Either through the calss's contructor or by directly assigning it. If you want to define the value later in your code, you can mark it as `late`.
    
    1. Marking a vairable as `final` assigns a value to the vairable only once, and that value cannot be modified afterward, similar to `const`. However, the value can be determined during runtime through the `contructor`, unlike a const variable, which must be known at compile time. You **MUST** assign the value through the contructor or directly assign the value when using `final`.

    1. To ensure a vairable is assigned a value when calling the class's `contructor`, you can use the `required` modifier.

    1. You can also assign a default value to a vairable in the `contructor`. This makes it optional to assign the value through the `contructor` when you `instantiate` the class later.

## Adding Custom Assets (Images, Fonts, etc.)
1. `pubsec.yaml` is essential for managing the packages and libraries your project relies on, specifying the minimum required versions, and organizing resources like images, fonts, and localization files. It comes installed with `Flutter`. You can find it in the root folder of your project.

1. Create a new folder called assets in the `root` folder of your project. 

1. Create 2 sub folders called `fonts` and `images`. Add your fonts and images into the respective folders.

1. Inside the `pubsec.yaml` file, find the `assets:` section under `flutter:`. Uncomment it and add the following:
    ```yaml
    assets:
        - assets/images/
    ```
    This references the images folder, and you're now able to access all the images under the `assets/images` folder like so:
    ```java
    Image.asset(
        'assets/images/image.png',
        height: screenHeight * 0.15,
        fit: BoxFit.contain,
    ),
    ```
    `NOTE`: Be sure to click on the `pub get` button that'll appear at the below the tabs list after making changes to `pubsec.yaml`, or your changes won't be saved!

1. To add your custom fonts in `pubsec.yaml` file, find the `fonts:` section under `flutter:`. Uncomment it and add the following:
    ```yaml
    fonts:
       - family: AcuminVairableConcept
        fonts:
        - asset: assets/fonts/AcuminVariableConcept.otf
    ```
    Unfortunatley, unlike images, you have to define the file path to each individual font and which family it belongs to. You can use the font like so:
    ```java
    Text(
        "Mobile No*",
        style: const TextStyle(
            fontFamily: "AcuminVairableConcept"
        ),
    ),
    ```

## Localization
1. You can refer to the full documentation for setting up localization [here](https://docs.flutter.dev/ui/accessibility-and-internationalization/internationalization).

1. Add the following dependencies in your pubsec.yaml file:
    ```yaml
    dependencies:
    flutter:
        sdk: flutter
    flutter_localizations:
        sdk: flutter
    intl: any
    ```
    Be sure to do `pub get` to install the dependecies.
1. In main.dart, import the necessary package.
    ```dart
    import 'package:flutter_localizations/flutter_localizations.dart';
    ```
1. You can now define which locales your app will support in the `build()` in `main.dart`, along with the necessary delegates:
    ```java
    return const MaterialApp(
      ...
      localizationsDelegates: const [
        AppLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
        GlobalMaterialLocalizations.delegate,
        GlobalCupertinoLocalizations.delegate,
      ],
      supportedLocales: const [
        Locale('en', ''), // English
        Locale('zh', 'CN'), // Simplified Chinese
      ],
      locale: Locale('en', ''), // Set default locale
      ...
    );
    ```

1. Now, to add your own localized messages, you'll need to:

1. Add the intl package as a dependency, pulling in the version pinned by `flutter_localizations`. Run this in the project's terminal:
    ```
    flutter pub add intl:any
    ```

1. Open the pubspec.yaml file and enable the generate flag under the `flutter:` section:
    ```yaml
    flutter:
        ...
        generate: true # Add this line
        ...
    ```

1. Create a new yaml file in your project's `root` directory. Name it `l10n.yaml` and add the following:
    ```yaml
    arb-dir: lib\localization
    template-arb-file: app_en.arb
    output-localization-file: app_localizations.dart
    ```

1. Now under `lib` folder, create a sub folder called `localization` and create 2 files inside the folder:
    1. app_en.arb (For english)
    1. app_zh.arb (For chinese)
    
1. Now run the following command in the project terminal:
    ```
    run flutter gen-l10n
    ```
    You should find generated files in `${FLUTTER_PROJECT}/.dart_tool/flutter_gen/gen_l10n` after the command executes.

1. Now you're all set up! To define locales, do so in the `app_en.arb` and `app_zh.arb` files like so:
    ```arb
    // app_en.arb
    {
        "noNameError": "Please provide your full name.",
    }

    //app_zh.arb
    {
        "noNameError": "CHINESE VERSION HERE",
    }
    ```
    Be sure to save your project (using `CTRL + S`) after making changes to either files.

1. To make use of the locales in your app, you can do so using:
    ```java
    import 'package:flutter_gen/gen_l10n/app_localizations.dart';

    Text(AppLocalizations.of(context)!.noNameError);
    ```

1. To change the locales during runtime, you'll have to convert your `main widget` to a `stateful widget` and store the locale in a vairable like so:
    ```java
    enum LanguageOption {
        english,
        chinese
    }

    class MyApp extends StatefulWidget {
        const MyApp({super.key});

        static void setLocale(BuildContext context, LanguageOption newLanguage) async {
            _MyAppState? state = context.findAncestorStateOfType<_MyAppState>();

            switch (newLanguage)
            {
                case LanguageOption.english:
                    state?.changeLanguage(const Locale('en', ''));
                    break;
                case LanguageOption.chinese:
                    state?.changeLanguage(const Locale('zh', 'CN'));
                    break;
            }

            languageOption = newLanguage;
            saveData();
        }

        @override
        State<MyApp> createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {
        Locale _locale = const Locale('en', '');

        changeLanguage(Locale locale) {
            setState(() {
            _locale = locale;
            });
        }

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                localizationsDelegates: const [
                    AppLocalizations.delegate,
                    GlobalWidgetsLocalizations.delegate,
                    GlobalMaterialLocalizations.delegate,
                    GlobalCupertinoLocalizations.delegate,
                ],
                supportedLocales: const [
                    Locale('en', ''),
                    Locale('zh', 'CN'),
                ],
                locale: _locale,
            );
        }
    }
    ```

1. All you need now are 2 `checkboxes` that called the `MyApp.setLocale()` function:
    ```java
    // Switch to chinese
    MyApp.setLocale(context, LanguageOption.chinese);
    // Switch to english
    MyApp.setLocale(context, LanguageOption.english);
    ```

## REST API Communication
1. To use APIs through web, you'll need to use the `http` plugin. Ensure that you have the `http` plugin listed in `pubspec.yaml`. Run `pub get` to install the plugin.
    ```
    dependencies:
        http: ^1.0.0
    ```
1. It's recommend to `decouple` the API logic to its own class, so I created a file called `api_manager.dart`.

1. As API calls can take time depending on the network `traffic` & `connection`, we'll be using Flutter's `Future` class. `Future` is an `abstract interface class` usually used in asynchronous operations.

1. We can further `decouple` each API's logic to its own individual function like so:
    ```java
    static Future<Map<String, dynamic>> loginUser(String mobile, String password) async {
        final url = Uri.parse('$apiURL?v=1&action=login-user&mobile_number=$mobile&password=$password');
        http.Response response = await UtilMethods.sendUrl(url);

        print(response.body);

        if (response.statusCode == 200) {
            return json.decode(response.body);
        } else {
            throw Exception('Failed to log in');
        }
    }
    ```

    1. Firstly, we define an `asynchronous static` function that returns a `Future<Map<String, dynamic>>` class. `Map<String, dynamic>` can be modified according to the API response you have. In this example, the API response is an `associative array` in php (`Map` in dart) called `response`:
        ```php
        $response = [
            "success" => true,
            "message" => "loginSuccess",
            "data" => "UsernameHere"
        ]
        ```
    1. Next, we create the `API URL` using Flutter's `Uri.parse()`. Then send it using a custom `sendUrl()` function:
        ```dart
        static Future<http.Response> sendUrl(Uri url) async {
            final headers = {
                'User-Agent':  await getUserAgent(),
            };

            return await http.get(url, headers: headers);
        }
        ```
        1. `sendUrl()` is an `async` method that returns a `Future<http.Response>`. This function sets the `User-Agent` header in the request (for security), then use the `http.get` method from `http` plugin we downloaded. 
        1. We'll use `await` to wait for the async operations to run. This is to ensure the code runs sequentially despite having potential delays, as well as preventing `race cases`.
        1. `sendUrl()` will request the api and return the response `asynchronously`.

1. After getting the `http response`, we need to check for `200 ok` status code to see if the request was successful. If so, we `json_decode` the response's body and return it as `Map<String, dynamic>`.
    ```
    if (response.statusCode == 200) {
        return json.decode(response.body);
    } else {
        throw Exception('Failed to log in');
    }
    ```

1. To use the `loginUser()` function in another file, we can just import it using:
    ``` dart
    import 'package:rewards/api_manager.dart';

    Future<void> _login() async {
        try {
            final response = await ApiManager.loginUser(
                mobileNumber,
                password,
            );

            if (response['success'] == true) {
                print("Success");
            } else {
                print("Failed To Login");
            }
        } catch (e) {
            print(e.toString());
        }
    }
    ```
    1. We'll create a wrapper function to handle the logic when login succeeds / fails / throws an exception. This function will also be an async function that returns `Future<void>`.