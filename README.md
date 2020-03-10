# FsCheckAssemblyLoadFailure

This is a reproducible test case (created with the [MiniScaffold](https://github.com/TheAngryByrd/MiniScaffold)) of a problem with the published version of FsCheck 2.14.1. The file version of the assembly is reported as 1.0.0, so the assembly loader can't load it (since it's looking for 2.14.1).

To reproduce, build and run the test executable in VS 2019. You should see a runtime error of the form:
```
[23:15:46 ERR] samples/testing errored in 00:00:00.4220000 <Expecto>
System.IO.FileLoadException: Could not load file or assembly 'FsCheck, Version=2.14.0.0, Culture=neutral, PublicKeyToken=null'. The located assembly's manifest definition does not match the assembly reference. (0x80131040)
File name: 'FsCheck, Version=2.14.0.0, Culture=neutral, PublicKeyToken=null'
   at Expecto.ExpectoFsCheckModule.test@90.Invoke(FsCheckConfig config)
   at Expecto.Impl.execTestAsync@692-1.Invoke(Unit unitVar)
   at Microsoft.FSharp.Control.AsyncBuilderImpl.callA@522.Invoke(AsyncParams`1 args)
```

To fix, change the paket.dependencies file to specify FsCheck 2.14.0, then run `dotnet tool run paket install` and re-run the tests.

