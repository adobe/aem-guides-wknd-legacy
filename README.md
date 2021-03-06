# Adobe Experience Manager Best Practice Analyzer code examples

This project is intended to illustrate example conditions identified by Adobe's [Best Practice Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) (BPA) and how they can be mitigated.

This Git repository contains a project rife with bad practices, incompatible code, and configuration. The violations are used to illustrate a starting condition which can then be juxtaposed against the remediation for specific Best Practice Analyzer codes, broken out by Git branches.

The `main` branch contains the AEM Maven project after being run through the [AEM  Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=en#refactoring-tools) tool, in order to provide a consistent, best practices Maven project structure baseline that specific BPA-code remediation branches can be easily compared against.

## Best Practice Analyzer code branches

Adobe Best Practice Analyzer reports violations by [code](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html), and each code provides details about what the violation is, and how to resolve it.

For violations this project's `main` Git branch a corresponding Git branch, in the format `code/<bpa code>` contains the changes required for resolve that, and only that, violation.

Performing a Github.com Compare between the `main` and `code/<bpa code>` provides a clear view of the changes required to mitigate the violation.
