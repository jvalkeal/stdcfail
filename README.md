# stdcfail

Simple native compile as a sample for https://github.com/oracle/graal/issues/5901.

This is a plain boot gradle build to get easy build to demonstrate failure on windows if `-H:+AllowJRTFileSystem` is enabled via `META-INF/native-image/native-image.properties`.

There is one workflow `native.yml` which builds on linux/macos/windows. Windows build fails with error:

```
LINK : fatal error LNK1181: cannot open input file 'stdc++.lib'
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.image.NativeImageViaCC.handleLinkerFailure(NativeImageViaCC.java:204)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.image.NativeImageViaCC.runLinkerCommand(NativeImageViaCC.java:151)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.image.NativeImageViaCC.write(NativeImageViaCC.java:117)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGenerator.doRun(NativeImageGenerator.java:718)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGenerator.run(NativeImageGenerator.java:535)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner.buildImage(NativeImageGeneratorRunner.java:403)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner.build(NativeImageGeneratorRunner.java:580)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner.main(NativeImageGeneratorRunner.java:128)
Error: Image build request failed with exit status 1

FAILURE: Build failed with an exception.

```