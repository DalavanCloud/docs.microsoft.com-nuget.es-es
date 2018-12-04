---
title: Notas de la versión de NuGet 4.9 RTM
description: Notas de la versión de NuGet 4.9, incluidos problemas conocidos, correcciones de errores, nuevas características y DCR.
author: karann-msft
ms.author: karann
ms.date: 11/20/2018
ms.topic: conceptual
ms.openlocfilehash: 3da1056f64b76f27afa662d879ef9f85868e2a07
ms.sourcegitcommit: 0c5a49ec6e0254a4e7a9d8bca7daeefb853c433a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2018
ms.locfileid: "52453781"
---
# <a name="nuget-49-release-notes"></a>Notas de la versión de NuGet 4.9

[Visual Studio 2017 15.9.0 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) incluye la funcionalidad NuGet 4.9.0.


También están disponibles las versiones de la línea de comandos de esta misma funcionalidad:
* NuGet.exe 4.9.x: [nuget.org/downloads](https://nuget.org/downloads)
* dotnet.exe: [.NET Core SDK 2.1.500](https://www.microsoft.com/net/download/visual-studio-sdks)


## <a name="summary-whats-new-in-490"></a>Resumen: novedades de 4.9.0

* Firma: habilitar ClientPolicies para requerir el uso de un conjunto de repositorios y autores de confianza que figura en NuGet.Config - [#6961](https://github.com/NuGet/Home/issues/6961)

* Crear archivos de ".snupkg" para contener símbolos en el paquete: mejorar la inserción para reconocer el protocolo de nuget para aceptar archivos snupkg para un servidor de símbolos - [#6878](https://github.com/NuGet/Home/issues/6878)

* Complemento de credenciales de NuGet V2 - [#6642](https://github.com/NuGet/Home/issues/6642)

* Paquetes de NuGet independientes, licencia - [#4628](https://github.com/NuGet/Home/issues/4628)

* Habilitar la participación en los metadatos "GeneratePathProperty" en un valor de PackageReference para generar una propiedad MSBuild por paquete en "Foo.Bar\1.0\" directory - [#6949](https://github.com/NuGet/Home/issues/6949)

* Mejorar la finalización correcta de las operaciones de NuGet por parte de los clientes - [#7108](https://github.com/NuGet/Home/issues/7108)

### <a name="issues-fixed-in-this-release"></a>Problemas corregidos en esta versión

* Las advertencias elevadas a errores (vía WarnAsErrors) por PackageExtraction no deben dejar nunca el paquete extraído de alrededor - [#7445](https://github.com/NuGet/Home/issues/7445)

* Los paquetes firmados incorrectamente no deben terminar en la carpeta de paquetes global - [#7423](https://github.com/NuGet/Home/issues/7423)

* La generación de redirección de enlace no debe omitir los ensamblados de fachada - [#7393](https://github.com/NuGet/Home/issues/7393)

* VersionRange Equals no compara intervalos flotantes - [#7324](https://github.com/NuGet/Home/issues/7324)

* Restaurar: regresión de rendimiento al usar la nueva pila HTTP de .NET Core 2.1 - [#7314](https://github.com/NuGet/Home/issues/7314)

* La actualización de un paquete no debe modificar la propiedad PrivateAssets de PackageReference - [#7285](https://github.com/NuGet/Home/issues/7285)

* Firma: la firma dará error si un paquete tiene demasiadas entradas de paquete (>65534) - [#7248](https://github.com/NuGet/Home/issues/7248)

* La ruta de código "dotnet nuget push" debe admitir el nuevo proveedor de credenciales - [#7233](https://github.com/NuGet/Home/issues/7233)

* Compatibilidad con la ejecución de complementos con referencia cultural invariable (como ocurre en docker) - [#7223](https://github.com/NuGet/Home/issues/7223)

* La adición de orígenes de NuGet no debe eliminar las credenciales en NuGet.config - [#7200](https://github.com/NuGet/Home/issues/7200)

* La instalación de una referencia PackageReference de tipo devDependency debe establecerse de manera predeterminada en excludeassets=compile - [#7084](https://github.com/NuGet/Home/issues/7084)

* Se ha corregido la opción de migrator para que se muestre en todos los proyectos e indique error si el proyecto no es compatible - [#6958](https://github.com/NuGet/Home/issues/6958)

* "dotnet add package" debe confirmar la restauración que realiza en el archivo de recursos - [#6928](https://github.com/NuGet/Home/issues/6928)

* Firma: mejorar los mensajes de error relacionados con la firma - [#6906](https://github.com/NuGet/Home/issues/6906)

* [Error de prueba] [zh-TW] La cadena "Package Manager Console" no se localiza en la Consola del Administrador de paquetes - [#6381](https://github.com/NuGet/Home/issues/6381)

* El mensaje de error sobre "No se puede encontrar información del proyecto" debe ser un poco más específico dentro de VS - [#5350](https://github.com/NuGet/Home/issues/5350)

* Mensaje de error poco práctico al usar incorrectamente la etiqueta de versión de nuspec del paquete de nuget - [#2714](https://github.com/NuGet/Home/issues/2714)

* DCR - firma: admitir el protocolo de NuGet: recurso RepositorySignatures/4.9.0  - [#7421](https://github.com/NuGet/Home/issues/7421)

* DCR - ahora se creará el archivo .nupkg.metadata durante la extracción del paquete; contiene "hash de contenido" - [#7283](https://github.com/NuGet/Home/issues/7283)

* DCR - omitir la comprobación de código de autenticación para complementos mientras se ejecuta en Mono - [#7222](https://github.com/NuGet/Home/issues/7222)

[Lista de todos los problemas corregidos en esta versión 4.9.0](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.9") <br>

## <a name="summary-whats-new-in-491"></a>Resumen: Novedades de 4.9.1

* Agregar compatibilidad para leer una escritura en el archivo nuget.config a través de un nuevo comando trusted-signers - [#7480](https://github.com/NuGet/Home/issues/7480)

### <a name="issues-fixed-in-this-release"></a>Problemas corregidos en esta versión

* Se ha corregido la generación del vínculo de licencia - [#7515](https://github.com/NuGet/Home/issues/7515)

* Regresión de códigos de error para validar las firmas- [#7492](https://github.com/NuGet/Home/issues/7492)

* El paquete NuGet.Build.Tasks.Pack no tiene información de licencia - [#7379](https://github.com/NuGet/Home/issues/7379)

[Lista de todos los problemas corregidos en esta versión 4.9.1](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.9.1")

## <a name="known-issues"></a>Problemas conocidos

### <a name="dotnetexenugetexe-doesnt-use-credentials-when-source-name-contains-a-whitespace---7517httpsgithubcomnugethomeissues7517"></a>dotnet.exe/nuget.exe no usa credenciales cuando el nombre de origen contiene un espacio en blanco - [#7517](https://github.com/NuGet/Home/issues/7517)

#### <a name="issue"></a>Problema
Cuando hay un espacio en blanco en el nombre de origen, nuget.exe produce un error similar a `The ' ' character, hexadecimal value 0x20, cannot be included in a name.`

#### <a name="workaround"></a>Solución
Cambie el nombre del origen para que no contenga un espacio en blanco.

### <a name="dotnet-nuget-push---interactive-gives-an-error-on-mac---7519httpsgithubcomnugethomeissues7519"></a>dotnet nuget push --interactive produce un error en un equipo Mac. - [#7519](https://github.com/NuGet/Home/issues/7519)

#### <a name="issue"></a>Problema
El argumento `--interactive` no se reenvía mediante la cli de dotnet y da como resultado el error `error: Missing value for option 'interactive'`

#### <a name="workaround"></a>Solución
Ejecute cualquier otro comando de dotnet con la opción interactiva como `dotnet restore --interactive` y autentíquese. La autenticación se puede almacenar en caché por el proveedor de credenciales. Después, ejecute `dotnet nuget push`.

### <a name="licenseacceptancewindow-and-licensefilewindow-accessibility-issues---7452httpsgithubcomnugethomeissues7452"></a>Problemas de accesibilidad de LicenseAcceptanceWindow y LicenseFileWindow - [#7452](https://github.com/NuGet/Home/issues/7452)

#### <a name="issue"></a>Problema
La ventana de aceptación de licencia y la ventana de archivo de licencia tienen problemas de accesibilidad con la navegación mediante el teclado y la narración con lector de pantalla y JAWS.

#### <a name="workaround"></a>Solución
Ninguna solución alternativa.

### <a name="packages-in-fallbackfolders-installed-by-net-core-sdk-are-custom-installed-and-fail-signature-validation---7414httpsgithubcomnugethomeissues7414"></a>Los paquetes en FallbackFolders instalados por el SDK de .NET Core de forma personalizada no superan la validación de firma. - [#7414](https://github.com/NuGet/Home/issues/7414)

#### <a name="issue"></a>Problema
Cuando se usa dotnet.exe 2.x para restaurar un proyecto que tiene como destinos múltiples netcoreapp 1.x y netcoreapp 2.x, la carpeta de reserva se trata como una fuente de archivos. Esto significa que, cuando se restaura, NuGet elegirá el paquete de la carpeta de reserva e intentará instalarlo en la carpeta de paquetes global y realizará la validación de firma habitual, lo cual produce un error.

#### <a name="workaround"></a>Solución
Deshabilite el uso de la carpeta reservada estableciendo `RestoreAdditionalProjectSources` en nothing. `<RestoreAdditionalProjectSources/>` Use esta opción con precaución, ya que provocará que muchos paquetes, que de otro modo se habrían restaurado de la carpeta de reserva, se descarguen de NuGet.org.