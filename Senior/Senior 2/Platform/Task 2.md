# Task 2

Task: Implement a custom **`UIViewController`** transition animation that uses
the snapshot API to animate a view hierarchy.

Solution:

```swift
class CustomTransitionAnimator: NSObject, UIViewControllerAnimatedTransitioning {
    let duration: TimeInterval = 0.5

    func transitionDuration(using transitionContext: UIViewControllerContextTransitioning?) -> TimeInterval {
        return duration
    }

    func animateTransition(using transitionContext: UIViewControllerContextTransitioning) {
        guard let fromViewController = transitionContext.viewController(forKey: .from),
            let toViewController = transitionContext.viewController(forKey: .to),
            let fromView = fromViewController.view,
            let toView = toViewController.view
            else { return }

        let containerView = transitionContext.containerView
        containerView.addSubview(toView)

        // Take snapshots of the views to be animated
        let fromSnapshot = fromView.snapshotView(afterScreenUpdates: false)!
        let toSnapshot = toView.snapshotView(afterScreenUpdates: true)!

        // Set the initial positions of the snapshots
        toSnapshot.frame = CGRect(x: -toView.frame.width, y: 0, width: toView.frame.width, height: toView.frame.height)
        fromSnapshot.frame = fromView.frame

        // Add the snapshots to the container view
        containerView.addSubview(fromSnapshot)
        containerView.addSubview(toSnapshot)

        // Animate the snapshots
        UIView.animate(withDuration: duration, animations: {
            fromSnapshot.frame = CGRect(x: fromView.frame.width, y: 0, width: fromView.frame.width, height: fromView.frame.height)
            toSnapshot.frame = toView.frame
        }) { (completed) in
            // Remove the snapshots from the container view and complete the transition
            fromSnapshot.removeFromSuperview()
            toSnapshot.removeFromSuperview()
            transitionContext.completeTransition(!transitionContext.transitionWasCancelled)
        }
    }
}
```

This task requires the developer to have knowledge of view snapshots and custom
transition animations. The solution demonstrates how to use the snapshot API to
take snapshots of the views to be animated and animate them in a custom
transition animation. The **`UIViewControllerAnimatedTransitioning`** protocol
is used to implement the custom transition animation. The
**`animateTransition`** function contains the code for the custom animation,
which animates the snapshots of the views by setting their frames and animating
them using a **`UIView.animate`** block. The **`transitionDuration`** function
specifies the duration of the animation. This task demonstrates a more advanced
knowledge of iOS development and shows that the developer is capable of
implementing complex animations and transitions.
