MSSA Cohort 3
Course: ISTA-320
Lesson Plan: 04
Name: Lee Sarduy

What is the purpose of the Universal Windows Platform? What was the name of the predecessor to UWP?
The purpose of the UWP platform is building and running highly interactive applications with continuously connected, touch-driven user interfaces and support for embedded device sensors. UWP also provides one platform to build applications for the widest range of Windows 10 devices without the need to maintain separate code bases. The predecessor to UWP was WinRT.

Describe in detail how the lifetime of a UWP app differs from a traditional desktop application.
The lifetime of a UWP app is somewhat different from that of a traditional desktop app. You should design apps that can run on devices such as smartphones to suspend execution when the user switches focus to another app and then to resume running when the focus returns. This approach can help to conserve resources and battery life on a constrained device. Windows might actually decide to close a suspended app if it determines that it needs to release system resources such as memory. When the app next runs, it should be able to resume where it left off. This means that you need to be prepared to manage app state information in your code, save it to hard disk, and restore it at the appropriate juncture.

Describe two ways you can set and modify the properties of controls.
You can set and modify the properties of controls using the Properties window or by typing the equivalent XAML markup into the XAML window.

Describe the two layout schemes of UWP apps that we constructed in class.
The tabular layout was designed for devices with a wider screen (like a computer monitor). The columnar layout was designed for devices with a narrow screen (like a mobile phone).

Describe three ways you can use the Visual State Manager to adapt the layout of UWP apps.
You can use triggers that alert the Visual State Manager when some aspect (such as the height or width) of the display changes. You can define the visual state transitions performed by these triggers in the XAML markup of your app. The Visual State Manager can move controls around, display, or hide controls based on the visual state.

Describe how you can modify multiple properties of multiple controls with one document. How do you connect this modification document with your UWP application?
With UWP apps, you can define reusable styles. You can implement them as app-wide resources by creating a resource dictionary, and then they are available to all controls in all pages in an app. You can also define local resources that apply to only a single page in the XAML markup for that page. Styles are one example of a resource, but you can also add other items like an ImageBrush.