# Task 4

Task: Explain the difference between static and dynamic libraries, and when you
would choose one over the other.

Solution:

Static libraries are linked at compile-time and the executable file includes all
the library code that the app needs. The app does not depend on any external
libraries at runtime. Dynamic libraries, on the other hand, are linked at
runtime and loaded into memory when the app is launched. The app only includes a
reference to the library, and the library is loaded separately when needed. This
means that the app is smaller in size when using dynamic libraries, as the
library is not included in the executable file.

The choice between static and dynamic libraries depends on the specific use
case. Static libraries are preferred when the app requires a specific version of
the library that should not change, or when the app needs to be completely
self-contained and not rely on external libraries. Dynamic libraries are
preferred when the app needs to share code with other apps or the system, or
when the library may need to be updated without updating the app itself. Dynamic
libraries also provide better memory management, as they can be loaded and
unloaded as needed.
