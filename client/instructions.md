# **Flutter Installation and Setup Guide**

This guide will walk you through installing Flutter and setting up your environment for mobile and web development.

---

## **Step 1: Download and Install Flutter**

1. **Download Flutter**:

   - Visit the [Flutter website](https://flutter.dev/docs/get-started/install) and download the appropriate version for your operating system (Windows, macOS, or Linux).
2. **Extract the Flutter SDK**:

   - Extract the downloaded zip file to a location of your choice (e.g., `C:\src\flutter` on Windows).
3. **Add Flutter to PATH**:

   - To use Flutter commands from any terminal, add the Flutter `bin` directory to your system’s PATH.

   ### Windows


   - Open **Environment Variables** from the System Properties, then add `C:\src\flutter\bin` (or wherever you installed Flutter) to the PATH variable.

   ### macOS/Linux

   - Open your terminal and add the following to your shell profile (e.g., `.bashrc` or `.zshrc`):
     ``` export PATH="$PATH:/path/to/flutter/bin" ```
   - Run `source ~/.bashrc` or `source ~/.zshrc` to update your PATH.

## **Step 2: Verify Flutter Installation**

Open a terminal and run the following command to check your installation:
``` flutter doctor ```

`flutter doctor` will check your environment and list any missing dependencies. Follow the recommendations provided to install any missing components (like Xcode for macOS or Android Studio for Android development).

---

## **Step 3: Set Up an Editor (VS Code)**

1. **Install VS Code**:

   - If you haven't already, download and install [Visual Studio Code](https://code.visualstudio.com/).
2. **Install Flutter and Dart Plugins**:

   - Open VS Code, go to the Extensions view (click on the Extensions icon on the sidebar or press `Ctrl+Shift+X`).
   - Search for **Flutter** and **Dart** plugins and install them. These plugins provide features like code completion, debugging, and Flutter-specific tools.

---

## **Step 4: Create a New Flutter Project**

Navigate to your preferred directory, and run the following command to create a new Flutter project:

``` flutter create frontend ```

This will create a new Flutter project in a folder named `frontend`.

---

## **Step 5: Run Your Flutter App**

1. **Navigate to Your Project Directory**:
   ``` cd frontend ```
2. **Run the App on Different Platforms**:

   - To run on a **mobile emulator** (Android or iOS), ensure you have an emulator set up in Android Studio or Xcode, then run:
     ``` flutter run ```
   - To run as a **web app**, enable web support by running:
     ``` flutter config --enable-web flutter run -d chrome ```

---

## **Step 6: Test and Debug**

- Use the **Flutter Inspector** and **Debugger** in VS Code to debug and inspect your app.
- You can press `F5` in VS Code to start debugging, or use `flutter run` from the terminal.

---

## **Summary of Flutter Commands**

1. **Create a Flutter Project**:
   ``` flutter create frontend ```
2. **Run the App on Emulator or Browser**:
   ``` flutter run ```
3. **Enable Web Support**:
   ``` flutter config --enable-web ```
