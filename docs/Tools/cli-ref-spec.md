---
title: Comando de NuGet CLI spec | Documentos de Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 85611449-87e6-489b-8c6c-fe1d7be76c13
description: Referencia para el comando spec nuget.exe
keywords: "referencia de especificación de NuGet, especificaciones de comando"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c32b23e66c8eb4db1c8fa6dc615589219c00239f
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="spec-command-nuget-cli"></a><span data-ttu-id="cec74-104">comando spec (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="cec74-104">spec command (NuGet CLI)</span></span>

<span data-ttu-id="cec74-105">**Se aplica a:** la creación del paquete &bullet; **versiones admitidas:** todos</span><span class="sxs-lookup"><span data-stu-id="cec74-105">**Applies to:** package creation &bullet; **Supported versions:** all</span></span>

<span data-ttu-id="cec74-106">Genera un `.nuspec` archivo para un nuevo paquete.</span><span class="sxs-lookup"><span data-stu-id="cec74-106">Generates a `.nuspec` file for a new package.</span></span> <span data-ttu-id="cec74-107">Si se ejecutan en la misma carpeta que un archivo de proyecto (`.csproj`, `.vbproj`, `.fsproj`), `spec` crea un con tokens `.nuspec` archivo.</span><span class="sxs-lookup"><span data-stu-id="cec74-107">If run in the same folder as a project file (`.csproj`, `.vbproj`, `.fsproj`), `spec` creates a tokenized `.nuspec` file.</span></span> <span data-ttu-id="cec74-108">Para obtener más información, consulte [crear un paquete](../create-packages/creating-a-package.md).</span><span class="sxs-lookup"><span data-stu-id="cec74-108">For additional information, see [Creating a Package](../create-packages/creating-a-package.md).</span></span>

## <a name="usage"></a><span data-ttu-id="cec74-109">Uso</span><span class="sxs-lookup"><span data-stu-id="cec74-109">Usage</span></span>

```
nuget spec [<packageID>] [options]
```

<span data-ttu-id="cec74-110">donde `<packageID>` es un identificador de paquete opcional para guardar en el `.nuspec` archivo.</span><span class="sxs-lookup"><span data-stu-id="cec74-110">where `<packageID>` is an optional package identifier to save in the `.nuspec` file.</span></span>

## <a name="options"></a><span data-ttu-id="cec74-111">Opciones</span><span class="sxs-lookup"><span data-stu-id="cec74-111">Options</span></span>

| <span data-ttu-id="cec74-112">Opción</span><span class="sxs-lookup"><span data-stu-id="cec74-112">Option</span></span> | <span data-ttu-id="cec74-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="cec74-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="cec74-114">AssemblyPath</span><span class="sxs-lookup"><span data-stu-id="cec74-114">AssemblyPath</span></span> | <span data-ttu-id="cec74-115">Especifica la ruta de acceso al ensamblado que se va a usar para los metadatos.</span><span class="sxs-lookup"><span data-stu-id="cec74-115">Specifies the path to the assembly to use for metadata.</span></span> |
| <span data-ttu-id="cec74-116">Force</span><span class="sxs-lookup"><span data-stu-id="cec74-116">Force</span></span> | <span data-ttu-id="cec74-117">Sobrescribe cualquier existente `.nuspec` archivo.</span><span class="sxs-lookup"><span data-stu-id="cec74-117">Overwrites any existing `.nuspec` file.</span></span> |
| <span data-ttu-id="cec74-118">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="cec74-118">ForceEnglishOutput</span></span> | <span data-ttu-id="cec74-119">*(3.5 +)*  Fuerza nuget.exe ejecutándose con una referencia cultural invariable, basados en el inglés.</span><span class="sxs-lookup"><span data-stu-id="cec74-119">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="cec74-120">Ayuda</span><span class="sxs-lookup"><span data-stu-id="cec74-120">Help</span></span> | <span data-ttu-id="cec74-121">Muestra información de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="cec74-121">Displays help information for the command.</span></span> |
| <span data-ttu-id="cec74-122">No interactivo</span><span class="sxs-lookup"><span data-stu-id="cec74-122">NonInteractive</span></span> | <span data-ttu-id="cec74-123">Suprime los mensajes para la entrada de usuario o confirmaciones.</span><span class="sxs-lookup"><span data-stu-id="cec74-123">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="cec74-124">Nivel de detalle</span><span class="sxs-lookup"><span data-stu-id="cec74-124">Verbosity</span></span> | <span data-ttu-id="cec74-125">Especifica la cantidad de detalle que se muestra en la salida: *normal*, *quiet*, *detallada (2.5 +)*.</span><span class="sxs-lookup"><span data-stu-id="cec74-125">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed (2.5+)*.</span></span> |

<span data-ttu-id="cec74-126">Consulte también [variables de entorno](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="cec74-126">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="examples"></a><span data-ttu-id="cec74-127">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="cec74-127">Examples</span></span>

```
nuget spec

nuget spec MyPackage

nuget spec -a MyAssembly.dll
```