# Simple Project

To learn more, visit the [documentation page for Simple Project for AEM 6.3](https://helpx.adobe.com/experience-manager/kt/sites/using/simple-code-use.html).

This a content package project generated using the AEM Multimodule Lazybones template.

## Building

This project uses Maven for building. Common commands:

From the root directory, run ``mvn -PautoInstallPackage clean install`` to build the bundle and content package and install to a CQ instance.

From the bundle directory, run ``mvn -PautoInstallBundle clean install`` to build *just* the bundle and install to a CQ instance.

## Using with AEM Developer Tools for Eclipse

To use this project with the AEM Developer Tools for Eclipse, import the generated Maven projects via the Import:Maven:Existing Maven Projects wizard. Then enable the Content Package facet on the _content_ project by right-clicking on the project, then select Configure, then Convert to Content Package... In the resulting dialog, select _src/main/content_ as the Content Sync Root.

## Using with VLT

To use vlt with this project, first build and install the package to your local CQ instance as described above. Then cd to `content/src/main/content/jcr_root` and run

    vlt --credentials admin:admin checkout -f ../META-INF/vault/filter.xml --force http://localhost:4502/crx

Once the working copy is created, you can use the normal ``vlt up`` and ``vlt ci`` commands.

## Specifying CRX Host/Port

The CRX host and port can be specified on the command line with:
mvn -Dcrx.host=otherhost -Dcrx.port=5502 <goals>

## Cutting a release

To cut a release use the embedded maven-release-plugin. Since these artifacts are manually distributed (and not via public artifact repositories) the following command can be used:

    mvn -Dresume=false release:prepare release:perform -Darguments="-Dmaven.deploy.skip=true"
    
When cutting a release, ensure semantic versioning is followed and all releases end with an EVEN build number (x.x.EVEN) and the next develop SNAPSHOT ends with an ODD build numner (x.x.ODD-SNAPSHOT)
