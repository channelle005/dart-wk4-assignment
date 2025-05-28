# dart-wk4-assignment

import 'dart:io';

void main() {
  print("Enter a string:");
  String? input = stdin.readLineSync();

  if (input == null || input.trim().isEmpty) {
    print("No input provided.");
    return;
  }

  // === String Manipulation ===
  String reversed = input.split('').reversed.join();
  int length = input.length;
  String upper = input.toUpperCase();
  String lower = input.toLowerCase();
  String substring = input.length >= 5 ? input.substring(0, 5) : input;

  print("\nString Manipulation:");
  print("Original: $input");
  print("Reversed: $reversed");
  print("Length: $length");
  print("Uppercase: $upper");
  print("Lowercase: $lower");
  print("Substring (first 5 chars): $substring");

  // === Collections ===

  List<String> stringList = [input, reversed];
  Set<String> uniqueWords = input.split(' ').toSet();
  Map<String, dynamic> summary = {
    "original": input,
    "reversed": reversed,
    "length": length,
    "timestamp": DateTime.now().toIso8601String()
  };

  print("\nCollections:");
  print("List: $stringList");
  print("Set of Unique Words: $uniqueWords");
  print("Map Summary: $summary");

  // === Date and Time ===
  DateTime now = DateTime.now();
  DateTime future = now.add(Duration(days: 7));
  DateTime past = now.subtract(Duration(days: 3));
  Duration difference = future.difference(past);

  print("\nDate and Time:");
  print("Now: $now");
  print("7 Days Later: $future");
  print("3 Days Ago: $past");
  print("Difference in Days: ${difference.inDays}");

  // === File Handling ===
  File file = File('log.txt');
  try {
    String logEntry = "[$now] $summary\n";
    file.writeAsStringSync(logEntry, mode: FileMode.append);
    print("\nData written to log.txt successfully.");
  } catch (e) {
    print("Error writing to file: $e");
  }

  // Reading file content
  try {
    print("\nCurrent log.txt contents:");
    String contents = file.readAsStringSync();
    print(contents);
  } catch (e) {
    print("Error reading file: $e");
  }
}
