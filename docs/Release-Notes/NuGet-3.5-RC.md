---
title: "3.5 notas de la versión RC | Documentos de Microsoft"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 75a9b496-5762-48b6-922f-fdddf1369c45
description: "Notas de la versión de NuGet 3.5 RC incluidos los problemas conocidos, correcciones de errores, las funciones agregadas y dcr."
keywords: "NuGet 3.5 RC notas de la versión, correcciones de errores, problemas, conocidos agregan características, DCR"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 09d566de6f53bc0f0ddd8049143dc647f3075671
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
#<a name="35-rc-release-notes"></a><span data-ttu-id="d2315-104">3.5 notas de la versión RC</span><span class="sxs-lookup"><span data-stu-id="d2315-104">3.5 RC Release Notes</span></span>

<span data-ttu-id="d2315-105">[Notas de la versión 3.5 Beta2 NuGet](../release-notes/nuget-3.5-Beta2.md) | [NuGet 3.5-notas de la versión de RTM](../release-notes/nuget-3.5-RTM.md)</span><span class="sxs-lookup"><span data-stu-id="d2315-105">[NuGet 3.5-Beta2 Release Notes](../release-notes/nuget-3.5-Beta2.md) | [NuGet 3.5-RTM Release Notes](../release-notes/nuget-3.5-RTM.md)</span></span>

<span data-ttu-id="d2315-106">versión 3.5 se centra en la mejora de la calidad y el rendimiento de los clientes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="d2315-106">3.5 release is focused on improving quality and performance of NuGet clients.</span></span> <span data-ttu-id="d2315-107">Además, nos hemos enviado algunas de las características como compatibilidad con [carpetas reserva](https://github.com/NuGet/Home/issues/2899), [PackageType](https://github.com/NuGet/Home/issues/2476) admitir en `.nuspec` y mucho más.</span><span class="sxs-lookup"><span data-stu-id="d2315-107">In addition, we have shipped a few features like support for [Fallback folders](https://github.com/NuGet/Home/issues/2899), [PackageType](https://github.com/NuGet/Home/issues/2476) support in `.nuspec` and more.</span></span>

[<span data-ttu-id="d2315-108">Lista de problemas</span><span class="sxs-lookup"><span data-stu-id="d2315-108">Issues List</span></span>](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%223.5 RC")

## <a name="bug-fixes"></a><span data-ttu-id="d2315-109">Correcciones de errores</span><span class="sxs-lookup"><span data-stu-id="d2315-109">Bug Fixes</span></span>

* <span data-ttu-id="d2315-110">Se produce un error en la instalación y restauración de un paquete con "paquete contiene varias `.nuspec` archivos."</span><span class="sxs-lookup"><span data-stu-id="d2315-110">Install/restore of a package fails with "Package contains multiple `.nuspec` files."</span></span><span data-ttu-id="d2315-111"> - [#3231](https://github.com/NuGet/Home/issues/3231)</span><span class="sxs-lookup"><span data-stu-id="d2315-111"> - [#3231](https://github.com/NuGet/Home/issues/3231)</span></span>

* <span data-ttu-id="d2315-112">paquete de NuGet forzosamente agrega `.tt` archivos a la carpeta de contenido con independencia de qué - [#3203](https://github.com/NuGet/Home/issues/3203)</span><span class="sxs-lookup"><span data-stu-id="d2315-112">nuget pack forcefully adds `.tt` files to content folder no matter what - [#3203](https://github.com/NuGet/Home/issues/3203)</span></span>

* <span data-ttu-id="d2315-113">NuGet pack csproj (con `project.json`) se bloquea si no hay ningún packOptions y propietario en el archivo JSON: [#3180](https://github.com/NuGet/Home/issues/3180)</span><span class="sxs-lookup"><span data-stu-id="d2315-113">nuget pack csproj (with `project.json`) crashes if there are no packOptions and owner in JSON file - [#3180](https://github.com/NuGet/Home/issues/3180)</span></span>

* <span data-ttu-id="d2315-114">paquete de NuGet para `project.json` omite las etiquetas packOptions como resumen, los autores y propietarios etcetera - [#3161](https://github.com/NuGet/Home/issues/3161)</span><span class="sxs-lookup"><span data-stu-id="d2315-114">nuget pack for `project.json` ignores packOptions tags like summary, authors , owners etc - [#3161](https://github.com/NuGet/Home/issues/3161)</span></span>

* <span data-ttu-id="d2315-115">paquete de NuGet omite las dependencias en la salida `.nuspec` para `project.json`  -  [#3145](https://github.com/NuGet/Home/issues/3145)</span><span class="sxs-lookup"><span data-stu-id="d2315-115">nuget pack ignores dependencies in output `.nuspec` for `project.json` - [#3145](https://github.com/NuGet/Home/issues/3145)</span></span>

* <span data-ttu-id="d2315-116">Actualizar varios paquetes con reversión deja el proyecto en un estado interrumpido - [#3139](https://github.com/NuGet/Home/issues/3139)</span><span class="sxs-lookup"><span data-stu-id="d2315-116">Updating multiple packages with rollback leaves the project in a broken state - [#3139](https://github.com/NuGet/Home/issues/3139)</span></span>

* <span data-ttu-id="d2315-117">No se agregan archivos en cualquiera de los proyectos netstandard - [#3118](https://github.com/NuGet/Home/issues/3118)</span><span class="sxs-lookup"><span data-stu-id="d2315-117">ContentFiles under any are not added for netstandard projects - [#3118](https://github.com/NuGet/Home/issues/3118)</span></span>

* <span data-ttu-id="d2315-118">No se puede empaquetar la biblioteca de destino .NET Framework estándar correctamente - [#3108](https://github.com/NuGet/Home/issues/3108)</span><span class="sxs-lookup"><span data-stu-id="d2315-118">Cannot package library targeting .Net Standard correctly - [#3108](https://github.com/NuGet/Home/issues/3108)</span></span>

* <span data-ttu-id="d2315-119">Archivo -> Nuevo proyecto -> produce un error de proyecto de biblioteca de clases (Portable) en VS2015 y Dev15 - [#3094](https://github.com/NuGet/Home/issues/3094)</span><span class="sxs-lookup"><span data-stu-id="d2315-119">File -> New Project -> Class Library (Portable) project fails in VS2015 and Dev15 - [#3094](https://github.com/NuGet/Home/issues/3094)</span></span>

* <span data-ttu-id="d2315-120">error de nuGet - 1.0.0-* no es una cadena de versión válida - [#3070](https://github.com/NuGet/Home/issues/3070)</span><span class="sxs-lookup"><span data-stu-id="d2315-120">NuGet error - 1.0.0-* is not a valid version string - [#3070](https://github.com/NuGet/Home/issues/3070)</span></span>

* <span data-ttu-id="d2315-121">Find-Package no puede mostrar, pero funciona de Install-Package - [&#3068;](https://github.com/NuGet/Home/issues/3068)</span><span class="sxs-lookup"><span data-stu-id="d2315-121">Find-Package fails to display but Install-Package works - [#3068](https://github.com/NuGet/Home/issues/3068)</span></span>

* <span data-ttu-id="d2315-122">Error al "Install-Package jquery.validation" en dev15 - [#3061](https://github.com/NuGet/Home/issues/3061)</span><span class="sxs-lookup"><span data-stu-id="d2315-122">Error when "Install-Package jquery.validation" on dev15 - [#3061](https://github.com/NuGet/Home/issues/3061)</span></span>

* <span data-ttu-id="d2315-123">Cuando instalado VS 2015 update 3 en un VS que usa NuGet se produce el error de versión 3.5.0 - [#3053](https://github.com/NuGet/Home/issues/3053)</span><span class="sxs-lookup"><span data-stu-id="d2315-123">When installed VS 2015 update 3 on a VS that uses NuGet version 3.5.0 error occurs - [#3053](https://github.com/NuGet/Home/issues/3053)</span></span>

* <span data-ttu-id="d2315-124">Paquete de interfaz de usuario de administrador: no se muestra la nueva versión después de actualizar un paquete- [#3041](https://github.com/NuGet/Home/issues/3041)</span><span class="sxs-lookup"><span data-stu-id="d2315-124">Package manager UI: Doesn't display new version after updating a package - [#3041](https://github.com/NuGet/Home/issues/3041)</span></span>

* <span data-ttu-id="d2315-125">-ApiKey en línea de comandos de eliminación no se lectura/envía en 3.5.0-beta - [#3037](https://github.com/NuGet/Home/issues/3037)</span><span class="sxs-lookup"><span data-stu-id="d2315-125">-ApiKey on delete command line is not read/sent in 3.5.0-beta - [#3037](https://github.com/NuGet/Home/issues/3037)</span></span>

* <span data-ttu-id="d2315-126">Cadena incorrecto: no debe tener una versión estable de un paquete con una dependencia de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="d2315-126">Incorrect string: A stable release of a package should not have on a prerelease dependency.</span></span><span data-ttu-id="d2315-127"> - [#3030](https://github.com/NuGet/Home/issues/3030)</span><span class="sxs-lookup"><span data-stu-id="d2315-127"> - [#3030](https://github.com/NuGet/Home/issues/3030)</span></span>

* <span data-ttu-id="d2315-128">Excepción de NullRef creación de get de proyecto PCL (net46 y windows 10).</span><span class="sxs-lookup"><span data-stu-id="d2315-128">Creating PCL (net46 and windows 10) project get NullRef exception.</span></span><span data-ttu-id="d2315-129"> - [#3014](https://github.com/NuGet/Home/issues/3014)</span><span class="sxs-lookup"><span data-stu-id="d2315-129"> - [#3014](https://github.com/NuGet/Home/issues/3014)</span></span>

* <span data-ttu-id="d2315-130">NuGet update debe suministrar mensaje informativo cuando una versión posterior está restringida por la restricción allowedversions válidas - [#3013](https://github.com/NuGet/Home/issues/3013)</span><span class="sxs-lookup"><span data-stu-id="d2315-130">Nuget update should provide informative message when a higher version is restricted by allowedVersions constraint - [#3013](https://github.com/NuGet/Home/issues/3013)</span></span>

* <span data-ttu-id="d2315-131">Complemento de credencial se cerró con el error -1 / error Descargar paquete cuando se usan proveedores de credenciales con varios orígenes - [#2885](https://github.com/NuGet/Home/issues/2885)</span><span class="sxs-lookup"><span data-stu-id="d2315-131">Credential plugin exited with error -1 / error downloading package when using credential providers with multiple sources - [#2885](https://github.com/NuGet/Home/issues/2885)</span></span>

* <span data-ttu-id="d2315-132">paquete de NuGet - dependencia del paquete falta Newtonsoft.Json - [#2876](https://github.com/NuGet/Home/issues/2876)</span><span class="sxs-lookup"><span data-stu-id="d2315-132">nuget pack - Missing Newtonsoft.Json package dependency - [#2876](https://github.com/NuGet/Home/issues/2876)</span></span>

* <span data-ttu-id="d2315-133">Error en ExecuteSynchronizedCore en Linux/MacOS + Mono - [&#2860;](https://github.com/NuGet/Home/issues/2860)</span><span class="sxs-lookup"><span data-stu-id="d2315-133">Bug in ExecuteSynchronizedCore on Linux/MacOS + Mono - [#2860](https://github.com/NuGet/Home/issues/2860)</span></span>

* <span data-ttu-id="d2315-134">VS no es compatible con variables de entorno en repositoryPath (nuget.exe hace) - [#2763](https://github.com/NuGet/Home/issues/2763)</span><span class="sxs-lookup"><span data-stu-id="d2315-134">VS doesn't support environment variables in repositoryPath (nuget.exe does) - [#2763](https://github.com/NuGet/Home/issues/2763)</span></span>

* <span data-ttu-id="d2315-135">Solucionar problemas de accesibilidad - [#2745](https://github.com/NuGet/Home/issues/2745)</span><span class="sxs-lookup"><span data-stu-id="d2315-135">Fix Accessibility Issues - [#2745](https://github.com/NuGet/Home/issues/2745)</span></span>

* <span data-ttu-id="d2315-136">Se rechazan los marcos de trabajo portátiles con perfiles con guiones.</span><span class="sxs-lookup"><span data-stu-id="d2315-136">Portable frameworks with hyphenated profiles are rejected.</span></span><span data-ttu-id="d2315-137"> - [#2734](https://github.com/NuGet/Home/issues/2734)</span><span class="sxs-lookup"><span data-stu-id="d2315-137"> - [#2734](https://github.com/NuGet/Home/issues/2734)</span></span>

* <span data-ttu-id="d2315-138">Administrador de paquetes de NuGet debe dejar claro esa lista de opciones en los paquetes de detalle no se aplica a `project.json`  -  [#2665](https://github.com/NuGet/Home/issues/2665)</span><span class="sxs-lookup"><span data-stu-id="d2315-138">NuGet package manager should make it clear that options list in packages detail does not apply to `project.json` - [#2665](https://github.com/NuGet/Home/issues/2665)</span></span>

* <span data-ttu-id="d2315-139">Se produce un error en la actualización de NuGet 3.3.0 con '... una restricción adicional definido en packages.config evita esta operación. "</span><span class="sxs-lookup"><span data-stu-id="d2315-139">NuGet 3.3.0 update fails with 'An additional constraint ... defined in packages.config prevents this operation.'</span></span><span data-ttu-id="d2315-140"> - [#1816](https://github.com/NuGet/Home/issues/1816)</span><span class="sxs-lookup"><span data-stu-id="d2315-140"> - [#1816](https://github.com/NuGet/Home/issues/1816)</span></span>

* <span data-ttu-id="d2315-141">Instalar el paquete de un origen local que no existe produce un mensaje ficticio: [#1674](https://github.com/NuGet/Home/issues/1674)</span><span class="sxs-lookup"><span data-stu-id="d2315-141">Installing package from a local source that doesn't exist throws a bogus message - [#1674](https://github.com/NuGet/Home/issues/1674)</span></span>

* <span data-ttu-id="d2315-142">Filtro de "Actualización isponibles" muestra las actualizaciones que infringen la restricción de versión - [#1094](https://github.com/NuGet/Home/issues/1094)</span><span class="sxs-lookup"><span data-stu-id="d2315-142">"Upgrade vailable" filter shows upgrades that violate the version constraint - [#1094](https://github.com/NuGet/Home/issues/1094)</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="d2315-143">Mejoras en el rendimiento</span><span class="sxs-lookup"><span data-stu-id="d2315-143">Performance Improvements</span></span>

* <span data-ttu-id="d2315-144">Rendimiento: Mejorar el ContentModel análisis de framework de destino - [#3162](https://github.com/NuGet/Home/issues/3162)</span><span class="sxs-lookup"><span data-stu-id="d2315-144">Performance: Improve ContentModel target framework parsing - [#3162](https://github.com/NuGet/Home/issues/3162)</span></span>

* <span data-ttu-id="d2315-145">Rendimiento: Evitar lectura `runtime.json` archivos para las restauraciones que no tienen RID [#3150](https://github.com/NuGet/Home/issues/3150).</span><span class="sxs-lookup"><span data-stu-id="d2315-145">Performance: Avoid reading `runtime.json` files for restores that do not have RIDs [#3150](https://github.com/NuGet/Home/issues/3150).</span></span> <span data-ttu-id="d2315-146">En equipos con elementos de configuración, la restauración de un ejemplo de que aplicación Web ASP.NET reduce más de 15 segundos a 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="d2315-146">On CI machines, restore of a sample ASP.NET Web Application reduced from over 15 secs to 3 secs.</span></span>

* <span data-ttu-id="d2315-147">Rendimiento: Tiempo de carga Package Manager Console init.ps1 [&#2956;](https://github.com/NuGet/Home/issues/2956).</span><span class="sxs-lookup"><span data-stu-id="d2315-147">Performance: Package Manager Console init.ps1 load time [#2956](https://github.com/NuGet/Home/issues/2956).</span></span> <span data-ttu-id="d2315-148">Tiempo en Abrir PackageManagerConsole mejorado en algunos casos de 132s a 10s.</span><span class="sxs-lookup"><span data-stu-id="d2315-148">Time to open PackageManagerConsole improved in some cases from 132s to 10s.</span></span>

* <span data-ttu-id="d2315-149">Solucionar problemas de rendimiento de ReSharper en actualización de NuGet - [&#3044;](https://github.com/NuGet/Home/issues/3044): en un proyecto de ejemplo, se reduce tiempo necesario para instalar paquetes de 140s a 68s.</span><span class="sxs-lookup"><span data-stu-id="d2315-149">Solve ReSharper performance issues in NuGet Update - [#3044](https://github.com/NuGet/Home/issues/3044): On a sample project, time taken to install packages reduced from 140s to 68s.</span></span>

## <a name="dcrs"></a><span data-ttu-id="d2315-150">DCR</span><span class="sxs-lookup"><span data-stu-id="d2315-150">DCRs</span></span>

* <span data-ttu-id="d2315-151">NuGet es necesario para que los usuarios sepan que se actualizar/instalar en un tfm dotnet según PCL puede producir problemas - [#3138](https://github.com/NuGet/Home/issues/3138)</span><span class="sxs-lookup"><span data-stu-id="d2315-151">NuGet needs to let users know that upgrading/installing in a dotnet tfm based PCL could cause issues - [#3138](https://github.com/NuGet/Home/issues/3138)</span></span>

* <span data-ttu-id="d2315-152">Advertir incorrecta instalación o actualización del proyecto con tfm = "dotnet" - [#3137](https://github.com/NuGet/Home/issues/3137)</span><span class="sxs-lookup"><span data-stu-id="d2315-152">Warn bad install/upgrade for project w/ tfm="dotnet" - [#3137](https://github.com/NuGet/Home/issues/3137)</span></span>

* <span data-ttu-id="d2315-153">Agregar compatibilidad con netcoreapp11 y netstandard17 - [#2998](https://github.com/NuGet/Home/issues/2998)</span><span class="sxs-lookup"><span data-stu-id="d2315-153">Add netcoreapp11 and netstandard17 support - [#2998](https://github.com/NuGet/Home/issues/2998)</span></span>

* <span data-ttu-id="d2315-154">Imprimir el contenido del encabezado de advertencia de NuGet en la consola en nuget.exe - [#2934](https://github.com/NuGet/Home/issues/2934)</span><span class="sxs-lookup"><span data-stu-id="d2315-154">Print NuGet-Warning header contents to console in nuget.exe - [#2934](https://github.com/NuGet/Home/issues/2934)</span></span>

* <span data-ttu-id="d2315-155">Atributo de AssemblyMetadata aproveche para `.nuspec` token reemplazos - [#2851](https://github.com/NuGet/Home/issues/2851)</span><span class="sxs-lookup"><span data-stu-id="d2315-155">Leverage AssemblyMetadata attribute for `.nuspec` token replacements - [#2851](https://github.com/NuGet/Home/issues/2851)</span></span>

* <span data-ttu-id="d2315-156">Quite la propiedad bloqueada el archivo de bloqueo - [#2379](https://github.com/NuGet/Home/issues/2379)</span><span class="sxs-lookup"><span data-stu-id="d2315-156">Remove the locked property from the lock file - [#2379](https://github.com/NuGet/Home/issues/2379)</span></span>

* <span data-ttu-id="d2315-157">Los paquetes de símbolos no deben ser utilizados jamás en instalar o actualización &#2807;</span><span class="sxs-lookup"><span data-stu-id="d2315-157">Symbol packages should not ever be used in install or update #2807</span></span>

## <a name="features"></a><span data-ttu-id="d2315-158">Características</span><span class="sxs-lookup"><span data-stu-id="d2315-158">Features</span></span>

* <span data-ttu-id="d2315-159">Compatibilidad con carpetas de paquete de reserva - [#2899](https://github.com/NuGet/Home/issues/2899)</span><span class="sxs-lookup"><span data-stu-id="d2315-159">Support for fallback package folders - [#2899](https://github.com/NuGet/Home/issues/2899)</span></span>

* <span data-ttu-id="d2315-160">Diseñar e implementar una noción de tipo de paquete para admitir la herramienta paquetes - [#2476](https://github.com/NuGet/Home/issues/2476)</span><span class="sxs-lookup"><span data-stu-id="d2315-160">Design and implement a notion of package type to support tool packages - [#2476](https://github.com/NuGet/Home/issues/2476)</span></span>

* <span data-ttu-id="d2315-161">API para obtener la ruta de acceso a la carpeta paquetes global - [#2403](https://github.com/NuGet/Home/issues/2403)</span><span class="sxs-lookup"><span data-stu-id="d2315-161">API to get the path to the global packages folder - [#2403](https://github.com/NuGet/Home/issues/2403)</span></span>

* <span data-ttu-id="d2315-162">Los paquetes originales de la actualización admiten - [#1291](https://github.com/NuGet/Home/issues/1291)</span><span class="sxs-lookup"><span data-stu-id="d2315-162">Native packages update support - [#1291](https://github.com/NuGet/Home/issues/1291)</span></span>