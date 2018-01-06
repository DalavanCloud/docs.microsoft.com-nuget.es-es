---
title: "Notas de la versión de NuGet 4.0 RC | Microsoft Docs"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/17/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: fa64825d-5908-4abe-9792-d70766d6e2ff
description: "Notas de la versión de NuGet 4.0 RC incluidos problemas conocidos, correcciones de errores, características agregadas y DCR."
keywords: "Notas de la versión de NuGet 4.0 RC, correcciones de errores, problemas, conocidos, características agregadas, DCR"
ms.reviewer: kraigb
ms.openlocfilehash: aa1c43be7ac0640bb5e118a162616acb36d44a83
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="40-rc-release-notes"></a><span data-ttu-id="6c13f-104">Notas de la versión 4.0 RC</span><span class="sxs-lookup"><span data-stu-id="6c13f-104">4.0 RC Release Notes</span></span>

[<span data-ttu-id="6c13f-105">Notas de la versión de NuGet 3.5 RTM</span><span class="sxs-lookup"><span data-stu-id="6c13f-105">NuGet 3.5 RTM Release Notes</span></span>](../release-notes/nuget-3.5-RTM.md)

<span data-ttu-id="6c13f-106">[NuGet 4.0 RC para Visual Studio 2017](http://blog.nuget.org/20161121/introducing-nuget4.0) se centra en agregar compatibilidad para escenarios de .NET Core, atender comentarios clave de los clientes y mejorar el rendimiento en una variedad de escenarios.</span><span class="sxs-lookup"><span data-stu-id="6c13f-106">[NuGet 4.0 RC for Visual Studio 2017](http://blog.nuget.org/20161121/introducing-nuget4.0) is focused on adding support for .NET Core scenarios, addressing key customer feedback and improving performance in a variety of scenarios.</span></span> <span data-ttu-id="6c13f-107">Esta versión ofrece varias mejoras, como la compatibilidad con PackageReference, comandos de NuGet como destinos de MSBuild, restauración de paquetes en segundo plano y mucho más.</span><span class="sxs-lookup"><span data-stu-id="6c13f-107">This release brings several improvements like support for PackageReference, NuGet commands as MSBuild targets, background package restore, and more.</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="6c13f-108">Correcciones de errores</span><span class="sxs-lookup"><span data-stu-id="6c13f-108">Bug Fixes</span></span>

* <span data-ttu-id="6c13f-109">Cambios de comportamiento en `dotnet pack --version-suffix foo` - [#3838](https://github.com/NuGet/Home/issues/3838)</span><span class="sxs-lookup"><span data-stu-id="6c13f-109">Behavioral changes in `dotnet pack --version-suffix foo` - [#3838](https://github.com/NuGet/Home/issues/3838)</span></span>

* <span data-ttu-id="6c13f-110">Solo se produce un error de nuget.exe restore en el equipo de VS "15": [#3834](https://github.com/NuGet/Home/issues/3834)</span><span class="sxs-lookup"><span data-stu-id="6c13f-110">nuget.exe restore on vs "15" machine only fails - [#3834](https://github.com/NuGet/Home/issues/3834)</span></span>

* <span data-ttu-id="6c13f-111">El proyecto nuevo de archivo de .NET Core debe bloquear la compilación durante la restauración: [#3780](https://github.com/NuGet/Home/issues/3780)</span><span class="sxs-lookup"><span data-stu-id="6c13f-111">.NETCore file new project should block the build during restore - [#3780](https://github.com/NuGet/Home/issues/3780)</span></span>

* <span data-ttu-id="6c13f-112">No se puede restaurar la aplicación web ASP.NET Core migrada de VS2015 a VS "15":</span><span class="sxs-lookup"><span data-stu-id="6c13f-112">ASP.NET Core web app, migrated from VS2015 to VS "15", unable to restore.</span></span><span data-ttu-id="6c13f-113">[#3773](https://github.com/NuGet/Home/issues/3773)</span><span class="sxs-lookup"><span data-stu-id="6c13f-113"> - [#3773](https://github.com/NuGet/Home/issues/3773)</span></span>

* <span data-ttu-id="6c13f-114">[Error de prueba] La IU de PM no puede desinstalar el paquete "jQuery Validation": [#3755](https://github.com/NuGet/Home/issues/3755)</span><span class="sxs-lookup"><span data-stu-id="6c13f-114">[Test Failure]Package ‘jQuery Validation’ can’t be uninstalled by PM UI - [#3755](https://github.com/NuGet/Home/issues/3755)</span></span>

* <span data-ttu-id="6c13f-115">Cuando se instala un paquete en `project.json` de UWP, también se deben restaurar los proyectos principales: [#3731](https://github.com/NuGet/Home/issues/3731)</span><span class="sxs-lookup"><span data-stu-id="6c13f-115">When a package is installed to UWP `project.json`, parent projects should also be restored - [#3731](https://github.com/NuGet/Home/issues/3731)</span></span>

* <span data-ttu-id="6c13f-116">Modificar los destinos de NuGet para registrar los orígenes del paquete con el nivel de detalle Alto en lugar de Normal: [#3719](https://github.com/NuGet/Home/issues/3719)</span><span class="sxs-lookup"><span data-stu-id="6c13f-116">Modify the NuGet targets to log the package sources as High verbosity instead of Normal - [#3719](https://github.com/NuGet/Home/issues/3719)</span></span>

* <span data-ttu-id="6c13f-117">dotnet pack3 debe incluir la documentación XML de forma predeterminada: [#3698](https://github.com/NuGet/Home/issues/3698)</span><span class="sxs-lookup"><span data-stu-id="6c13f-117">dotnet pack3 should include XML documentation by default - [#3698](https://github.com/NuGet/Home/issues/3698)</span></span>

* <span data-ttu-id="6c13f-118">Se produce un error de actualización por lotes desde la interfaz de usuario cuando primero está el código fuente sin el paquete y se selecciona el origen Todos: [#3696](https://github.com/NuGet/Home/issues/3696)</span><span class="sxs-lookup"><span data-stu-id="6c13f-118">Batch update fails from UI when source without the package is first and All source is selected - [#3696](https://github.com/NuGet/Home/issues/3696)</span></span>

* <span data-ttu-id="6c13f-119">El comando pack de NuGet no incluye todos los archivos: [#3678](https://github.com/NuGet/Home/issues/3678)</span><span class="sxs-lookup"><span data-stu-id="6c13f-119">Nuget pack command does not include all files - [#3678](https://github.com/NuGet/Home/issues/3678)</span></span>

* <span data-ttu-id="6c13f-120">Problema de memoria insuficiente: [#3661](https://github.com/NuGet/Home/issues/3661)</span><span class="sxs-lookup"><span data-stu-id="6c13f-120">OOM issue - [#3661](https://github.com/NuGet/Home/issues/3661)</span></span>

* <span data-ttu-id="6c13f-121">En la sección ProjectFileDependencyGroups del archivo de recursos se deben usar nombres de biblioteca para los proyectos: [#3611](https://github.com/NuGet/Home/issues/3611)</span><span class="sxs-lookup"><span data-stu-id="6c13f-121">ProjectFileDependencyGroups section of the assets file should use library names for projects - [#3611](https://github.com/NuGet/Home/issues/3611)</span></span>

* <span data-ttu-id="6c13f-122">"dotnet restore" y directorios recurrentes: [#3517](https://github.com/NuGet/Home/issues/3517)</span><span class="sxs-lookup"><span data-stu-id="6c13f-122">"dotnet restore" and recursing directories - [#3517](https://github.com/NuGet/Home/issues/3517)</span></span>

* <span data-ttu-id="6c13f-123">Los errores Restore3 se registran como advertencias en lugar de errores: [#3503](https://github.com/NuGet/Home/issues/3503)</span><span class="sxs-lookup"><span data-stu-id="6c13f-123">Restore3 failures are logged as warnings instead of errors - [#3503](https://github.com/NuGet/Home/issues/3503)</span></span>

* <span data-ttu-id="6c13f-124">Problema de TFS: "No se pudo encontrar [archivo] en el área de trabajo o no tiene permiso para obtener acceso a él": [#2805](https://github.com/NuGet/Home/issues/2805)</span><span class="sxs-lookup"><span data-stu-id="6c13f-124">TFS issue: "[file]not be found in your workspace, or you do not have permission to access it" - [#2805](https://github.com/NuGet/Home/issues/2805)</span></span>

* <span data-ttu-id="6c13f-125">Al escribir "nuget <packagename>" en el cuadro de búsqueda de inicio rápido de VS se mantiene el prefijo "nuget": [#2719](https://github.com/NuGet/Home/issues/2719)</span><span class="sxs-lookup"><span data-stu-id="6c13f-125">Typing "nuget <packagename>" in vs quicklaunch search box keeps "nuget " prefix - [#2719](https://github.com/NuGet/Home/issues/2719)</span></span>

* <span data-ttu-id="6c13f-126">System.Xml.XmlException: Elemento raíz no reconocido en la parte Core Properties.</span><span class="sxs-lookup"><span data-stu-id="6c13f-126">System.Xml.XmlException: Unrecognized root element in Core Properties part.</span></span> <span data-ttu-id="6c13f-127">Línea 2, posición 2:</span><span class="sxs-lookup"><span data-stu-id="6c13f-127">Line 2, position 2.</span></span><span data-ttu-id="6c13f-128">[#2718](https://github.com/NuGet/Home/issues/2718)</span><span class="sxs-lookup"><span data-stu-id="6c13f-128"> - [#2718](https://github.com/NuGet/Home/issues/2718)</span></span>

* <span data-ttu-id="6c13f-129">Ya no se compila `.nuspec` con los caracteres de escape &lt; o &gt; en campos de texto: [#2651](https://github.com/NuGet/Home/issues/2651)</span><span class="sxs-lookup"><span data-stu-id="6c13f-129">`.nuspec` with escaped &lt; or &gt; in text fields no longer builds - [#2651](https://github.com/NuGet/Home/issues/2651)</span></span>

* <span data-ttu-id="6c13f-130">La eliminación de nuget.exe no solicita credenciales (está en modo no interactivo): [#2626](https://github.com/NuGet/Home/issues/2626)</span><span class="sxs-lookup"><span data-stu-id="6c13f-130">nuget.exe delete won't prompt for credentials (it's in non-interactive mode) - [#2626](https://github.com/NuGet/Home/issues/2626)</span></span>

* <span data-ttu-id="6c13f-131">La eliminación de nuget.exe advierte sobre la clave de API para orígenes locales, aunque no tiene sentido: [#2625](https://github.com/NuGet/Home/issues/2625)</span><span class="sxs-lookup"><span data-stu-id="6c13f-131">nuget.exe delete warns about API Key for local sources, even though it makes no sense - [#2625](https://github.com/NuGet/Home/issues/2625)</span></span>

* <span data-ttu-id="6c13f-132">Experiencia de error deficiente al instalar el paquete -pre de EF: [#2566](https://github.com/NuGet/Home/issues/2566)</span><span class="sxs-lookup"><span data-stu-id="6c13f-132">Error experience poor when installing EF -pre package - [#2566](https://github.com/NuGet/Home/issues/2566)</span></span>

* <span data-ttu-id="6c13f-133">Visual Studio bloqueó el intento después de cambiar la selección en el Administrador de paquetes: [#2551](https://github.com/NuGet/Home/issues/2551)</span><span class="sxs-lookup"><span data-stu-id="6c13f-133">Visual Studio crashed attempting after changing selection in Package Manager - [#2551](https://github.com/NuGet/Home/issues/2551)</span></span>

* <span data-ttu-id="6c13f-134">La restauración de dotnet realiza búsquedas de identificador que distinguen mayúsculas de minúsculas en repositorios locales de lista plana cuando se usan versiones flotantes: [#2516](https://github.com/NuGet/Home/issues/2516)</span><span class="sxs-lookup"><span data-stu-id="6c13f-134">Dotnet restore performs case sensitive Id lookups on flat-list local repositories when floating versions are used - [#2516](https://github.com/NuGet/Home/issues/2516)</span></span>

* <span data-ttu-id="6c13f-135">La eliminación con nuget.exe se interrumpe para la fuente de V2: [#2509](https://github.com/NuGet/Home/issues/2509)</span><span class="sxs-lookup"><span data-stu-id="6c13f-135">nuget.exe delete is broken for V2 feed - [#2509](https://github.com/NuGet/Home/issues/2509)</span></span>

* <span data-ttu-id="6c13f-136">El tiempo de espera de inserción de nuget.exe necesita un mensaje de error mejor: [#2503](https://github.com/NuGet/Home/issues/2503)</span><span class="sxs-lookup"><span data-stu-id="6c13f-136">nuget.exe push timeout needs a better error message - [#2503](https://github.com/NuGet/Home/issues/2503)</span></span>

* <span data-ttu-id="6c13f-137">Se produce un error en modo silencioso en la restauración de herramienta sin las importaciones adecuadas:</span><span class="sxs-lookup"><span data-stu-id="6c13f-137">Tool restore without proper imports silently fails.</span></span><span data-ttu-id="6c13f-138">[#2462](https://github.com/NuGet/Home/issues/2462)</span><span class="sxs-lookup"><span data-stu-id="6c13f-138"> - [#2462](https://github.com/NuGet/Home/issues/2462)</span></span>

* <span data-ttu-id="6c13f-139">NuGet le pide que escriba las credenciales cuando hay una fuente privada incluso cuando se instala desde nuget.org: [#2346](https://github.com/NuGet/Home/issues/2346)</span><span class="sxs-lookup"><span data-stu-id="6c13f-139">NuGet prompts to enter credentials when there is a private feed even when installing from nuget.org - [#2346](https://github.com/NuGet/Home/issues/2346)</span></span>

* <span data-ttu-id="6c13f-140">El paquete ApplicationInsights 2.0 aparece pero todavía no existe: [#2317](https://github.com/NuGet/Home/issues/2317)</span><span class="sxs-lookup"><span data-stu-id="6c13f-140">ApplicationInsights 2.0 package is listed but doesn't exist yet - [#2317](https://github.com/NuGet/Home/issues/2317)</span></span>

* <span data-ttu-id="6c13f-141">Retraso de la interfaz de usuario en la rama 5 de VS "15" Preview: [#3500](https://github.com/NuGet/Home/issues/3500)</span><span class="sxs-lookup"><span data-stu-id="6c13f-141">UIDelay in VS "15" preview 5 branch - [#3500](https://github.com/NuGet/Home/issues/3500)</span></span>

* <span data-ttu-id="6c13f-142">Falta el primer evento OnBuild para la restauración durante la compilación para UWP: [#3489](https://github.com/NuGet/Home/issues/3489)</span><span class="sxs-lookup"><span data-stu-id="6c13f-142">First OnBuild event is missed for Restore during Build for UWP - [#3489](https://github.com/NuGet/Home/issues/3489)</span></span>

* <span data-ttu-id="6c13f-143">¿PowerShell5 interrumpe la instalación de EntityFramework?:</span><span class="sxs-lookup"><span data-stu-id="6c13f-143">PowerShell5 breaks EntityFramework install?</span></span><span data-ttu-id="6c13f-144">[#3312](https://github.com/NuGet/Home/issues/3312)</span><span class="sxs-lookup"><span data-stu-id="6c13f-144"> - [#3312](https://github.com/NuGet/Home/issues/3312)</span></span>

* <span data-ttu-id="6c13f-145">Agregar origen a un registro detallado (recomendado para 3.5): [#3294](https://github.com/NuGet/Home/issues/3294)</span><span class="sxs-lookup"><span data-stu-id="6c13f-145">Add source to detailed logging (consider for 3.5) - [#3294](https://github.com/NuGet/Home/issues/3294)</span></span>

* <span data-ttu-id="6c13f-146">El parámetro NoCache no se respeta en la versión de cliente de NuGet 3.4 y posteriores: [#3074](https://github.com/NuGet/Home/issues/3074)</span><span class="sxs-lookup"><span data-stu-id="6c13f-146">NoCache parameter not honored in nuget client version 3.4+ - [#3074](https://github.com/NuGet/Home/issues/3074)</span></span>

* <span data-ttu-id="6c13f-147">Cuando un proveedor de credenciales no se puede cargar en VS, no interrumpa NuGet: [#2422](https://github.com/NuGet/Home/issues/2422)</span><span class="sxs-lookup"><span data-stu-id="6c13f-147">When a credential provider fails to load in VS, don't break NuGet - [#2422](https://github.com/NuGet/Home/issues/2422)</span></span>


## <a name="features"></a><span data-ttu-id="6c13f-148">Características</span><span class="sxs-lookup"><span data-stu-id="6c13f-148">Features</span></span>

* <span data-ttu-id="6c13f-149">Configurar CI para ejecutar x86: [#3868](https://github.com/NuGet/Home/issues/3868)</span><span class="sxs-lookup"><span data-stu-id="6c13f-149">Set up CI to run x86 - [#3868](https://github.com/NuGet/Home/issues/3868)</span></span>

* <span data-ttu-id="6c13f-150">Restauración automática 3/3: interfaz de usuario sin bloqueo: [#3658](https://github.com/NuGet/Home/issues/3658)</span><span class="sxs-lookup"><span data-stu-id="6c13f-150">Auto Restore 3/3: non blocking UI - [#3658](https://github.com/NuGet/Home/issues/3658)</span></span>

* <span data-ttu-id="6c13f-151">Restauración automática 2/3: restauración en nominación en segundo plano: [#3657](https://github.com/NuGet/Home/issues/3657)</span><span class="sxs-lookup"><span data-stu-id="6c13f-151">Auto Restore 2/3: background restore on nomination - [#3657](https://github.com/NuGet/Home/issues/3657)</span></span>

* <span data-ttu-id="6c13f-152">Restaurar referencias de proyecto para que coincidan con el comportamiento de compilación (recurrente): [#3615](https://github.com/NuGet/Home/issues/3615)</span><span class="sxs-lookup"><span data-stu-id="6c13f-152">Restore project refs to match build behavior (recurse) - [#3615](https://github.com/NuGet/Home/issues/3615)</span></span>

* <span data-ttu-id="6c13f-153">Compatibilidad con DPL en VS "15" (minbar): [#3614](https://github.com/NuGet/Home/issues/3614)</span><span class="sxs-lookup"><span data-stu-id="6c13f-153">DPL support in VS "15" - minbar - [#3614](https://github.com/NuGet/Home/issues/3614)</span></span>

* <span data-ttu-id="6c13f-154">Mover el archivo de configuración a Archivos de programa: [#3613](https://github.com/NuGet/Home/issues/3613)</span><span class="sxs-lookup"><span data-stu-id="6c13f-154">Move settings file to Program Files - [#3613](https://github.com/NuGet/Home/issues/3613)</span></span>

* <span data-ttu-id="6c13f-155">Las propiedades y destinos de restauración necesitan compatibilidad con la participación entre orígenes: [#3496](https://github.com/NuGet/Home/issues/3496)</span><span class="sxs-lookup"><span data-stu-id="6c13f-155">Generated restore props and targets need cross-targeting participation support - [#3496](https://github.com/NuGet/Home/issues/3496)</span></span>

* <span data-ttu-id="6c13f-156">Compatibilidad con la restauración de NuGet para PackageTargetFallback (antes conocida como Imports): [#3494](https://github.com/NuGet/Home/issues/3494)</span><span class="sxs-lookup"><span data-stu-id="6c13f-156">NuGet Restore support for PackageTargetFallback (f.k.a Imports) - [#3494](https://github.com/NuGet/Home/issues/3494)</span></span>

* <span data-ttu-id="6c13f-157">Implementación de ToolsRef: [#3472](https://github.com/NuGet/Home/issues/3472)</span><span class="sxs-lookup"><span data-stu-id="6c13f-157">ToolsRef implementation - [#3472](https://github.com/NuGet/Home/issues/3472)</span></span>

* <span data-ttu-id="6c13f-158">Restore3 para un RID: [#3465](https://github.com/NuGet/Home/issues/3465)</span><span class="sxs-lookup"><span data-stu-id="6c13f-158">Restore3 for a RID - [#3465](https://github.com/NuGet/Home/issues/3465)</span></span>

* <span data-ttu-id="6c13f-159">Interfaz de usuario de NuGet para admitir la adición, eliminación y actualización de PackageRef: [#3457](https://github.com/NuGet/Home/issues/3457)</span><span class="sxs-lookup"><span data-stu-id="6c13f-159">NuGet UI to support Add/Remove/Update of PackageRefs - [#3457](https://github.com/NuGet/Home/issues/3457)</span></span>

* <span data-ttu-id="6c13f-160">Restauración automática 1/3: Implementación de la API de nominación a través del almacenamiento en caché de la información de restauración del proyecto: [#3456](https://github.com/NuGet/Home/issues/3456)</span><span class="sxs-lookup"><span data-stu-id="6c13f-160">Auto Restore 1/3: Implemenation of Nomination API via Caching Project Restore Info - [#3456](https://github.com/NuGet/Home/issues/3456)</span></span>

* <span data-ttu-id="6c13f-161">[0] Tarea y destinos de restauración de NuGet: [#2994](https://github.com/NuGet/Home/issues/2994)</span><span class="sxs-lookup"><span data-stu-id="6c13f-161">[0] NuGet Restore Task & Targets - [#2994](https://github.com/NuGet/Home/issues/2994)</span></span>

* <span data-ttu-id="6c13f-162">[1] Habilitar la restauración en el nivel de solución en MSBuild: [#2993](https://github.com/NuGet/Home/issues/2993)</span><span class="sxs-lookup"><span data-stu-id="6c13f-162">[1] Enable Solution level restore in MSBuild - [#2993](https://github.com/NuGet/Home/issues/2993)</span></span>

* <span data-ttu-id="6c13f-163">Admitir la extensibilidad pública de proveedores de credenciales en Visual Studio: [#2909](https://github.com/NuGet/Home/issues/2909)</span><span class="sxs-lookup"><span data-stu-id="6c13f-163">Support credential provider public extensibility in Visual Studio - [#2909](https://github.com/NuGet/Home/issues/2909)</span></span>

* <span data-ttu-id="6c13f-164">Restauración de nuget recursiva: [#2533](https://github.com/NuGet/Home/issues/2533)</span><span class="sxs-lookup"><span data-stu-id="6c13f-164">Recursive nuget restore - [#2533](https://github.com/NuGet/Home/issues/2533)</span></span>

* <span data-ttu-id="6c13f-165">No se puede cargar Microsoft.TeamFoundation.Client en dev15, es necesario actualizar Microsoft.TeamFoundation.Client a la versión 15.0 para VS "15" Preview: [#2392](https://github.com/NuGet/Home/issues/2392)</span><span class="sxs-lookup"><span data-stu-id="6c13f-165">Can't load Microsoft.TeamFoundation.Client on dev15, need to update Microsoft.TeamFoundation.Client version to 15.0 for VS "15" Preview - [#2392](https://github.com/NuGet/Home/issues/2392)</span></span>

* <span data-ttu-id="6c13f-166">No se puede instalar el paquete de C++ en el proyecto de UWP de C++ en VS "15" Preview: [#2369](https://github.com/NuGet/Home/issues/2369)</span><span class="sxs-lookup"><span data-stu-id="6c13f-166">Unable to install C++ package to C++ UWP project in VS "15" Preview - [#2369](https://github.com/NuGet/Home/issues/2369)</span></span>

* <span data-ttu-id="6c13f-167">Nupkg tiene que admitir la carpeta \buildCrossTargeting\ e importar `.targets` / `.props` para el ámbito "multidestino" de MSBuild:</span><span class="sxs-lookup"><span data-stu-id="6c13f-167">Nupkg needs to support \buildCrossTargeting\ folder - and import `.targets` / `.props` for "crosstargeting" MSBuild scope.</span></span><span data-ttu-id="6c13f-168">[#3499](https://github.com/NuGet/Home/issues/3499)</span><span class="sxs-lookup"><span data-stu-id="6c13f-168"> - [#3499](https://github.com/NuGet/Home/issues/3499)</span></span>

* <span data-ttu-id="6c13f-169">Diseño de ToolsReference: [#3462](https://github.com/NuGet/Home/issues/3462)</span><span class="sxs-lookup"><span data-stu-id="6c13f-169">ToolsReference Design - [#3462](https://github.com/NuGet/Home/issues/3462)</span></span>

* <span data-ttu-id="6c13f-170">Corregir la interfaz de usuario de NuGet para admitir la restauración con PackageReferences en `.csproj`: [#3455](https://github.com/NuGet/Home/issues/3455)</span><span class="sxs-lookup"><span data-stu-id="6c13f-170">Fix NuGet UI to support restore w/ PackageReferences in `.csproj` - [#3455](https://github.com/NuGet/Home/issues/3455)</span></span>

* <span data-ttu-id="6c13f-171">Adición del botón Borrar caché a las opciones del Administrador de paquetes de VS: [#3289](https://github.com/NuGet/Home/issues/3289)</span><span class="sxs-lookup"><span data-stu-id="6c13f-171">Adding clear cache button to VS package manager settings - [#3289](https://github.com/NuGet/Home/issues/3289)</span></span>

## <a name="dcrs"></a><span data-ttu-id="6c13f-172">DCR</span><span class="sxs-lookup"><span data-stu-id="6c13f-172">DCRs</span></span>

* <span data-ttu-id="6c13f-173">La restauración de la solución debe bloquearse mientras se está produciendo la restauración automática:</span><span class="sxs-lookup"><span data-stu-id="6c13f-173">Solution Restore should be blocked while auto restore is happening.</span></span><span data-ttu-id="6c13f-174">[#3797](https://github.com/NuGet/Home/issues/3797)</span><span class="sxs-lookup"><span data-stu-id="6c13f-174"> - [#3797](https://github.com/NuGet/Home/issues/3797)</span></span>

* <span data-ttu-id="6c13f-175">La instalación de NetCore desde la interfaz de usuario del Administrador de paquetes NuGet se instala en todos los TFM, en lugar de los que admite el paquete: [#3721](https://github.com/NuGet/Home/issues/3721)</span><span class="sxs-lookup"><span data-stu-id="6c13f-175">NetCore install from NuGet Package Manager UI installs to every TFM , instead of ones that the package supports - [#3721](https://github.com/NuGet/Home/issues/3721)</span></span>

* <span data-ttu-id="6c13f-176">La API Nomination de restauración también debe admitir DotNetCliToolsReferences:</span><span class="sxs-lookup"><span data-stu-id="6c13f-176">Restore nominator API needs to support DotNetCliToolsReferences too.</span></span><span data-ttu-id="6c13f-177">[#3702](https://github.com/NuGet/Home/issues/3702)</span><span class="sxs-lookup"><span data-stu-id="6c13f-177"> - [#3702](https://github.com/NuGet/Home/issues/3702)</span></span>

* <span data-ttu-id="6c13f-178">Marcar vsix de VS "15" como systemcomponent: [#3700](https://github.com/NuGet/Home/issues/3700)</span><span class="sxs-lookup"><span data-stu-id="6c13f-178">Mark our VS "15" vsix as a systemcomponent - [#3700](https://github.com/NuGet/Home/issues/3700)</span></span>

* <span data-ttu-id="6c13f-179">Migrar desde MS.VS.Services.Client a MS.VS.Services.Client.Interactive: [#3670](https://github.com/NuGet/Home/issues/3670)</span><span class="sxs-lookup"><span data-stu-id="6c13f-179">Migrate from referencing MS.VS.Services.Client to MS.VS.Services.Client.Interactive - [#3670](https://github.com/NuGet/Home/issues/3670)</span></span>

* <span data-ttu-id="6c13f-180">La restauración debe respetar $(RestoreLegacyPackagesDirectory) al nivel de proyecto: [#3618](https://github.com/NuGet/Home/issues/3618)</span><span class="sxs-lookup"><span data-stu-id="6c13f-180">$(RestoreLegacyPackagesDirectory) should be respected at a project level by restore - [#3618](https://github.com/NuGet/Home/issues/3618)</span></span>

* <span data-ttu-id="6c13f-181">La restauración del proyecto con una única TargetFramework no debe condicionar las propiedades: [#3588](https://github.com/NuGet/Home/issues/3588)</span><span class="sxs-lookup"><span data-stu-id="6c13f-181">Restore to project with single TargetFramework must not condition props - [#3588](https://github.com/NuGet/Home/issues/3588)</span></span>

* <span data-ttu-id="6c13f-182">dotnet restore3 foo.csproj debe seguir las dependencias de projectref y también restaurarlas.</span><span class="sxs-lookup"><span data-stu-id="6c13f-182">dotnet restore3 foo.csproj should follow projectref dependencies, and restore those too.</span></span> <span data-ttu-id="6c13f-183">Igual que la compilación:</span><span class="sxs-lookup"><span data-stu-id="6c13f-183">Like build.</span></span><span data-ttu-id="6c13f-184">[#3577](https://github.com/NuGet/Home/issues/3577)</span><span class="sxs-lookup"><span data-stu-id="6c13f-184"> - [#3577](https://github.com/NuGet/Home/issues/3577)</span></span>

* <span data-ttu-id="6c13f-185">Las dependencias "tipo": "plataforma" se representan como "tipo":"paquete" en el archivo de bloqueo: [#2695](https://github.com/NuGet/Home/issues/2695)</span><span class="sxs-lookup"><span data-stu-id="6c13f-185">"type": "platform" Dependencies represented as "type":"package" in lock file - [#2695](https://github.com/NuGet/Home/issues/2695)</span></span>

* <span data-ttu-id="6c13f-186">El modo detallado de nuget.exe debería mostrar la dirección URL de descarga: [#2629](https://github.com/NuGet/Home/issues/2629)</span><span class="sxs-lookup"><span data-stu-id="6c13f-186">nuget.exe Verbose mode should show the download url - [#2629](https://github.com/NuGet/Home/issues/2629)</span></span>

* <span data-ttu-id="6c13f-187">Mover xplat de NuGet a Microsoft.NetCore.App y netcoreapp1.0: [#2483](https://github.com/NuGet/Home/issues/2483)</span><span class="sxs-lookup"><span data-stu-id="6c13f-187">Move NuGet xplat to Microsoft.NetCore.App and netcoreapp1.0 - [#2483](https://github.com/NuGet/Home/issues/2483)</span></span>

* <span data-ttu-id="6c13f-188">Inserción: debe ser posible invalidar el servidor de símbolos al realizar inserciones desde la línea de comandos: [#2348](https://github.com/NuGet/Home/issues/2348)</span><span class="sxs-lookup"><span data-stu-id="6c13f-188">Push - It should be possible to override the symbol server when pushing from the command line - [#2348](https://github.com/NuGet/Home/issues/2348)</span></span>

* <span data-ttu-id="6c13f-189">Consolidar el código para buscar la ruta de acceso global de los paquetes: [#2296](https://github.com/NuGet/Home/issues/2296)</span><span class="sxs-lookup"><span data-stu-id="6c13f-189">Consolidate code for finding the global packages path - [#2296](https://github.com/NuGet/Home/issues/2296)</span></span>

* <span data-ttu-id="6c13f-190">Se necesita un nombre más adecuado que suppressParent: [#2196](https://github.com/NuGet/Home/issues/2196)</span><span class="sxs-lookup"><span data-stu-id="6c13f-190">Need a better name than suppressParent - [#2196](https://github.com/NuGet/Home/issues/2196)</span></span>

* <span data-ttu-id="6c13f-191">Determinar el nombre de dependencia de `project.json` que se va a usar para los proyectos de MSBuild: [#1914](https://github.com/NuGet/Home/issues/1914)</span><span class="sxs-lookup"><span data-stu-id="6c13f-191">Determine `project.json` dependency name to use for MSBuild projects - [#1914](https://github.com/NuGet/Home/issues/1914)</span></span>

* <span data-ttu-id="6c13f-192">Agregar compatibilidad con SemVer 2.0.0 a NuGet.Core: [#3383](https://github.com/NuGet/Home/issues/3383)</span><span class="sxs-lookup"><span data-stu-id="6c13f-192">Add SemVer 2.0.0 support to NuGet.Core - [#3383](https://github.com/NuGet/Home/issues/3383)</span></span>

* <span data-ttu-id="6c13f-193">Permitir la disponibilidad de NuPkgs con dependencias transitivas con `.targets` en MSBuild: [#3342](https://github.com/NuGet/Home/issues/3342)</span><span class="sxs-lookup"><span data-stu-id="6c13f-193">Allow transitive dependency NuPkgs with `.targets` to be available in MSBuild - [#3342](https://github.com/NuGet/Home/issues/3342)</span></span>

* <span data-ttu-id="6c13f-194">La restauración de NuGet desde la línea de comandos es mucho más lenta que en VS: [#3330](https://github.com/NuGet/Home/issues/3330)</span><span class="sxs-lookup"><span data-stu-id="6c13f-194">NuGet restore from the commandline is significantly slower than VS - [#3330](https://github.com/NuGet/Home/issues/3330)</span></span>

* <span data-ttu-id="6c13f-195">Hacer que el identificador del paquete y la comparación de versiones no distingan entre mayúsculas y minúsculas: [#2522](https://github.com/NuGet/Home/issues/2522)</span><span class="sxs-lookup"><span data-stu-id="6c13f-195">Make package ID and version comparison case insensitive - [#2522](https://github.com/NuGet/Home/issues/2522)</span></span>

* <span data-ttu-id="6c13f-196">La opción NoCache no funciona para la restauración o instalación basada en `packages.config` (GlobalPackagesFolder): [#1406](https://github.com/NuGet/Home/issues/1406)</span><span class="sxs-lookup"><span data-stu-id="6c13f-196">NoCache option does not work for `packages.config` based restore/install (GlobalPackagesFolder) - [#1406](https://github.com/NuGet/Home/issues/1406)</span></span>

* <span data-ttu-id="6c13f-197">Los recursos FindPackageByIdResource necesitan un contexto de caché y un registrador predeterminados: [#1357](https://github.com/NuGet/Home/issues/1357)</span><span class="sxs-lookup"><span data-stu-id="6c13f-197">FindPackageByIdResource resources needs a default cache context and logger - [#1357](https://github.com/NuGet/Home/issues/1357)</span></span>