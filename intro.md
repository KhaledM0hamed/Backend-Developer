# 1. Introduction:
## 1.2 Semantic Versioning
<h3 align='center'><strong>Summary</strong></h3>

> Given a version number MAJOR.MINOR.PATCH
> increment the: 
> 
> 1. MAJOR version when you make incompatible API changes,
> 2. MINOR version when you add functionality in a backwards compatible manner, and
> 3. PATCH version when you make backwards compatible bug fixes.
<h3 align='center'><strong>FAQ</strong></h3>
<h4><strong>How should I deal with revisions in the 0.y.z initial development phase?</strong></h4>

> The simplest thing to do is start your initial development release at 0.1.0 and then increment the minor version for each subsequent release.
<h4><strong>How do I know when to release 1.0.0?</strong></h4>

> If your software is being used in production, it should probably already be 1.0.0. If you have a stable API on which users have come to depend, you should be 1.0.0. If you’re worrying a lot about backwards compatibility, you should probably already be 1.0.0.

<h4><strong>Doesn’t this discourage rapid development and fast iteration?
</strong></h4>

> Major version zero is all about rapid development. If you’re changing the API every day you should either still be in version 0.y.z or on a separate development branch working on the next major version.

<h4><strong>If even the tiniest backwards incompatible changes to the public API require a major version bump, won’t I end up at version 42.0.0 very rapidly?
</strong></h4>

> This is a question of responsible development and foresight. Incompatible changes should not be introduced lightly to software that has a lot of dependent code. The cost that must be incurred to upgrade can be significant. Having to bump major versions to release incompatible changes means you’ll think through the impact of your changes, and evaluate the cost/benefit ratio involved.

<h4><strong>Documenting the entire public API is too much work!
</strong></h4>

> It is your responsibility as a professional developer to properly document software that is intended for use by others. Managing software complexity is a hugely important part of keeping a project efficient, and that’s hard to do if nobody knows how to use your software, or what methods are safe to call. In the long run, Semantic Versioning, and the insistence on a well defined public API can keep everyone and everything running smoothly.

<h4><strong>What do I do if I accidentally release a backwards incompatible change as a minor version?
</strong></h4>

>As soon as you realize that you’ve broken the Semantic Versioning spec, fix the problem and release a new minor version that corrects the problem and restores backwards compatibility. Even under this circumstance, it is unacceptable to modify versioned releases. If it’s appropriate, document the offending version and inform your users of the problem so that they are aware of the offending version.

<h4><strong>What should I do if I update my own dependencies without changing the public API?
</strong></h4>

> That would be considered compatible since it does not affect the public API. Software that explicitly depends on the same dependencies as your package should have their own dependency specifications and the author will notice any conflicts. Determining whether the change is a patch level or minor level modification depends on whether you updated your dependencies in order to fix a bug or introduce new functionality. I would usually expect additional code for the latter instance, in which case it’s obviously a minor level increment.

<h4><strong>What if I inadvertently alter the public API in a way that is not compliant with the version number change (i.e. the code incorrectly introduces a major breaking change in a patch release)?
</strong></h4>

> Use your best judgment. If you have a huge audience that will be drastically impacted by changing the behavior back to what the public API intended, then it may be best to perform a major version release, even though the fix could strictly be considered a patch release. Remember, Semantic Versioning is all about conveying meaning by how the version number changes. If these changes are important to your users, use the version number to inform them.

<h4><strong>How should I handle deprecating functionality?
</strong></h4>

>Deprecating existing functionality is a normal part of software development and is often required to make forward progress. When you deprecate part of your public API, you should do two things: (1) update your documentation to let users know about the change, (2) issue a new minor release with the deprecation in place. Before you completely remove the functionality in a new major release there should be at least one minor release that contains the deprecation so that users can smoothly transition to the new API.

<h4><strong>Does SemVer have a size limit on the version string?
</strong></h4>

> No, but use good judgment. A 255 character version string is probably overkill, for example. Also, specific systems may impose their own limits on the size of the string.


<h4><strong>Is “v1.2.3” a semantic version?
</strong></h4>

> No, “v1.2.3” is not a semantic version. However, prefixing a semantic version with a “v” is a common way (in English) to indicate it is a version number. Abbreviating “version” as “v” is often seen with version control. Example: git tag v1.2.3 -m "Release version 1.2.3", in which case “v1.2.3” is a tag name and the semantic version is “1.2.3”.

