# FsCheckAssemblyLoadFailure

This is a reproducible test case (created with the [MiniScaffold](https://github.com/TheAngryByrd/MiniScaffold)) of a problem with the published version of FsCheck 2.14.1. The file version of the assembly is reported as 1.0.0, so the assembly loader can't load it (since it's looking for 2.14.1).

To reproduce:
```
./build.cmd DotnetTest
```

To fix, change the paket.dependencies file to specify FsCheck 2.14.0, then run `dotnet tool run paket install` and re-run the tests.

