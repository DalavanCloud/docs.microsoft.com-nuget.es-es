---
title: Versiones preliminares en paquetes NuGet
description: Guía para la creación de paquetes de versión preliminar
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 08/14/2017
ms.topic: conceptual
ms.openlocfilehash: a4540d29d9ca01f98ee5d1786e8a175ee0ea79f4
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="building-pre-release-packages"></a><span data-ttu-id="ce8bc-103">Crear paquetes de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="ce8bc-103">Building pre-release packages</span></span>

<span data-ttu-id="ce8bc-104">Cada vez que libere un paquete actualizado con un nuevo número de versión, NuGet la considerará la "versión estable más reciente" tal y como se muestra, por ejemplo, en la interfaz de usuario del Administrador de paquetes en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-104">Whenever you release an updated package with a new version number, NuGet considers that one as the "latest stable release" as shown, for example in the Package Manager UI within Visual Studio:</span></span>

![Interfaz de usuario del Administrador de paquetes que muestra la versión estable más reciente](media/Prerelease_01-LatestStable.png)

<span data-ttu-id="ce8bc-106">Una versión estable es aquella que se considera lo suficientemente confiable para su uso en producción.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-106">A stable release is one that's considered reliable enough to be used in production.</span></span> <span data-ttu-id="ce8bc-107">La versión estable más reciente también es la que se instalará como actualización del paquete o durante la restauración del paquete (sujeta a restricciones, tal y como se describe en [Reinstalación y actualización de paquetes](../consume-packages/reinstalling-and-updating-packages.md)).</span><span class="sxs-lookup"><span data-stu-id="ce8bc-107">The latest stable release is also the one that will be installed as a package update or during package restore (subject to constraints as described in [Reinstalling and updating packages](../consume-packages/reinstalling-and-updating-packages.md)).</span></span>

<span data-ttu-id="ce8bc-108">Para admitir el ciclo de vida de la versión de software, NuGet 1.6 y versiones posteriores permite la distribución de paquetes de versión preliminar, donde el número de versión incluye un sufijo de control de versiones semántico como `-alpha`, `-beta` o `-rc`.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-108">To support the software release lifecycle, NuGet 1.6 and later allows for the distribution of pre-release packages, where the version number includes a semantic versioning suffix such as `-alpha`, `-beta`, or `-rc`.</span></span> <span data-ttu-id="ce8bc-109">Para más información, vea [Package versioning](../reference/package-versioning.md#pre-release-versions) (Control de versiones de paquetes).</span><span class="sxs-lookup"><span data-stu-id="ce8bc-109">For more information, see [Package versioning](../reference/package-versioning.md#pre-release-versions).</span></span>

<span data-ttu-id="ce8bc-110">Puede especificar estas versiones de dos maneras:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-110">You can specify such versions in two ways:</span></span>

- <span data-ttu-id="ce8bc-111">Archivo `.nuspec`: incluya el sufijo de versión semántica en el elemento `version`:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-111">`.nuspec` file: include the semantic version suffix in the `version` element:</span></span>

    ```xml
    <version>1.0.1-alpha</version>
    ```

- <span data-ttu-id="ce8bc-112">Atributos de ensamblado: al compilar un paquete desde un proyecto de Visual Studio (`.csproj` o `.vbproj`), use `AssemblyInformationalVersionAttribute` para especificar la versión:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-112">Assembly attributes: when building a package from a Visual Studio project (`.csproj` or `.vbproj`), use the `AssemblyInformationalVersionAttribute` to specify the version:</span></span>

    ```cs
    [assembly: AssemblyInformationalVersion("1.0.1-beta")]
    ```

    <span data-ttu-id="ce8bc-113">NuGet toma este valor en lugar del que se especifica en el atributo `AssemblyVersion`, que no es compatible con el control de versiones semánticas.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-113">NuGet picks up this value instead of the one specified in the `AssemblyVersion` attribute, which does not support semantic versioning.</span></span>

<span data-ttu-id="ce8bc-114">Cuando esté listo para liberar una versión estable, quite el sufijo y el paquete tendrá prioridad sobre las demás versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-114">When you’re ready to release a stable version, just remove the suffix and the package takes precedence over any pre-release versions.</span></span> <span data-ttu-id="ce8bc-115">Una vez más, vea [Package versioning](../reference/package-versioning.md#pre-release-versions) (Control de versiones de paquetes).</span><span class="sxs-lookup"><span data-stu-id="ce8bc-115">Again, see [Package versioning](../reference/package-versioning.md#pre-release-versions).</span></span>

## <a name="installing-and-updating-pre-release-packages"></a><span data-ttu-id="ce8bc-116">Instalar y actualizar paquetes de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="ce8bc-116">Installing and updating pre-release packages</span></span>

<span data-ttu-id="ce8bc-117">De forma predeterminada, NuGet no incluye las versiones preliminares al trabajar con paquetes, pero puede cambiar este comportamiento del siguiente modo:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-117">By default, NuGet does not include pre-release versions when working with packages, but you can change this behavior as follows:</span></span>

- <span data-ttu-id="ce8bc-118">**Interfaz de usuario del Administrador de paquetes en Visual Studio**: en la interfaz de usuario **Administrar paquetes NuGet**, marque la casilla **Incluir versión preliminar**:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-118">**Package Manager UI in Visual Studio**: In the **Manage NuGet Packages** UI, check the **Include prerelease** box:</span></span>

    ![Casilla Incluir versión preliminar en Visual Studio](media/Prerelease_02-CheckPrerelease.png)

    <span data-ttu-id="ce8bc-120">Si marca o desmarca esta casilla, se actualizarán la interfaz de usuario del Administrador de paquetes y la lista de versiones disponibles que puede instalar.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-120">Setting or clearing this box will refresh the Package Manager UI and the list of available versions you can install.</span></span>

- <span data-ttu-id="ce8bc-121">**Consola del Administrador de paquetes**: use el conmutador `-IncludePrerelease` con los comandos `Find-Package`, `Get-Package`, `Install-Package`, `Sync-Package` y `Update-Package`.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-121">**Package Manager Console**: Use the `-IncludePrerelease` switch with the `Find-Package`, `Get-Package`, `Install-Package`, `Sync-Package`, and `Update-Package` commands.</span></span> <span data-ttu-id="ce8bc-122">Consulte la [referencia de PowerShell](../tools/powershell-reference.md).</span><span class="sxs-lookup"><span data-stu-id="ce8bc-122">Refer to the [PowerShell Reference](../tools/powershell-reference.md).</span></span>

- <span data-ttu-id="ce8bc-123">**CLI de NuGet**: use el conmutador `-prerelease` con los comandos `install`, `update`, `delete` y `mirror`.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-123">**NuGet CLI**: Use the `-prerelease` switch with the `install`, `update`, `delete`, and `mirror` commands.</span></span> <span data-ttu-id="ce8bc-124">Consulte la [referencia de la CLI de NuGet](../tools/nuget-exe-cli-reference.md)</span><span class="sxs-lookup"><span data-stu-id="ce8bc-124">Refer to the [NuGet CLI reference](../tools/nuget-exe-cli-reference.md)</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="ce8bc-125">Control de versiones semántico</span><span class="sxs-lookup"><span data-stu-id="ce8bc-125">Semantic versioning</span></span>

<span data-ttu-id="ce8bc-126">En [Semantic Versioning or SemVer convention](http://semver.org/spec/v1.0.0.html) (Control de versiones semántico o convención SemVer) se describe cómo usar las cadenas en los números de versión para expresar el significado del código subyacente.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-126">The [Semantic Versioning or SemVer convention](http://semver.org/spec/v1.0.0.html) describes how to utilize strings in version numbers to convey they meaning of the underlying code.</span></span>

<span data-ttu-id="ce8bc-127">En esta convención, cada versión tiene tres partes, `Major.Minor.Patch`, con el significado siguiente:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-127">In this convention, each version has three parts, `Major.Minor.Patch`, with the following meaning:</span></span>

- <span data-ttu-id="ce8bc-128">`Major`: cambios importantes</span><span class="sxs-lookup"><span data-stu-id="ce8bc-128">`Major`: Breaking changes</span></span>
- <span data-ttu-id="ce8bc-129">`Minor`: nuevas características, compatibles con versiones anteriores</span><span class="sxs-lookup"><span data-stu-id="ce8bc-129">`Minor`: New features, but backwards compatible</span></span>
- <span data-ttu-id="ce8bc-130">`Patch`: solo correcciones de errores compatibles con versiones anteriores</span><span class="sxs-lookup"><span data-stu-id="ce8bc-130">`Patch`: Backwards compatible bug fixes only</span></span>

<span data-ttu-id="ce8bc-131">Las versiones preliminares se indican anexando un guion y una cadena después del número de revisión.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-131">Pre-release versions are then denoted by appending a hyphen and a string after the patch number.</span></span> <span data-ttu-id="ce8bc-132">Desde el punto de vista técnico, puede usar *cualquier* cadena después del guion y NuGet tratará el paquete como una versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-132">Technically speaking, you can use *any *string after the hyphen and NuGet will treat the package as pre-release.</span></span> <span data-ttu-id="ce8bc-133">Luego, NuGet muestra el número de versión completo en la interfaz de usuario aplicable y deja que los consumidores interpreten el significado ellos mismos.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-133">NuGet then displays the full version number in the applicable UI, leaving consumers to interpret the meaning for themselves.</span></span>

<span data-ttu-id="ce8bc-134">Teniendo esto en cuenta, se recomienda seguir unas convenciones de nomenclatura reconocidas, como las siguientes:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-134">With this in mind, it's generally good to follow recognized naming conventions such as the following:</span></span>

- <span data-ttu-id="ce8bc-135">`-alpha`: versión alfa, que se suele usar para el trabajo en curso y la experimentación.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-135">`-alpha`: Alpha release, typically used for work-in-progress and experimentation</span></span>
- <span data-ttu-id="ce8bc-136">`-beta`: versión beta, que suele contar con todas las características de la próxima versión planificada, pero puede contener errores conocidos.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-136">`-beta`: Beta release, typically one that is feature complete for the next planned release, but may contain known bugs.</span></span>
- <span data-ttu-id="ce8bc-137">`-rc`: versión candidata para lanzamiento. Suele ser una versión potencialmente definitiva (estable) a menos que surjan errores importantes.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-137">`-rc`: Release candidate, typically a release that's potentially final (stable) unless significant bugs emerge.</span></span>

> [!Note]
> <span data-ttu-id="ce8bc-138">NuGet 4.3.0 y versiones posteriores admite [Versionamiento semántico v2.0.0](http://semver.org/spec/v2.0.0.html), que es compatible con números de versión preliminar con notación de puntos, como en `1.0.1-build.23`.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-138">NuGet 4.3.0+ supports [Semantic Versioning v2.0.0](http://semver.org/spec/v2.0.0.html), which supports pre-release numbers with dot notation, as in `1.0.1-build.23`.</span></span> <span data-ttu-id="ce8bc-139">La notación de puntos no es compatible con versiones de NuGet anteriores a 4.3.0.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-139">Dot notation is not supported with NuGet versions before 4.3.0.</span></span> <span data-ttu-id="ce8bc-140">En versiones anteriores de NuGet, podría usar un formulario como `1.0.1-build23`, pero esto siempre se considera una versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-140">In earlier versions of NuGet, you could use a form like `1.0.1-build23` but this was always considered a pre-release version.</span></span>

<span data-ttu-id="ce8bc-141">Use los sufijos que use, NuGet les dará prioridad en orden alfabético inverso:</span><span class="sxs-lookup"><span data-stu-id="ce8bc-141">Whatever suffixes you use, however, NuGet will give them precedence in reverse alphabetical order:</span></span>

    1.0.1
    1.0.1-zzz
    1.0.1-rc
    1.0.1-open
    1.0.1-beta12
    1.0.1-beta05
    1.0.1-beta
    1.0.1-alpha2
    1.0.1-alpha

<span data-ttu-id="ce8bc-142">Como se muestra, la versión sin sufijo siempre tendrá prioridad sobre las versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-142">As shown, the version without any suffix will always take precedence over pre-release versions.</span></span> <span data-ttu-id="ce8bc-143">Tenga en cuenta también que, si usa sufijos numéricos con etiquetas de versión preliminar que podrían usar números de dos dígitos (o más), use ceros iniciales como en beta01 y beta05 para asegurarse de que se ordenen correctamente cuando los números vayan aumentando.</span><span class="sxs-lookup"><span data-stu-id="ce8bc-143">Note also that if you use numerical suffixes with pre-release tags that might use double-digit numbers (or more), use leading zeroes as in beta01 and beta05 to ensure that they sort correctly when the numbers get larger.</span></span>