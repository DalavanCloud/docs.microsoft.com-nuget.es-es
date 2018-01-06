---
title: "Información general y flujo de trabajo del uso de paquetes de NuGet | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 06/06/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 3c60f920-457d-4f43-9efe-210c514e5242
description: "Información general sobre el proceso de consumo de paquetes de NuGet en un proyecto, con vínculos a otras partes específicas del proceso."
keywords: "Consumo de paquetes de NuGet, información general sobre el consumo de NuGet, flujo de trabajo de consumo de NuGet, flujo de trabajo de consumo de paquetes, información general sobre el consumo de paquetes"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c48351cb6fed0ac94bd437d9443811f46c032bd0
ms.sourcegitcommit: 122bf7ce308365ea45da018b0768f0536de76a1f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="package-consumption-workflow"></a><span data-ttu-id="b7825-104">Flujo de trabajo de consumo de paquetes</span><span class="sxs-lookup"><span data-stu-id="b7825-104">Package consumption workflow</span></span>

<span data-ttu-id="b7825-105">Entre la galería de nuget.org y las galerías de paquetes privadas que puede establecer su organización, puede encontrar decenas de miles de paquetes muy útiles para usarlos en sus aplicaciones y servicios.</span><span class="sxs-lookup"><span data-stu-id="b7825-105">Between nuget.org and private package galleries that your organization might establish, you can find tens of thousands of highly useful packages to use in your apps and services.</span></span> <span data-ttu-id="b7825-106">Pero, independientemente del origen, el consumo de un paquete sigue el mismo flujo de trabajo general que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="b7825-106">But regardless of the source, consuming a package follows the same general workflow as shown below.</span></span> <span data-ttu-id="b7825-107">Para más información, vea [Búsqueda y selección de paquetes](../consume-packages/finding-and-choosing-packages.md) y la [guía de inicio rápido de uso de un paquete](../quickstart/use-a-package.md).</span><span class="sxs-lookup"><span data-stu-id="b7825-107">For details, see [Finding and Choosing Packages](../consume-packages/finding-and-choosing-packages.md) and the [Use a Package quickstart](../quickstart/use-a-package.md).</span></span>

![Flujo para ir al origen de un paquete, buscar un paquete, instalarlo en un proyecto y agregar una instrucción Using y llamadas a la API del paquete](media/Overview-01-GeneralFlow.png)

<span data-ttu-id="b7825-109">\* _Excepto con `nuget install` de la línea de comandos, en cuyo caso es necesario editar manualmente los archivos de configuración. Consulte la [referencia del comando install](../tools/cli-ref-install.md)._</span><span class="sxs-lookup"><span data-stu-id="b7825-109">\* _Except with `nuget install` from the command-line, in which case it's necessary to edit the configuration files by hand. See the [install command reference](../tools/cli-ref-install.md)._</span></span>

<span data-ttu-id="b7825-110">NuGet recuerda la identidad y el número de versión de cada paquete instalado y los graba en `packages.config`, en el archivo del proyecto o en un archivo `project.json` de la raíz del proyecto, según el tipo de proyecto y la versión de NuGet.</span><span class="sxs-lookup"><span data-stu-id="b7825-110">NuGet remembers the identity and version number of each installed package, recording it in either `packages.config`, the project file, or a `project.json` file in your project root, depending on project type and your version of NuGet.</span></span> <span data-ttu-id="b7825-111">Con NuGet 4.0+, [el almacenamiento de las dependencias en el archivo del proyecto](../consume-packages/package-references-in-project-files.md) es el comportamiento predeterminado (salvo para los proyectos UWP que tienen como destino Windows 10 RS1).</span><span class="sxs-lookup"><span data-stu-id="b7825-111">With NuGet 4.0+, [storing dependencies in the project file](../consume-packages/package-references-in-project-files.md) is the default (except for UWP projects targeting Windows 10 RS1).</span></span> <span data-ttu-id="b7825-112">En cualquier caso, puede consultar el archivo adecuado en cualquier momento para ver la lista completa de dependencias del proyecto.</span><span class="sxs-lookup"><span data-stu-id="b7825-112">In any case, you can look in the appropriate file at any time to see the full list of dependencies for your project.</span></span>

> [!Tip]
> <span data-ttu-id="b7825-113">Es recomendable comprobar siempre la licencia de cada paquete que vaya a usar en el software.</span><span class="sxs-lookup"><span data-stu-id="b7825-113">It's prudent to always check the license for each package you intend to use in your software.</span></span> <span data-ttu-id="b7825-114">En nuget.org encontrará un vínculo de **información de licencias** a la derecha de la página de descripción de cada paquete.</span><span class="sxs-lookup"><span data-stu-id="b7825-114">On nuget.org, you'll find a **License Info** link on the right side of each package's description page.</span></span> <span data-ttu-id="b7825-115">Si un paquete no especifica los términos de licencia, póngase en contacto directamente con el propietario del paquete mediante el vínculo de **contacto con los propietarios** de la página del paquete.</span><span class="sxs-lookup"><span data-stu-id="b7825-115">If a package does not specify license terms, contact the package owner directly using the **Contact owners** link on the package page.</span></span> <span data-ttu-id="b7825-116">Microsoft no le ofrece licencia para propiedad intelectual de proveedores de paquetes de terceros ni es responsable de la información proporcionada por terceros.</span><span class="sxs-lookup"><span data-stu-id="b7825-116">Microsoft does not license any intellectual property to you from third party package providers and is not responsible for information provided by third parties.</span></span>

<span data-ttu-id="b7825-117">Al instalar paquetes, NuGet suele comprobar si el paquete ya está disponible en su memoria caché.</span><span class="sxs-lookup"><span data-stu-id="b7825-117">When installing packages, NuGet typically checks if the package is already available from its cache.</span></span> <span data-ttu-id="b7825-118">Puede borrar manualmente esta memoria caché desde la línea de comandos, tal como se describe en [Managing the NuGet cache](../consume-packages/managing-the-nuget-cache.md) (Administrar la memoria caché de NuGet).</span><span class="sxs-lookup"><span data-stu-id="b7825-118">You can manually clear this cache from the command line, as described on [Managing the NuGet cache](../consume-packages/managing-the-nuget-cache.md).</span></span>

<span data-ttu-id="b7825-119">NuGet también garantiza que las plataformas de destino admitidas por el paquete son compatibles con el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b7825-119">NuGet also makes sure that the target frameworks supported by the package are compatible with your project.</span></span> <span data-ttu-id="b7825-120">Si el paquete no contiene ensamblados compatibles, NuGet le mostrará un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="b7825-120">If the package does not contain compatible assemblies, NuGet will give you an error message.</span></span> <span data-ttu-id="b7825-121">Vea [Resolución de errores de paquetes incompatibles](dependency-resolution.md#resolving-incompatible-package-errors).</span><span class="sxs-lookup"><span data-stu-id="b7825-121">See [Resolving incompatible package errors](dependency-resolution.md#resolving-incompatible-package-errors).</span></span>

<span data-ttu-id="b7825-122">Al agregar el código del proyecto a un repositorio de origen, no se suelen incluir los paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="b7825-122">When adding project code to a source repository, you typically don't include NuGet packages.</span></span> <span data-ttu-id="b7825-123">Quienes más adelante clonan el repositorio, que incluye agentes de compilación en sistemas como Visual Studio Team Services, deben restaurar los paquetes necesarios antes de ejecutar una compilación:</span><span class="sxs-lookup"><span data-stu-id="b7825-123">Those who later clone the repository, which includes build agents on systems like Visual Studio Team Services, must restore the necessary packages prior to running a build:</span></span>

![Flujo para restaurar paquetes de NuGet clonando un repositorio y usando un comando de restauración](media/Overview-02-RestoreFlow.png)

<span data-ttu-id="b7825-125">La [restauración de paquetes](../consume-packages/package-restore.md) usa la información del archivo del proyecto, `packages.config`, `project.json` para volver a instalar todas las dependencias.</span><span class="sxs-lookup"><span data-stu-id="b7825-125">[Package Restore](../consume-packages/package-restore.md) uses the information in the project file, `packages.config`, `project.json` to reinstall all dependencies.</span></span> <span data-ttu-id="b7825-126">Tenga en cuenta que existen diferencias en el proceso implicado, como se describe en [Dependency Resolution](../consume-packages/dependency-resolution.md) (Resolución de dependencias).</span><span class="sxs-lookup"><span data-stu-id="b7825-126">Note that there are differences in the process involved, as described in [Dependency Resolution](../consume-packages/dependency-resolution.md).</span></span>

<span data-ttu-id="b7825-127">A veces es necesario volver a instalar los paquetes que ya están incluidos en un proyecto, que también podrían volver a instalar las dependencias.</span><span class="sxs-lookup"><span data-stu-id="b7825-127">Occasionally it's necessary to reinstall packages that are already included in a project, which may also reinstall dependencies.</span></span> <span data-ttu-id="b7825-128">Esto resulta sencillo usando el comando `reinstall` con la línea de comandos de NuGet o la consola del Administrador de paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="b7825-128">This is easy to do using the `reinstall` command via the NuGet command line or the NuGet Package Manager Console.</span></span> <span data-ttu-id="b7825-129">Para más información, vea [Reinstalación y actualización de paquetes](../consume-packages/reinstalling-and-updating-packages.md).</span><span class="sxs-lookup"><span data-stu-id="b7825-129">For details, see [Reinstalling and Updating Packages](../consume-packages/reinstalling-and-updating-packages.md).</span></span>

<span data-ttu-id="b7825-130">Por último, el comportamiento de NuGet se controla con los archivos de configuración `Nuget.Config`.</span><span class="sxs-lookup"><span data-stu-id="b7825-130">Finally, NuGet's behavior is driven by `Nuget.Config` configuration files.</span></span> <span data-ttu-id="b7825-131">Se pueden usar varios archivos para centralizar determinados valores a niveles diferentes, como se explica en [Configuración del comportamiento de NuGet](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="b7825-131">Multiple files can be used to centralize certain settings at different levels, as explained in [Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md).</span></span>

<span data-ttu-id="b7825-132">¡Disfrute del proceso de codificación productiva con los paquetes de NuGet!</span><span class="sxs-lookup"><span data-stu-id="b7825-132">Enjoy your productive coding with NuGet packages!</span></span>