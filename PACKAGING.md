## How to ship an Akavache release

1. Bump the version in all the `nuspec` files
1. Bump the required ReactiveUI version in the `nuspec` file if necessary
1. Bump the version in all the `AssemblyInfo.cs` files
1. `msbuild Akavache.sln /p:Configuration=Release`
1. `mono ext/tools/xamarin-component.exe package component`
1. Run `nuget.exe pack` on the three .nuspec files (i.e. `Akavache`,
   `Akavache.Sqlite3`, and `Akavache.Mobile`)
1. Run `nuget.exe push` on the three new nupkg files
1. Run the MakeRelease.ps1, zip up the folders in the `Release` directory into a
   file called `Akavache x.y.z.zip` (where `x.y.z` is the version)
1. Commit everything, make a tag: `git tag -a -m "Akavache x.y.z" x.y.z HEAD;
   git push --tags`
1. Create an entry on Releases
1. Publish to the Xamarin Component Store
