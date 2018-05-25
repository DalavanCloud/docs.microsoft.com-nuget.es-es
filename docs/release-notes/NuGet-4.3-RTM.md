---
title: Notas de la versión de NuGet 4.3 RTM
description: Notas de la versión de NuGet 4.3 RTM incluidos problemas conocidos, correcciones de errores, características agregadas y DCR.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 08/14/2017
ms.topic: conceptual
ms.reviewer: anangaur
ms.openlocfilehash: cb44f47ef0b3bd086f0a681cb2fedc7c5afc42fa
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="nuget-43-rtm-release-notes"></a><span data-ttu-id="4bf56-103">Notas de la versión de NuGet 4.3 RTM</span><span class="sxs-lookup"><span data-stu-id="4bf56-103">NuGet 4.3 RTM Release Notes</span></span>

<span data-ttu-id="4bf56-104">[Visual Studio 2017 15.3 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) incluye NuGet 4.3 RTM que agrega compatibilidad para escenarios nuevos, como .NET Standard 2.0 y .NET Core 2.0, contiene numerosas correcciones de calidad y mejora el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="4bf56-104">[Visual Studio 2017 15.3 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) comes with NuGet 4.3 RTM which adds support for new scenarios such as .NET Standard 2.0/.NET Core 2.0, contains many quality fixes, and improves performance.</span></span> <span data-ttu-id="4bf56-105">En esta versión también se ofrecen varias mejoras como compatibilidad para Versionamiento Semántico 2.0.0, integración de MSBuild de advertencias y errores de NuGet, y mucho más.</span><span class="sxs-lookup"><span data-stu-id="4bf56-105">This release also brings several improvements like support for Semantic Versioning 2.0.0, MSBuild integration of NuGet warnings and errors, and more.</span></span>

## <a name="known-issues"></a><span data-ttu-id="4bf56-106">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="4bf56-106">Known issues</span></span>

### <a name="nuget-restore-may-treat-disabled-package-sources-as-enabled-in-some-cases"></a><span data-ttu-id="4bf56-107">La restauración de NuGet puede tratar los orígenes de paquetes deshabilitados como habilitados en algunos casos</span><span class="sxs-lookup"><span data-stu-id="4bf56-107">NuGet restore may treat disabled package sources as enabled in some cases</span></span>

#### <a name="issue"></a><span data-ttu-id="4bf56-108">Problema</span><span class="sxs-lookup"><span data-stu-id="4bf56-108">Issue</span></span>

<span data-ttu-id="4bf56-109">En las siguientes técnicas de línea de comandos de restauración se tratan los orígenes de paquetes deshabilitados como habilitados.</span><span class="sxs-lookup"><span data-stu-id="4bf56-109">The following restore command-line techniques treat disabled packages sources as enabled.</span></span> [<span data-ttu-id="4bf56-110">NuGet#5704</span><span class="sxs-lookup"><span data-stu-id="4bf56-110">NuGet#5704</span></span>](https://github.com/NuGet/Home/issues/5704)
- `msbuild /t:restore`
- <span data-ttu-id="4bf56-111">`dotnet restore` (ya sea con dotnet.exe, que se incluye con VS, o con el que se incluye con NetCore SDK 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="4bf56-111">`dotnet restore` (either with dotnet.exe that ships with VS, or the one that comes with NetCore SDK 2.0.0)</span></span>

#### <a name="workaround"></a><span data-ttu-id="4bf56-112">Solución</span><span class="sxs-lookup"><span data-stu-id="4bf56-112">Workaround</span></span>

1. <span data-ttu-id="4bf56-113">Use Visual Studio (2017 15.3 o posterior) o NuGet.exe (v4.3.0 o posterior).</span><span class="sxs-lookup"><span data-stu-id="4bf56-113">Use Visual Studio (2017 15.3 or later) or NuGet.exe (v4.3.0 or later)</span></span>
1. <span data-ttu-id="4bf56-114">Elimine el origen deshabilitado y siga usando msbuild o dotnet.exe.</span><span class="sxs-lookup"><span data-stu-id="4bf56-114">Delete your disabled source and continue to use msbuild or dotnet.exe.</span></span>
1. <span data-ttu-id="4bf56-115">Para la solución, puede usar "Clear" en NuGet.config y, después, definir los orígenes necesarios para esa solución.</span><span class="sxs-lookup"><span data-stu-id="4bf56-115">For your solution, you could use "Clear" in NuGet.config and then define the sources necessary for that solution.</span></span>

### <a name="while-using-package-manager-console-enter-key-may-not-work"></a><span data-ttu-id="4bf56-116">Mientras usa la Consola del Administrador de paquetes, puede que la tecla "Entrar" no funcione</span><span class="sxs-lookup"><span data-stu-id="4bf56-116">While using Package Manager Console, 'Enter' key may not work</span></span>

#### <a name="issue"></a><span data-ttu-id="4bf56-117">Problema</span><span class="sxs-lookup"><span data-stu-id="4bf56-117">Issue</span></span>

<span data-ttu-id="4bf56-118">En algunas ocasiones, la tecla Entrar no funciona en la Consola del Administrador de paquetes.</span><span class="sxs-lookup"><span data-stu-id="4bf56-118">Occasionally, the enter key does not work in the Package Manager Console.</span></span> <span data-ttu-id="4bf56-119">Si ve esto, revise el progreso de la corrección y proporcione información útil adicional sobre los pasos de reproducción.</span><span class="sxs-lookup"><span data-stu-id="4bf56-119">If you see this, please check out the progress on the fix, and provide any additional helpful information about your repro steps.</span></span> <span data-ttu-id="4bf56-120">[NuGet#4204](https://github.com/NuGet/Home/issues/4204) [NuGet#4570](https://github.com/NuGet/Home/issues/4570)</span><span class="sxs-lookup"><span data-stu-id="4bf56-120">[NuGet#4204](https://github.com/NuGet/Home/issues/4204) [NuGet#4570](https://github.com/NuGet/Home/issues/4570)</span></span>

#### <a name="workaround"></a><span data-ttu-id="4bf56-121">Solución</span><span class="sxs-lookup"><span data-stu-id="4bf56-121">Workaround</span></span>

<span data-ttu-id="4bf56-122">Reinicie Visual Studio y abra la consola de Administración de paquetes antes de abrir la solución.</span><span class="sxs-lookup"><span data-stu-id="4bf56-122">Restart Visual Studio and open the PMC before opening the solution.</span></span> <span data-ttu-id="4bf56-123">Como alternativa, intente eliminar el archivo `project.lock.json` y restaurarlo de nuevo.</span><span class="sxs-lookup"><span data-stu-id="4bf56-123">Alternatively, try deleting the `project.lock.json` and restoring again.</span></span>

### <a name="you-are-unable-to-view-add-or-update-dotnetclitools-using-nuget-package-manager"></a><span data-ttu-id="4bf56-124">No se puede ver, agregar ni actualizar DotNetCLITools con el Administrador de paquetes NuGet</span><span class="sxs-lookup"><span data-stu-id="4bf56-124">You are unable to view, add, or update DotNetCLITools, using Nuget Package Manager</span></span>

#### <a name="issue"></a><span data-ttu-id="4bf56-125">Problema</span><span class="sxs-lookup"><span data-stu-id="4bf56-125">Issue</span></span>

<span data-ttu-id="4bf56-126">El Administrador de paquetes de NuGet no muestra ni permite agregar o actualizar DotNetCLITools.</span><span class="sxs-lookup"><span data-stu-id="4bf56-126">NuGet Package Manager does not display and does not allow add/update of DotNetCLITools.</span></span> [<span data-ttu-id="4bf56-127">NuGet#4256</span><span class="sxs-lookup"><span data-stu-id="4bf56-127">NuGet#4256</span></span>](https://github.com/NuGet/Home/issues/4256)

#### <a name="workaround"></a><span data-ttu-id="4bf56-128">Solución</span><span class="sxs-lookup"><span data-stu-id="4bf56-128">Workaround</span></span>

<span data-ttu-id="4bf56-129">DotNetCLIToolReferences se debe editar manualmente en el archivo del proyecto.</span><span class="sxs-lookup"><span data-stu-id="4bf56-129">DotNetCLIToolReferences must be manually edited in your project file.</span></span>

### <a name="retargeting-target-framework-version-may-lead-to-incomplete-intellisense"></a><span data-ttu-id="4bf56-130">Redestinar la versión del marco de trabajo de destino puede llevar a tener una instancia de IntelliSense incompleta</span><span class="sxs-lookup"><span data-stu-id="4bf56-130">Retargeting target framework version may lead to incomplete Intellisense</span></span>

#### <a name="issue"></a><span data-ttu-id="4bf56-131">Problema</span><span class="sxs-lookup"><span data-stu-id="4bf56-131">Issue</span></span>

<span data-ttu-id="4bf56-132">Redestinar la versión del marco de trabajo de destino puede llevar a tener una instancia de IntelliSense incompleta, en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4bf56-132">Retargeting target framework version may lead to incomplete Intellisense, in Visual Studio.</span></span> <span data-ttu-id="4bf56-133">Esto sucede cuando usa PackageReferences como el formato del administrador de paquete.</span><span class="sxs-lookup"><span data-stu-id="4bf56-133">This happens when you are using PackageReferences as the package manager format.</span></span> [<span data-ttu-id="4bf56-134">NuGet#4216</span><span class="sxs-lookup"><span data-stu-id="4bf56-134">NuGet#4216</span></span>](https://github.com/NuGet/Home/issues/4216)

#### <a name="workaround"></a><span data-ttu-id="4bf56-135">Solución</span><span class="sxs-lookup"><span data-stu-id="4bf56-135">Workaround</span></span>

<span data-ttu-id="4bf56-136">Haga una restauración manual.</span><span class="sxs-lookup"><span data-stu-id="4bf56-136">Do a manual restore.</span></span>

## <a name="issues-fixed-in-nuget-43-rtm-timeframe"></a><span data-ttu-id="4bf56-137">Problemas corregidos en el período de NuGet 4.3 RTM</span><span class="sxs-lookup"><span data-stu-id="4bf56-137">Issues fixed in NuGet 4.3 RTM timeframe</span></span>

<span data-ttu-id="4bf56-138">[Notas de la versión de NuGet 4.0 RTM](../release-notes/nuget-4.0-RTM.md): enumera todos los problemas corregidos en NuGet 4.0 RTM</span><span class="sxs-lookup"><span data-stu-id="4bf56-138">[NuGet 4.0 RTM Release Notes](../release-notes/nuget-4.0-RTM.md) - Lists all the issues fixed for NuGet 4.0 RTM</span></span>

### <a name="features"></a><span data-ttu-id="4bf56-139">Características</span><span class="sxs-lookup"><span data-stu-id="4bf56-139">Features</span></span>

- <span data-ttu-id="4bf56-140">Mejorar el rendimiento de restauración de NuGet: implementar NoOp más inteligente para las restauraciones de línea de comandos y VS: [#5080](https://github.com/NuGet/Home/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="4bf56-140">Improve NuGet Restore Perf - Implement smarter NoOp for command line restores and VS - [#5080](https://github.com/NuGet/Home/issues/5080)</span></span>

- <span data-ttu-id="4bf56-141">.NET Core 2.0: la CLI de VS o Dotnet deben empezar a usar la funcionalidad existente de NuGet: carpetas FallBack: [#4939](https://github.com/NuGet/Home/issues/4939)</span><span class="sxs-lookup"><span data-stu-id="4bf56-141">NET Core 2.0: VS/Dotnet CLI should start using existing NuGet functionality: FallBack folders - [#4939](https://github.com/NuGet/Home/issues/4939)</span></span>

- <span data-ttu-id="4bf56-142">.NET Core 2.0: permitir a los usuarios ignorar advertencias de restauración específicas (o elevarlas a error): [#4898](https://github.com/NuGet/Home/issues/4898)</span><span class="sxs-lookup"><span data-stu-id="4bf56-142">NET Core 2.0: Enable users to ignore specific restore warnings (or elevate to error) - [#4898](https://github.com/NuGet/Home/issues/4898)</span></span>

- <span data-ttu-id="4bf56-143">NET Core 2.0: ensamblados localizados de la CLI: [#4896](https://github.com/NuGet/Home/issues/4896)</span><span class="sxs-lookup"><span data-stu-id="4bf56-143">NET Core 2.0: CLI localized assemblies - [#4896](https://github.com/NuGet/Home/issues/4896)</span></span>

- <span data-ttu-id="4bf56-144">NET Core 2.0: registrar todas las advertencias o errores en el archivo de recursos (incluido PackageTargetFallback): [#4895](https://github.com/NuGet/Home/issues/4895)</span><span class="sxs-lookup"><span data-stu-id="4bf56-144">NET Core 2.0: register all warnings/errors to assets file (including PackageTargetFallback) - [#4895](https://github.com/NuGet/Home/issues/4895)</span></span>

- <span data-ttu-id="4bf56-145">Habilitar la compatibilidad con TFM: NetStandard2.0, Tizen: [#4892](https://github.com/NuGet/Home/issues/4892)</span><span class="sxs-lookup"><span data-stu-id="4bf56-145">Enable TFM support: NetStandard2.0, Tizen - [#4892](https://github.com/NuGet/Home/issues/4892)</span></span>

- <span data-ttu-id="4bf56-146">Reducir el número de proyectos de NuGet.Core NuGet.Client (y, por tanto, de archivos DLL): [#2446](https://github.com/NuGet/Home/issues/2446)</span><span class="sxs-lookup"><span data-stu-id="4bf56-146">Reduce the number of NuGet.Core and NuGet.Client projects (and thus DLLs) - [#2446](https://github.com/NuGet/Home/issues/2446)</span></span>

- <span data-ttu-id="4bf56-147">Agregar la capacidad de marcar advertencias de NuGet como errores: [#2395](https://github.com/NuGet/Home/issues/2395)</span><span class="sxs-lookup"><span data-stu-id="4bf56-147">Add ability to mark nuget warnings as errors - [#2395](https://github.com/NuGet/Home/issues/2395)</span></span>

### <a name="bugs"></a><span data-ttu-id="4bf56-148">Errores</span><span class="sxs-lookup"><span data-stu-id="4bf56-148">Bugs</span></span>

- <span data-ttu-id="4bf56-149">Se produce un error de msbuild /t:pack con el parámetro "DevelopmentDependency" que no es compatible con la tarea "PackTask": [#5584](https://github.com/NuGet/Home/issues/5584)</span><span class="sxs-lookup"><span data-stu-id="4bf56-149">msbuild /t:pack fails with The "DevelopmentDependency" parameter is not supported by the "PackTask" task - [#5584](https://github.com/NuGet/Home/issues/5584)</span></span>

- <span data-ttu-id="4bf56-150">La estructura de directorios para los archivos de contenido es plana si no se agrega el separador de directorios de Windows al final de PackagePath: [#4795](https://github.com/NuGet/Home/issues/4795)</span><span class="sxs-lookup"><span data-stu-id="4bf56-150">Directory structure for content files flattened if not adding Windows directory separator at the end of PackagePath - [#4795](https://github.com/NuGet/Home/issues/4795)</span></span>

- <span data-ttu-id="4bf56-151">Los proyectos de netcore no admiten la configuración como developmentDependency: [#4694](https://github.com/NuGet/Home/issues/4694)</span><span class="sxs-lookup"><span data-stu-id="4bf56-151">netcore projects don't support setting as developmentDependency - [#4694](https://github.com/NuGet/Home/issues/4694)</span></span>

- <span data-ttu-id="4bf56-152">RestoreManagerPackage se carga de forma sincrónica lo que bloquea el subproceso de la interfaz de usuario e interbloquea VS: [#4679](https://github.com/NuGet/Home/issues/4679)</span><span class="sxs-lookup"><span data-stu-id="4bf56-152">RestoreManagerPackage being loaded synchronously which blocked UI thread and deadlocked VS - [#4679](https://github.com/NuGet/Home/issues/4679)</span></span>

- <span data-ttu-id="4bf56-153">dotnet</span><span class="sxs-lookup"><span data-stu-id="4bf56-153">dotnet</span></span>
  - <span data-ttu-id="4bf56-154">dotnetcore restore (y, por tanto, msbuild /t:restore) omite los proyectos con una dependencia de proyecto de solución explícita: [#4578](https://github.com/NuGet/Home/issues/4578)</span><span class="sxs-lookup"><span data-stu-id="4bf56-154">dotnetcore Restore (& therefore msbuild /t:restore) skips projects with an explicit solution project dependency [#4578](https://github.com/NuGet/Home/issues/4578)</span></span>

- <span data-ttu-id="4bf56-155">Si la solución tiene referencias de proyecto que hacen referencia al mismo proyecto, con distinto uso de mayúsculas y minúsculas, es posible que la restauración no funcione.</span><span class="sxs-lookup"><span data-stu-id="4bf56-155">If your solution has projectreferences that refer to the same project, with different casing, restore may not work.</span></span> <span data-ttu-id="4bf56-156">Esto afecta también a diferentes rutas de acceso relativas, sin una diferencia de uso de mayúsculas y minúsculas: [#4574](https://github.com/NuGet/Home/issues/4574)</span><span class="sxs-lookup"><span data-stu-id="4bf56-156">This also affects different relative paths, without a difference in casing - [#4574](https://github.com/NuGet/Home/issues/4574)</span></span>

- <span data-ttu-id="4bf56-157">Los archivos ejecutables restaurados desde paquetes NuGet ya no son ejecutables con .NET Core 2.0: [#4424](https://github.com/NuGet/Home/issues/4424)</span><span class="sxs-lookup"><span data-stu-id="4bf56-157">Executables restored from NuGet packages are no longer executable with .NET Core 2.0 - [#4424](https://github.com/NuGet/Home/issues/4424)</span></span>

- <span data-ttu-id="4bf56-158">NuGet.exe acepta los detalles de excepción al analizar el archivo de solución: [#4411](https://github.com/NuGet/Home/issues/4411)</span><span class="sxs-lookup"><span data-stu-id="4bf56-158">NuGet.exe swallows details of exception when parsing solution file - [#4411](https://github.com/NuGet/Home/issues/4411)</span></span>

- <span data-ttu-id="4bf56-159">Pack coloca los archivos de contenido en una ubicación incorrecta si ContentTargetFolders contiene una ruta de acceso que termina con "/" en Windows: [#4407](https://github.com/NuGet/Home/issues/4407)</span><span class="sxs-lookup"><span data-stu-id="4bf56-159">Pack puts content files in wrong location if ContentTargetFolders contains a path that ends with '/' on Windows - [#4407](https://github.com/NuGet/Home/issues/4407)</span></span>

- <span data-ttu-id="4bf56-160">No se puede restaurar una referencia DotNetCliToolReference para un paquete de herramientas destinado a netcoreapp1.1: [#4396](https://github.com/NuGet/Home/issues/4396)</span><span class="sxs-lookup"><span data-stu-id="4bf56-160">Can't restore a DotNetCliToolReference for a tools package that targets netcoreapp1.1 - [#4396](https://github.com/NuGet/Home/issues/4396)</span></span>

- <span data-ttu-id="4bf56-161">La actualización de la CLI de NuGet deja la condición anterior de versión de paquete en el archivo de proyecto (C++): [#2449](https://github.com/NuGet/Home/issues/2449)</span><span class="sxs-lookup"><span data-stu-id="4bf56-161">Nuget update CLI leaves the old package version condition in project file (C++) - [#2449](https://github.com/NuGet/Home/issues/2449)</span></span>

### <a name="dcrs"></a><span data-ttu-id="4bf56-162">DCR</span><span class="sxs-lookup"><span data-stu-id="4bf56-162">DCRs</span></span>

- <span data-ttu-id="4bf56-163">Leer DotnetCliToolTargetFramework desde la nominación de CPS: [#5397](https://github.com/NuGet/Home/issues/5397)</span><span class="sxs-lookup"><span data-stu-id="4bf56-163">Read DotnetCliToolTargetFramework from CPS nomation - [#5397](https://github.com/NuGet/Home/issues/5397)</span></span>

- <span data-ttu-id="4bf56-164">La comprobación de TPMinV debería funcionar para UWP de estilo de pj: [#4763](https://github.com/NuGet/Home/issues/4763)</span><span class="sxs-lookup"><span data-stu-id="4bf56-164">TPMinV check should work for pj style UWP - [#4763](https://github.com/NuGet/Home/issues/4763)</span></span>

- <span data-ttu-id="4bf56-165">Mejorar la descripción de la interfaz de usuario para los paquetes con referencia automática: [#4471](https://github.com/NuGet/Home/issues/4471)</span><span class="sxs-lookup"><span data-stu-id="4bf56-165">Improve UI description for AutoReferenced packages - [#4471](https://github.com/NuGet/Home/issues/4471)</span></span>

- <span data-ttu-id="4bf56-166">La restauración de NuGet selecciona activos de compilación de la sección de tiempo de ejecución:</span><span class="sxs-lookup"><span data-stu-id="4bf56-166">NuGet restore is selecting compile assets from runtime section.</span></span><span data-ttu-id="4bf56-167">[#4207](https://github.com/NuGet/Home/issues/4207)</span><span class="sxs-lookup"><span data-stu-id="4bf56-167"> - [#4207](https://github.com/NuGet/Home/issues/4207)</span></span>

- <span data-ttu-id="4bf56-168">Colocar el diagnóstico de dependencias en el archivo de bloqueo: [#1599](https://github.com/NuGet/Home/issues/1599)</span><span class="sxs-lookup"><span data-stu-id="4bf56-168">Put dependency diagnostics in the lock file - [#1599](https://github.com/NuGet/Home/issues/1599)</span></span>

## <a name="links-to-github-issues-fixed-in-43-rtm"></a><span data-ttu-id="4bf56-169">Vínculos a problemas de GitHub corregidos en 4.3 RTM</span><span class="sxs-lookup"><span data-stu-id="4bf56-169">Links to GitHub issues fixed in 4.3 RTM</span></span>

[<span data-ttu-id="4bf56-170">Lista de problemas</span><span class="sxs-lookup"><span data-stu-id="4bf56-170">Issues List</span></span>](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.3")