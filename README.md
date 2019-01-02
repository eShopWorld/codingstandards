# Coding standards

this repository covers eshopworld .editorconfig and other artefacts to capture coding standards agreed upon

**What is .editorconfig file**

It is a coding standard definition file supported by many IDEs including VS. Please see https://editorconfig.org/#overview

**How to deploy .editorconfig globally**

The editor config deployment is hierarchical. the folder path is checked from bottom to top until a root definition is found. So here we can support top level definition (when placed at the root of the project hosting drive(s) e.g. C:\) and if any team wishes to override - they can maintain their own copy at the root of the project and mark it as root level definiton (root = true)

In principle, we have the option of deploying this top level global editor config via domain policy. At the moment, it requires manual deployment by the developer. This policy would take care of subsequent updates of the policy.

**Content Nuget packages - is that an option?**

We have investigated the option of distributing the editorconfig as a content only nuget package. The idea was to set the project to contain such nuget as a dependency and it would also give team members to apply latest version of the policy as it is released.

This is unfortunately not an option. MS has taken the stance of that configuration/content should not be distributed via nuget - for among others security reasons. The behavior now is that while we may place the content package into nuget, the file is physically located outside of project source. Being outside of project source breaks the editorconfig placement design and such file would not be detected and applied. 
