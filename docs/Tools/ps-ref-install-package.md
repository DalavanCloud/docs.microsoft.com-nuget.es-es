---
title: "Referencia de PowerShell de paquete de instalación de NuGet | Documentos de Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 6/1/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 879db0ef-6b72-4a4a-bb68-f9e3a00f64b8
description: "Referencia de comandos de PowerShell de paquete de instalación en la consola de administrador de paquetes de NuGet en Visual Studio."
keywords: Consola de administrador, comandos de NuGet Powershell, referencia de NuGet Powershell, Install-Package de paquete de NuGet
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 4d7645297d2cd48f39a8e2ec168040710f6fc7a3
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="install-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="4801f-104">Paquete de instalación (consola de administrador de paquetes en Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="4801f-104">Install-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="4801f-105">*Este tema describe el comando dentro de la [NuGet Package Manager Console](Package-Manager-Console.md) en Visual Studio en Windows. Para el comando de PowerShell Install-Package genérico, vea la [referencia de PowerShell PackageManagement](/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="4801f-105">*This topic describes the command within the [NuGet Package Manager Console](Package-Manager-Console.md) in Visual Studio on Windows. For the generic PowerShell Install-Package command, see the [PowerShell PackageManagement reference](/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="4801f-106">Instala un paquete y sus dependencias en un proyecto.</span><span class="sxs-lookup"><span data-stu-id="4801f-106">Installs a package and its dependencies into a project.</span></span>

## <a name="syntax"></a><span data-ttu-id="4801f-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4801f-107">Syntax</span></span>

```ps
Install-Package [-Id] <string> [-IgnoreDependencies] [-ProjectName <string>] [[-Source] <string>] 
    [[-Version] <string>] [-IncludePrerelease] [-FileConflictAction] [-DependencyVersion]
    [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="4801f-108">En NuGet 2.8 + `Install-Package` puede degradar un paquete existente en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4801f-108">In NuGet 2.8+, `Install-Package` can downgrade an existing package in your project.</span></span> <span data-ttu-id="4801f-109">Por ejemplo, si tiene 5.1.0-rc1 Microsoft.AspNet.MVC instalado, el siguiente comando de la degradación a 5.0.0:</span><span class="sxs-lookup"><span data-stu-id="4801f-109">For example, if you have Microsoft.AspNet.MVC 5.1.0-rc1 installed, the following command would downgrade it to 5.0.0:</span></span>

```ps
Install-Package Microsoft.AspNet.MVC -Version 5.0.0.
```

<span data-ttu-id="4801f-110">NuGet 2.7 y versiones anterior, produce un error que indica que ya está instalada una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="4801f-110">NuGet 2.7 and earlier gives an error saying that a newer version is already installed.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="4801f-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4801f-111">Parameters</span></span>

| <span data-ttu-id="4801f-112">Parámetro</span><span class="sxs-lookup"><span data-stu-id="4801f-112">Parameter</span></span> | <span data-ttu-id="4801f-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="4801f-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="4801f-114">Id.</span><span class="sxs-lookup"><span data-stu-id="4801f-114">Id</span></span> | <span data-ttu-id="4801f-115">(Obligatorio) El identificador de paquete que desea instalar.</span><span class="sxs-lookup"><span data-stu-id="4801f-115">(Required) The identifier of the package to install.</span></span> <span data-ttu-id="4801f-116">(*3.0 +*) el identificador puede ser una ruta de acceso o dirección URL de un `packages.config` archivo o un `.nupkg` archivo.</span><span class="sxs-lookup"><span data-stu-id="4801f-116">(*3.0+*) The identifier can be a path or URL of a `packages.config` file or a `.nupkg` file.</span></span> <span data-ttu-id="4801f-117">-Identificador propio modificador es opcional.</span><span class="sxs-lookup"><span data-stu-id="4801f-117">The -Id switch itself is optional.</span></span> |
| <span data-ttu-id="4801f-118">IgnoreDependencies</span><span class="sxs-lookup"><span data-stu-id="4801f-118">IgnoreDependencies</span></span> | <span data-ttu-id="4801f-119">Instalar solo este paquete pero no sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="4801f-119">Install only this package and not its dependencies.</span></span> |
| <span data-ttu-id="4801f-120">NombreDelProyecto</span><span class="sxs-lookup"><span data-stu-id="4801f-120">ProjectName</span></span> | <span data-ttu-id="4801f-121">El proyecto en el que se va a instalar el paquete, el valor predeterminado para el proyecto predeterminado.</span><span class="sxs-lookup"><span data-stu-id="4801f-121">The project into which to install the package, defaulting to the default project.</span></span> |
| <span data-ttu-id="4801f-122">Origen</span><span class="sxs-lookup"><span data-stu-id="4801f-122">Source</span></span> | <span data-ttu-id="4801f-123">La ruta de acceso URL o una carpeta de origen del paquete para buscar.</span><span class="sxs-lookup"><span data-stu-id="4801f-123">The URL or folder path for the package source to search.</span></span> <span data-ttu-id="4801f-124">Las rutas de acceso de la carpeta local pueden ser absoluta o relativa a la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="4801f-124">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="4801f-125">Si se omite, `Install-Package` busca en el origen del paquete seleccionado.</span><span class="sxs-lookup"><span data-stu-id="4801f-125">If omitted, `Install-Package` searches the currently selected package source.</span></span> |
| <span data-ttu-id="4801f-126">Versión</span><span class="sxs-lookup"><span data-stu-id="4801f-126">Version</span></span> | <span data-ttu-id="4801f-127">La versión del paquete para instalar, toma como valor predeterminado para la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="4801f-127">The version of the package to install, defaulting to the latest version.</span></span> |
| <span data-ttu-id="4801f-128">IncludePrerelease</span><span class="sxs-lookup"><span data-stu-id="4801f-128">IncludePrerelease</span></span> | <span data-ttu-id="4801f-129">Considera los paquetes de versión preliminar para la instalación.</span><span class="sxs-lookup"><span data-stu-id="4801f-129">Considers prerelease packages for the install.</span></span> <span data-ttu-id="4801f-130">Si se omite, se consideran solo los paquetes estables.</span><span class="sxs-lookup"><span data-stu-id="4801f-130">If omitted, only stable packages are considered.</span></span> |
| <span data-ttu-id="4801f-131">FileConflictAction</span><span class="sxs-lookup"><span data-stu-id="4801f-131">FileConflictAction</span></span> | <span data-ttu-id="4801f-132">La acción que se realizará cuando se le pregunte para sobrescribir u omitir los archivos existentes al que hace referencia el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4801f-132">The action to take when asked to overwrite or ignore existing files referenced by the project.</span></span> <span data-ttu-id="4801f-133">Los valores posibles son *sobrescribir, omitir, None, OverwriteAll*, y *(3.0 +)* *IgnoreAll*.</span><span class="sxs-lookup"><span data-stu-id="4801f-133">Possible values are *Overwrite, Ignore, None, OverwriteAll*, and *(3.0+)* *IgnoreAll*.</span></span> |
| <span data-ttu-id="4801f-134">DependencyVersion</span><span class="sxs-lookup"><span data-stu-id="4801f-134">DependencyVersion</span></span> | <span data-ttu-id="4801f-135">La versión de los paquetes de dependencia que se va a usar, que puede ser uno de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="4801f-135">The version of the dependency packages to use, which can be one of the following:</span></span><br/><ul><li><span data-ttu-id="4801f-136">*Menor* (valor predeterminado): la versión más antigua</span><span class="sxs-lookup"><span data-stu-id="4801f-136">*Lowest* (default): the lowest version</span></span></li><li><span data-ttu-id="4801f-137">*HighestPatch*: la versión con la revisión mínimo mayor, menor menor, más alto</span><span class="sxs-lookup"><span data-stu-id="4801f-137">*HighestPatch*: the version with the lowest major, lowest minor, highest patch</span></span></li><li><span data-ttu-id="4801f-138">*HighestMinor*: la versión con el menor principales, mayor revisión secundaria, más alto</span><span class="sxs-lookup"><span data-stu-id="4801f-138">*HighestMinor*: the version with the lowest major, highest minor, highest patch</span></span></li><li><span data-ttu-id="4801f-139">*Mayor* (predeterminado para el paquete de actualización sin parámetros): la versión más reciente</span><span class="sxs-lookup"><span data-stu-id="4801f-139">*Highest* (default for Update-Package with no parameters): the highest version</span></span></li></ul><span data-ttu-id="4801f-140">Puede establecer el valor predeterminado mediante la [ `dependencyVersion` ](../Schema/nuget-config-file.md#config-section) en el `Nuget.Config` archivo.</span><span class="sxs-lookup"><span data-stu-id="4801f-140">You can set the default value using the [`dependencyVersion`](../Schema/nuget-config-file.md#config-section) setting in the `Nuget.Config` file.</span></span> |
| <span data-ttu-id="4801f-141">WhatIf</span><span class="sxs-lookup"><span data-stu-id="4801f-141">WhatIf</span></span> | <span data-ttu-id="4801f-142">Muestra qué ocurre cuando se ejecuta el comando sin realmente realizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="4801f-142">Shows what would happen when running the command without actually performing the install.</span></span> |

<span data-ttu-id="4801f-143">Ninguno de estos parámetros aceptan caracteres de entrada o el carácter comodín de canalización.</span><span class="sxs-lookup"><span data-stu-id="4801f-143">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="4801f-144">Parámetros comunes</span><span class="sxs-lookup"><span data-stu-id="4801f-144">Common Parameters</span></span>

<span data-ttu-id="4801f-145">`Install-Package`admite las siguientes [parámetros comunes de PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): depuración, acción de Error, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, detallado, WarningAction y WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4801f-145">`Install-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="4801f-146">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4801f-146">Examples</span></span>

```ps
# Installs the latest version of Elmah from the current source into the default project
Install-Package Elmah

# Installs Glimpse 1.0.0 into the MvcApplication1 project
Install-Package Glimpse -Version 1.0.0 -Project MvcApplication1

# Installs Ninject.Mvc3 but not its dependencies from c:\temp\packages
Install-Package Ninject.Mvc3 -IgnoreDependencies -Source c:\temp\packages

# Installs the package listed on the online packages.config into the current project.
Install-package https://raw.githubusercontent.com/json-ld.net/master/src/JsonLD/packages.config

# Installs jquery 1.10.2 package, using the .nupkg file under local path of c:\temp\packages.
Install-package c:\temp\packages\jQuery.1.10.2.nupkg

# Installs the specific online package
Install-package https://az320820.vo.msecnd.net/packages/microsoft.aspnet.mvc.5.2.3.nupkg
```