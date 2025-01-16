# Objective-C NSInvocation and Object Lifetime Management Bug

This repository demonstrates a subtle bug related to using `NSInvocation` in Objective-C and how improper object lifetime management can lead to unexpected crashes.  The code showcases a scenario where an object is deallocated before an `NSInvocation` scheduled to operate on it is invoked.  The solution provides a safer approach to prevent this type of error.

## Bug Description
The primary issue lies in the timing of object deallocation and the execution of the `NSInvocation`. If the object being invoked upon has its retain count reduced to zero and gets deallocated before the invocation, attempting to invoke the method on that deallocated object results in a crash. This is particularly problematic in scenarios with asynchronous operations or complex object dependencies.