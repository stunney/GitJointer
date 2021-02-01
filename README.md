Problem Space to Solve

Jointer is a development utility to be utilized when dealing with large micro/many repo app project
with interconnecting dependencies and a distributed development team.

Hopefully the team is using something like gitslave or meta.

```
meta git branch my-new-feature
.....
```

Now this branch gets pushed up to the repositories that are connected to this meta repo.  Alternatively, SourceLink may solve the need for a meta repo.

Another developer on your team makes changes that affect a class library that a project you are working on is impacted by.

Wouldn't it be great if that package was automatically pulled down for you based on a common branch name?

But How??

On a branching operation, GitVersion knows what branch you are working on.
GitVersion *already* modifies projects, assemblyinfo.cs to update things like AssemblyVersion, AssemblyFileVersion, AssemblyInformationalVersion.
NuGet packages inherit some of this information (hopefully all).
Packages are pushed, and when they are, they are unstable/prerelease and carry additional information

Ex: 1.0.0-my-new-feature.1+4

Hey, that matches the branch I'm working in.  It would be best if the latest version of this package were pulled in

Jointer is intented to automatically update package references

Real-life example (2021-02-01)
Newtonsoft.Json has a beta package, 13.0.1-beta1 (https://www.nuget.org/packages/Newtonsoft.Json/13.0.1-beta1)
If we were working on a project, and Newtonsoft was in our meta repo, we could create a branch called Beta and take advantage of any new releases of their beta in our own project references
If we create a branch by any other name, we wouldn't get this


References:
--https://docs.microsoft.com/en-us/dotnet/standard/library-guidance/sourcelink
--https://www.npmjs.com/package/meta
--http://gitslave.sourceforge.net/
--https://github.com/GitTools/GitVersion
