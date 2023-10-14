import 'package:flutter/material.dart';
import 'package:intl/intl.dart';
import 'package:shared_preferences/shared_preferences.dart';
import 'package:google_fonts/google_fonts.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SplashScreen(),
      theme: ThemeData(
        primaryColor: Color.fromARGB(255, 2, 11, 115), // Light Blue
        scaffoldBackgroundColor:
            Color.fromARGB(255, 235, 236, 237), // Dark Blue
      ),
    );
  }
}

class SplashScreen extends StatefulWidget {
  @override
  _SplashScreenState createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> {
  @override
  void initState() {
    super.initState();
    // Delay for 2 seconds before navigating to FrontPage
    Future.delayed(Duration(seconds: 2), () {
      Navigator.of(context).pushReplacement(
        MaterialPageRoute(builder: (context) => FrontPage()),
      );
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Stack(
        children: [
          Container(
            decoration: BoxDecoration(
              gradient: LinearGradient(
                begin: Alignment.topCenter,
                end: Alignment.bottomCenter,
                colors: [
                  Color(0xFF460645), // #460645
                  Color(0xFFFF5450), // #ff5450
                ],
                stops: [0.0, 1.0], // Color stops for the gradient
              ),
            ),
            height: double.infinity,
            width: double.infinity,
          ),
          Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Text(
                  "PIPE GAS CALCULATOR",
                  style: TextStyle(
                    fontSize: 28,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                    shadows: [Shadow(blurRadius: 10.0, color: Colors.black)],
                  ),
                ),
                SizedBox(height: 20),
                CircularProgressIndicator(
                  valueColor: AlwaysStoppedAnimation<Color>(Colors.white),
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }
}

class FrontPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        automaticallyImplyLeading: false, // Remove the back button
        backgroundColor: Color(0xFF460645), // #460645
        elevation: 0,
      ),
      body: Column(
        children: [
          Expanded(
            flex: 2, // Adjust the ratio as needed
            child: Container(
              decoration: BoxDecoration(
                gradient: LinearGradient(
                  begin: Alignment.topCenter,
                  end: Alignment.bottomCenter,
                  colors: [
                    Color.fromRGBO(70, 6, 69, 1), // #460645
                    Color(0xFFFF5450), // #ff5450
                  ],
                  stops: [0.0, 1.0], // Color stops for the gradient
                ),
                borderRadius: BorderRadius.only(
                  bottomLeft: Radius.circular(30),
                  bottomRight: Radius.circular(30),
                ),
              ),
              child: Center(
                child: Column(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Text(
                      "Meadow Castle Piped Gas Calculator", // Moved the title here
                      style: TextStyle(
                        fontSize: 20,
                        fontWeight: FontWeight.bold,
                        color: Color.fromARGB(255, 245, 246, 250),
                        shadows: [
                          Shadow(blurRadius: 10.0, color: Colors.black)
                        ],
                      ),
                    ),
                    SizedBox(height: 50), // Add some space below the title
                    Text(
                      "Hey.. Welcome !! 😀 ",
                      style: TextStyle(
                        fontSize: 18,
                        fontWeight: FontWeight.bold,
                        color: Color.fromARGB(255, 245, 246, 250),
                      ),
                    ),
                  ],
                ),
              ),
            ),
          ),
          // Add other widgets or content below as needed
          Expanded(
            flex: 3, // Adjust the ratio as needed
            child: Container(
              color: Colors.white,
              child: Center(
                child: Column(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Text(
                      "App Features at a Glance", // Title for the instruction manual
                      style: TextStyle(
                        fontSize: 21,
                        fontWeight: FontWeight.bold,
                        color: Color.fromRGBO(70, 6, 69, 1),
                      ),
                    ),
                    SizedBox(height: 20),
                    // Instructions for each operation with bullet points
                    ListTile(
                      leading: Icon(Icons.arrow_right),
                      title: Text(
                          "Calculate Bill - Use this feature to calculate your piped gas bill accurately."),
                    ),
                    ListTile(
                      leading: Icon(Icons.arrow_right),
                      title: Text(
                          "Update Gas Rate - Keep your gas rate up-to-date with this function."),
                    ),
                    ListTile(
                      leading: Icon(Icons.arrow_right),
                      title: Text(
                          "Show Statement - Access your piped gas statements effortlessly."),
                    ),
                    ListTile(
                      leading: Icon(Icons.arrow_right),
                      title: Text(
                          "Choose the category wisely, whether you are a user or a gas collector."),
                    ),
                    SizedBox(height: 20),
                    ElevatedButton(
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Color.fromRGBO(255, 84, 80, 1),
                      ),
                      onPressed: () {
                        Navigator.of(context).push(
                          PageRouteBuilder(
                            pageBuilder:
                                (context, animation, secondaryAnimation) =>
                                    CategoryPage(),
                            transitionsBuilder: (context, animation,
                                secondaryAnimation, child) {
                              const begin =
                                  Offset(0.0, 1.0); // Start from the bottom
                              const end = Offset(0.0, 0.0); // Slide to the top
                              const curve = Curves.easeInOut;
                              var tween = Tween(begin: begin, end: end)
                                  .chain(CurveTween(curve: curve));

                              // Adjust the duration to control the speed (larger value = slower)
                              Animation<double> slowUpAnimation =
                                  CurvedAnimation(
                                      parent: animation,
                                      curve: Interval(0.0, 1.0));
                              slowUpAnimation = Tween(begin: 0.0, end: 1.0)
                                  .animate(slowUpAnimation);

                              return SlideTransition(
                                position: slowUpAnimation.drive(tween),
                                child: child,
                              );
                            },
                          ),
                        );
                      },
                      child: Container(
                        color: Color.fromRGBO(243, 239, 242, 0.063),
                        child: Text("Choose Category"),
                      ),
                    ),
                  ],
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

class CategoryPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "Choose Category",
          textAlign: TextAlign.center,
          style: GoogleFonts.montserrat(
            fontSize: 16,
            fontWeight: FontWeight.bold,
            color: Color.fromARGB(255, 246, 246, 249),
            shadows: [
              Shadow(
                  blurRadius: 10.0, color: const Color.fromARGB(70, 6, 69, 1))
            ],
          ),
        ),
        backgroundColor: const Color.fromRGBO(70, 6, 69, 1),
        centerTitle: true,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.push(
                  context,
                  PageRouteBuilder(
                    pageBuilder: (context, animation, secondaryAnimation) =>
                        ReadingPage(),
                    transitionsBuilder:
                        (context, animation, secondaryAnimation, child) {
                      const begin = Offset(0.0, 1.0);
                      const end = Offset.zero;
                      const curve = Curves.easeInOut;
                      var tween = Tween(begin: begin, end: end)
                          .chain(CurveTween(curve: curve));
                      var offsetAnimation = animation.drive(tween);
                      return SlideTransition(
                        position: offsetAnimation,
                        child: child,
                      );
                    },
                  ),
                );
              },
              child: Text("Gas Collector Page"),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.push(
                  context,
                  PageRouteBuilder(
                    pageBuilder: (context, animation, secondaryAnimation) =>
                        UserPage(), // Added UserPage here
                    transitionsBuilder:
                        (context, animation, secondaryAnimation, child) {
                      const begin = Offset(0.0, 1.0);
                      const end = Offset.zero;
                      const curve = Curves.easeInOut;
                      var tween = Tween(begin: begin, end: end)
                          .chain(CurveTween(curve: curve));
                      var offsetAnimation = animation.drive(tween);
                      return SlideTransition(
                        position: offsetAnimation,
                        child: child,
                      );
                    },
                  ),
                );
              },
              child: Text("User Page"), // Added "USER" button
            ),
          ],
        ),
      ),
    );
  }
}

class ReadingPage extends StatefulWidget {
  @override
  _ReadingPageState createState() => _ReadingPageState();
}

class _ReadingPageState extends State<ReadingPage> {
  double previousReading = 0.0;
  double currentReading = 0.0;
  double gasRate = 68.60; // Default gas rate
  double billAmount = 0.0;
  double totalBillAmountCollected = 0.0;
  String flatNumber = "";
  String userName = "";

  List<UserStatement> history = [];

  @override
  void initState() {
    super.initState();
    loadGasRate();
    loadHistory();
  }

  Future<void> loadGasRate() async {
    final prefs = await SharedPreferences.getInstance();
    final savedGasRate = prefs.getDouble('gas_rate');
    if (savedGasRate != null) {
      setState(() {
        gasRate = savedGasRate;
      });
    }
  }

  Future<void> saveGasRate(double newGasRate) async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setDouble('gas_rate', newGasRate);
  }

  Future<void> loadHistory() async {
    final prefs = await SharedPreferences.getInstance();
    final historyData = prefs.getString('history');
    if (historyData != null) {
      setState(() {
        history = UserStatement.listFromString(historyData);
        calculateTotalBillAmountCollected();
      });
    }
  }

  Future<void> saveHistory() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setString('history', UserStatement.listToString(history));
  }

  void calculateTotalBillAmountCollected() {
    totalBillAmountCollected = history.fold(
      0.0,
      (previous, statement) => previous + statement.billAmount,
    );
  }

  _calculateBill() {
    setState(() {
      double rawBillAmount = (currentReading - previousReading) * 2.6 * gasRate;
      billAmount = rawBillAmount; // Round up to the nearest whole rupee
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "Meadow Castle Piped Gas Calculator",
          textAlign: TextAlign.center,
          style: GoogleFonts.montserrat(
            fontSize: 16,
            fontWeight: FontWeight.bold, // Make it bold
          ),
        ),
        backgroundColor: const Color.fromRGBO(70, 6, 69, 1),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            TextField(
              decoration: InputDecoration(labelText: "Flat No."),
              onChanged: (value) {
                setState(() {
                  flatNumber = value;
                });
              },
            ),
            TextField(
              decoration: InputDecoration(labelText: "Name"),
              onChanged: (value) {
                setState(() {
                  userName = value;
                });
              },
            ),
            TextField(
              keyboardType: TextInputType.number,
              decoration: InputDecoration(labelText: "Previous Reading"),
              onChanged: (value) {
                setState(() {
                  previousReading = double.tryParse(value) ?? 0.0;
                });
              },
            ),
            TextField(
              keyboardType: TextInputType.number,
              decoration: InputDecoration(labelText: "Current Reading"),
              onChanged: (value) {
                setState(() {
                  currentReading = double.tryParse(value) ?? 0.0;
                });
              },
            ),
            SizedBox(height: 20),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: _calculateBill,
              child: Text("Calculate Bill"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                _showUpdateDialog();
              },
              child: Text("Update Gas Rate"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                _showUserDetailsDialog();
              },
              child: Text("Show Statement"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                _showHistory();
              },
              child: Text("History"),
            ),
            SizedBox(height: 20),
            Text(
              "Bill Amount: ₹ ${billAmount.toStringAsFixed(2)}",
              style: TextStyle(fontSize: 18),
            ),
          ],
        ),
      ),
    );
  }

  _showUpdateDialog() {
    showDialog(
      context: context,
      builder: (context) {
        double newGasRate = gasRate;
        return AlertDialog(
          title: Text("Update Gas Rate"),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              Text("Current Gas Rate: ₹ $gasRate"),
              TextField(
                keyboardType: TextInputType.number,
                decoration: InputDecoration(labelText: "New Gas Rate"),
                onChanged: (value) {
                  newGasRate = double.tryParse(value) ?? gasRate;
                },
              ),
            ],
          ),
          actions: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () async {
                setState(() {
                  gasRate = newGasRate;
                });
                await saveGasRate(gasRate);
                Navigator.of(context).pop();
              },
              child: Text("Save"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.of(context).pop();
              },
              child: Text("Cancel"),
            ),
          ],
        );
      },
    );
  }

  _showUserDetailsDialog() {
    final nettConsumption = currentReading - previousReading;
    final convertedToKg = nettConsumption * 2.6;

    showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          title: Text("User Details"),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text("Flat No.: $flatNumber"),
              Text("Name: $userName"),
              Text("Previous Reading: $previousReading"),
              Text("Current Reading: $currentReading"),
              Text(
                  "Nett Consumption (Nm^3): ${nettConsumption.toStringAsFixed(2)}"),
              Text("Converted to Kg: ${convertedToKg.toStringAsFixed(2)}"),
              Text("Gas Rate per Kg: ₹ $gasRate"),
              Text("Total Bill Amount: ₹ ${billAmount.toStringAsFixed(2)}"),
              Text(
                  "Date and Time: ${DateFormat('dd-MM-yyyy HH:mm:ss').format(DateTime.now())}"),
              ElevatedButton(
                style: ElevatedButton.styleFrom(
                    backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
                onPressed: () {
                  _saveToHistory();
                  Navigator.of(context).pop();
                },
                child: Text("Save"),
              ),
            ],
          ),
          actions: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.of(context).pop();
              },
              child: Text("Close"),
            ),
          ],
        );
      },
    );
  }

  _saveToHistory() {
    final statement = UserStatement(
      flatNumber: flatNumber,
      userName: userName,
      previousReading: previousReading,
      currentReading: currentReading,
      gasRate: gasRate,
      billAmount: billAmount,
      dateTime: DateTime.now(),
    );
    setState(() {
      history.add(statement);
      totalBillAmountCollected +=
          billAmount; // Update the total bill amount collected
    });
    saveHistory();
  }

  _showHistory() {
    Navigator.of(context).push(
      MaterialPageRoute(
        builder: (context) => HistoryPage(
          history: history,
          totalBillAmountCollected: totalBillAmountCollected,
        ),
      ),
    );
  }
}

class HistoryPage extends StatefulWidget {
  final List<UserStatement> history;
  double totalBillAmountCollected;

  HistoryPage({required this.history, required this.totalBillAmountCollected});

  @override
  _HistoryPageState createState() => _HistoryPageState();
}

class _HistoryPageState extends State<HistoryPage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("History"),
        backgroundColor: const Color.fromRGBO(70, 6, 69, 1),
      ),
      body: Column(
        children: [
          ListTile(
            title: Text(
              "Total Bill Amount Collected: ₹ ${widget.totalBillAmountCollected.toStringAsFixed(2)}",
              style: TextStyle(fontSize: 18),
            ),
            tileColor: Colors.blueGrey,
            contentPadding: EdgeInsets.symmetric(horizontal: 16),
          ),
          Expanded(
            child: ListView.builder(
              itemCount: widget.history.length,
              itemBuilder: (context, index) {
                final statement = widget.history[index];
                return ListTile(
                  title: Text("Flat No.: ${statement.flatNumber}"),
                  subtitle: Text("Name: ${statement.userName}"),
                  trailing: Row(
                    mainAxisSize: MainAxisSize.min,
                    children: [
                      Text(
                        "Bill Amount: ₹ ${statement.billAmount.toStringAsFixed(2)}",
                        style: TextStyle(fontSize: 16),
                      ),
                      IconButton(
                        icon: Icon(Icons.delete),
                        onPressed: () {
                          _deleteStatement(index);
                        },
                      ),
                    ],
                  ),
                  onTap: () {
                    _showDetailsDialog(statement);
                  },
                );
              },
            ),
          ),
        ],
      ),
    );
  }

  _showDetailsDialog(UserStatement statement) {
    showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          title: Text("User Details"),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text("Flat No : ${statement.flatNumber}"),
              Text("Name: ${statement.userName}"),
              Text("Previous Reading: ${statement.previousReading}"),
              Text("Current Reading: ${statement.currentReading}"),
              Text(
                  "Nett Consumption (Nm^3): ${statement.nettConsumption.toStringAsFixed(2)}"),
              Text(
                  "Converted to Kg: ${statement.convertedToKg.toStringAsFixed(2)}"),
              Text("Gas Rate per Kg: ₹ ${statement.gasRate}"),
              Text(
                  "Total Bill Amount: ₹ ${statement.billAmount.toStringAsFixed(2)}"),
              Text(
                  "Date and Time: ${DateFormat('dd-MM-yyyy HH:mm:ss').format(statement.dateTime)}"),
            ],
          ),
          actions: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.of(context).pop();
              },
              child: Text("Close"),
            ),
          ],
        );
      },
    );
  }

  _deleteStatement(int index) {
    setState(() {
      widget.totalBillAmountCollected -= widget.history[index].billAmount;
      widget.history.removeAt(index);
    });
    _saveHistory();
  }

  _saveHistory() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setString(
        'history', UserStatement.listToString(widget.history));
  }
}

class UserStatement {
  final String flatNumber;
  final String userName;
  final double previousReading;
  final double currentReading;
  final double gasRate;
  final double billAmount;
  final DateTime dateTime;

  UserStatement({
    required this.flatNumber,
    required this.userName,
    required this.previousReading,
    required this.currentReading,
    required this.gasRate,
    required this.billAmount,
    required this.dateTime,
  });

  double get nettConsumption => currentReading - previousReading;

  double get convertedToKg => nettConsumption * 2.6;

  static List<UserStatement> listFromString(String data) {
    final List<UserStatement> list = [];
    final lines = data.split('\n');
    for (var line in lines) {
      final parts = line.split(',');
      if (parts.length == 7) {
        list.add(UserStatement(
          flatNumber: parts[0],
          userName: parts[1],
          previousReading: double.parse(parts[2]),
          currentReading: double.parse(parts[3]),
          gasRate: double.parse(parts[4]),
          billAmount: double.parse(parts[5]),
          dateTime: DateTime.parse(parts[6]),
        ));
      }
    }
    return list;
  }

  static String listToString(List<UserStatement> list) {
    final List<String> lines = [];
    for (var statement in list) {
      lines.add(
          '${statement.flatNumber},${statement.userName},${statement.previousReading},${statement.currentReading},${statement.gasRate},${statement.billAmount},${statement.dateTime.toIso8601String()}');
    }
    return lines.join('\n');
  }
}

class UserPage extends StatefulWidget {
  @override
  _UserPageState createState() => _UserPageState();
}

class _UserPageState extends State<UserPage> {
  double previousReading = 0.0;
  double currentReading = 0.0;
  double gasRate = 68.60; // Default gas rate
  double billAmount = 0.0;

  @override
  void initState() {
    super.initState();
    loadGasRate();
  }

  Future<void> loadGasRate() async {
    final prefs = await SharedPreferences.getInstance();
    final savedGasRate = prefs.getDouble('user_gas_rate');
    if (savedGasRate != null) {
      setState(() {
        gasRate = savedGasRate;
      });
    }
  }

  Future<void> saveGasRate(double newGasRate) async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setDouble('user_gas_rate', newGasRate);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "Meadow Castle Pipe Gas Calculator",
          textAlign: TextAlign.center,
          style: GoogleFonts.montserrat(
            fontSize: 16,
            fontWeight: FontWeight.bold,
          ),
        ),
        backgroundColor: const Color.fromRGBO(70, 6, 69, 1),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            TextField(
              keyboardType: TextInputType.number,
              decoration: InputDecoration(labelText: "Previous Reading"),
              onChanged: (value) {
                setState(() {
                  previousReading = double.tryParse(value) ?? 0.0;
                });
              },
            ),
            TextField(
              keyboardType: TextInputType.number,
              decoration: InputDecoration(labelText: "Current Reading"),
              onChanged: (value) {
                setState(() {
                  currentReading = double.tryParse(value) ?? 0.0;
                });
              },
            ),
            SizedBox(height: 20),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: _calculateBill,
              child: Text("Calculate Bill"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: _showUpdateDialog,
              child: Text("Update Gas Rate"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: _showStatement,
              child: Text("Show Statement"),
            ),
            SizedBox(height: 20),
            Text(
              "Bill Amount: ₹ ${billAmount.toStringAsFixed(2)}",
              style: TextStyle(fontSize: 18),
            )
          ],
        ),
      ),
    );
  }

  _calculateBill() {
    setState(() {
      double rawBillAmount = (currentReading - previousReading) * 2.6 * gasRate;
      billAmount = rawBillAmount; // Round up to the nearest whole rupee
    });
  }

  _showStatement() {
    final nettConsumption = currentReading - previousReading;
    final convertedToKg = nettConsumption * 2.6;
    final now = DateTime.now();
    final formattedDate = "${now.day}-${now.month}-${now.year}";
    final formattedTime = "${now.hour}:${now.minute}:${now.second}";

    showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          title: Text("User Statement"),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text("Previous Reading: $previousReading"),
              Text("Current Reading: $currentReading"),
              Text(
                  "Nett Consumption (Nm^3): ${nettConsumption.toStringAsFixed(2)}"),
              Text("Converted to Kg: ${convertedToKg.toStringAsFixed(2)}"),
              Text("Gas Rate per Kg: ₹ $gasRate"),
              Text("Bill Amount: ₹ ${billAmount.toStringAsFixed(2)}"),
              Text("Date: $formattedDate"), // Add date and time
              Text("Time: $formattedTime"), // Add time
            ],
          ),
          actions: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.of(context).pop();
              },
              child: Text("Close"),
            ),
          ],
        );
      },
    );
  }

  _showUpdateDialog() {
    showDialog(
      context: context,
      builder: (context) {
        double newGasRate = gasRate;
        return AlertDialog(
          title: Text("Update Gas Rate"),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              Text("Current Gas Rate: ₹ $gasRate"),
              TextField(
                keyboardType: TextInputType.number,
                decoration: InputDecoration(labelText: "New Gas Rate"),
                onChanged: (value) {
                  newGasRate = double.tryParse(value) ?? gasRate;
                },
              ),
            ],
          ),
          actions: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                setState(() {
                  gasRate = newGasRate;
                });
                saveGasRate(gasRate); // Save the updated gas rate
                Navigator.of(context).pop();
              },
              child: Text("Save"),
            ),
            ElevatedButton(
              style: ElevatedButton.styleFrom(
                  backgroundColor: Color.fromRGBO(255, 84, 80, 1)),
              onPressed: () {
                Navigator.of(context).pop();
              },
              child: Text("Cancel"),
            ),
          ],
        );
      },
    );
  }
}
