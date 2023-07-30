# Task 1

Task: You are given a simple iOS app with a ViewController containing a UILabel
and a UIButton. Every time the button is pressed, the text of the label should
change to a random number between 1 and 100. However, you have noticed that
after pressing the button multiple times, the app starts to slow down and
eventually crashes due to a memory issue. Your task is to identify and fix the
memory leak causing the issue.

Solution:

Step 1: Identify the cause of the memory leak The first step is to identify what
is causing the memory leak. We can use Xcode's memory graph debugger to help us
with this. Open the project in Xcode, run it on a device or simulator, and then
open the Debug Navigator. Click on the "Memory" tab to show the memory graph.
Click on the "Record" button to start recording memory allocations.

Now, press the button multiple times and notice that the memory usage keeps
increasing. Stop recording and take a look at the memory graph. You should see
that there are many instances of the ViewController that are not being released
from memory. This is a clear indication that we have a memory leak.

Step 2: Fix the memory leak The most common cause of memory leaks in iOS apps is
retaining objects in a closure or a reference cycle. In our case, we can see
that the ViewController is being retained in memory because of the closure we
have used to handle the button tap.

To fix this, we need to break the reference cycle between the closure and the
ViewController. One way to do this is to use an "unowned" reference to the
ViewController in the closure. Modify the button tap handler code as follows:

```swift
button.addTarget(self, action: #selector(buttonTapped), for: .touchUpInside)

@objc func buttonTapped() {
    let randomNumber = Int.random(in: 1...100)
    label.text = "\(randomNumber)"
}
```

By using "self" instead of a closure, we have removed the reference cycle and
prevented the memory leak.

Step 3: Test the app Run the app again and repeat the same steps. Notice that
the memory usage no longer keeps increasing, and the app does not crash due to a
memory issue. The problem has been fixed!

Note: This is just one way to fix a memory leak in this particular scenario.
There can be many other causes of memory leaks in iOS apps, and it's important
to understand how to identify and fix them. Additionally, testing the app
thoroughly after making any changes is crucial to ensure that the problem has
been resolved.
