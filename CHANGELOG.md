# Change log

This log only contains changes from version `0.6.0` and forward.


## 0.7.0

The grid keyboard view controller uses a new way to calculate the available item
space and item size for a certain number of rows and buttons per row. This means
that we can now use top and bottom content insets to create vertical margins for
grid-based keyboards.


## 0.6.2

I previously used the async image functions to quickly setup a lot of images for
"emoji" keyboards. Since I didn't use a collection view for emoji keyboards then,
all image views were created at the same time, which caused rendering delays. By
using the async image approach, image loading was moved from the main thread and
allowed individual images to appear when they were loaded instead of waiting for
all images to load before any image could be displayed.

However, `KeyboardKit` now has collection view-based keyboards, which are better
suited for the task above, since they only render the cells they need. This will
solve the image loading issues, which means that the async image extensions will
no longer be needed. I have therefore removed `UIImage+Async` and the `Threading`
folder from the library, to keep it as small as possible.


## 0.6.1

No functional changes, just README updates and improvements. The version bump is
required to give CocoaPod users the latest docs.


## 0.6.0

This is a complete rewrite of the entire library. KeyboardKit now targets iOS 11
and the code has been improved a lot. Check out the demo app to see how to setup
keyboards from now on.
