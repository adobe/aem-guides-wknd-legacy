# Adobe Experience Manager Best Practice Analyzer code examples

This project is intended to illustrate example conditions identified by Adobe's [Best Practice Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) (BPA) and how they can be mitigated.

This Git repository contains a project rife with bad practices, incompatible code, and configuration. The violations are used to illustrate a starting condition which can then be juxtaposed against the remediation for specific Best Practice Analyzer codes, broken out by Git branches.

## Best Practice Analyzer code branches

Adobe Best Practice Analyzer reports violations by [code](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html), and each code provides details about what the violation is, and how to resolve it.

For violations this project's `main` Git branch a corresponding Git branch, in the format `code/<bpa code>` contains the changes required for resolve that, and only that, violation.

Performing a Github.com Compare between the `main` and `code/<bpa code>` provides a clear view of the changes required to mitigate the violation.

## DOPI - Deprecated Ordered Property Index

This branch (`code/dopi`) illustrates how to resolve DOPI violations.

* DOPI documentation: [https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/dopi.html](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/dopi.html)

### Update summary

This example illustrates how deprecated Ordered Property indexes can be converted to Lucene indexes, who are capable of defining ordered indexes on a JCR property.

#### Key changes

* Convert the Ordered Property index definition to an [Lucene index definition](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition).
  * Ensure the new Lucene index adheres to the [required naming conventions](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?#adding-an-index) for custom indexes.
    * Add an `indexRule` to the new Lucene index definition that covers the JCR property and marks it as orderable
* Replace the `ui.apps/src/main/content/META-INF/filter.xml` index rule for the old Ordered Property index with the path to the new Lucene index.
