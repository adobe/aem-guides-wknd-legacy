# Adobe Experience Manager Best Practice Analyzer code examples

This project is intended to illustrate example conditions identified by Adobe's [Best Practice Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) (BPA) and how they can be mitigated.

This Git repository contains a project rife with bad practices, incompatible code, and configuration. The violations are used to illustrate a starting condition which can then be juxtaposed against the remediation for specific Best Practice Analyzer codes, broken out by Git branches.

## Best Practice Analyzer code branches

Adobe Best Practice Analyzer reports violations by [code](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html), and each code provides details about what the violation is, and how to resolve it.

For violations this project's `main` Git branch a corresponding Git branch, in the format `code/<bpa code>` contains the changes required for resolve that, and only that, violation.

Performing a Github.com Compare between the `main` and `code/<bpa code>` provides a clear view of the changes required to mitigate the violation.

## URC - Unsupported Run mode Configuration

This branch (`code/urc`) illustrates how to resolve URC violations.

* [URC documentation](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/urc.html)

### Update summary

This example illustrates how custom runmode-based OSGi configurations can be updated to adhere with [AEM as a Cloud Service's supported run modes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#custom-runmodes).

#### Key changes

_All OSGi configurations should be stored in a project names `ui.config` under a JCR path `/apps/<example-app>/osgiconfig/<runmode.folder>`_

* Rename run mode folder `config.staging` to the supported `config.stage` format. 
* Consolidate OSGi configurations for non-Production run modes,  , and `config.dev`, into `config.dev` which is the only non-Production run mode allowed in AEM as a Cloud Service.
  * Any OSGi configuration values that differ between the logical "QA" and "Dev" environments, must be set [using OSGi configuration environment variables](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#how-to-choose-the-appropriate-osgi-configuration-value-type).

_As part of this migration, the OSGi configuration files were converted from the legacy `xml` format defining `sling:OsgiConfig` nodes to recommended `.cfg.json` format._
