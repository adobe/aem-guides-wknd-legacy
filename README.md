# Adobe Experience Manager Best Practice Analyzer code examples

This project is intended to illustrate example conditions identified by Adobe's [Best Practice Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) (BPA) and how they can be mitigated.

This Git repository contains a project rife with bad practices, incompatible code, and configuration. The violations are used to illustrate a starting condition which can then be juxtaposed against the remediation for specific Best Practice Analyzer codes, broken out by Git branches.

## Best Practice Analyzer code branches

Adobe Best Practice Analyzer reports violations by [code](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html), and each code provides details about what the violation is, and how to resolve it.

For violations this project's `main` Git branch a corresponding Git branch, in the format `code/<bpa code>` contains the changes required for resolve that, and only that, violation.

Performing a Github.com Compare between the `main` and `code/<bpa code>` provides a clear view of the changes required to mitigate the violation.

## OID - Oak Index Definition

This branch (`code/oid`) illustrates how to resolve OID violations.

* [OID documentation](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/oid.html)

### Update summary

This example illustrates to define the extension, or customization, of an AEM-provided index definition can be converted to Lucene indexes, which are capable of defining ordered indexes on a JCR property.

#### Key changes

* Run the [`aio aem-migration:index-converter` tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/index-converter.html) against the AEM Maven project which automatically generates AEM as a Cloud Service 
  * Move the AEM as a Cloud Service compatible index definition back into `ui.apps/src/main/content/jcr_root/_oak_index/.content.xml`, replacing the prior index definition.
* In `ui.apps/src/main/content/META-INF/filter.xml` update the filter rule to reference the new index name.
