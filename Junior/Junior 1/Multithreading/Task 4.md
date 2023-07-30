# Task 4

Task: Create a simple iOS app that displays a countdown timer on the screen. The
timer should count down from a specified amount of time (e.g. 60 seconds) and
update the UI every second.

Solution:

1. Create a new Xcode project, selecting the "Single View App" template.
2. In the Main.storyboard file, add a Label to the view controller.
3. In the view controller's class, define a property to store the remaining time
   left in the countdown.
4. Create a function to update the countdown timer every second on the main
   thread using a Timer.
5. In the viewDidLoad() method, set the initial value for the countdown timer
   and call the function to update the countdown timer every second.
6. In the function to update the countdown timer, update the remaining time left
   in the countdown and display it in the label.
7. Run the app and verify that the countdown timer updates every second and
   displays the correct remaining time left.

To make the app more performant, you can use asyncAfter() method to start the
countdown timer after delay. Additionally, you can use @synchronized blocks to
ensure thread safety when accessing shared resources, such as the remaining time
left in the countdown.
