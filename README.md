# Silent Failure of Expo Camera's takePictureAsync before Initialization

This repository demonstrates a subtle bug in Expo's Camera API where calling `takePictureAsync` before the camera is fully initialized results in a silent failure.  The error message is unhelpful, making debugging challenging.

## Problem

When using Expo's Camera component, attempting to use `takePictureAsync` too early leads to a failure without a clear error message.  This typically occurs when the method is called in the `onCameraReady` callback or before the camera has had sufficient time to load.

## Solution

The solution involves ensuring that `takePictureAsync` is only called *after* the camera is confirmed to be ready.  This can be achieved by using a state variable to track the camera's readiness and only enabling the capture button once the camera is initialized.