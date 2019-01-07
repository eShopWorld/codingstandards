# Coding standards

this repository covers eshopworld .editorconfig and other artefacts to capture coding standards agreed upon

**What is .editorconfig file**

It is a coding standard definition file supported by many IDEs including VS. Please see https://editorconfig.org/#overview

**How to Install**

Place the .editorconfig at the root of the drive where your source code resides.

Eg:
If you are using a C:\ for your source, place the .editorconfig file at C:\.editorconfig


**How to deploy .editorconfig globally**

The editor config deployment is hierarchical, such that the folder path of your source is checked from bottom to top until a definition (.editorconfig) is found. Here, we can support top level definition where the .editorconfig is placed at the root of the drive. If any team wishes to override the definition - they can maintain their own copy at the root of the project and mark it as root level definiton (root = true).

In principle, we have the option of deploying this top level global .editorconfig via Active Directory Group Policy (AD) with the ESW Domain. At the moment, .editorconfig requires manual deployment by the developer just once for initial install. Using AD would take care of updates there after of any editorconfig updates.

**Content Nuget packages - is that an option?**

We have investigated the option of distributing the editorconfig as a content only nuget package. The idea was to set the project to contain such nuget as a dependency and it would also give team members to apply latest version of the policy as it is released.

This is unfortunately not an option. MS has taken the stance of that configuration/content should not be distributed via nuget - for among others security reasons. The behavior now is that while we may place the content package into nuget, the file is physically located outside of project source. Being outside of project source breaks the editorconfig placement design and such file would not be detected and applied. 
