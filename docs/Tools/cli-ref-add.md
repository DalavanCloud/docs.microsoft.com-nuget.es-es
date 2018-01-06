---
title: NuGet CLI Agregar comando | Documentos de Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 4f68a016-ad4e-41fc-b869-88910fc5121e
description: Referencia para el nuget.exe agregar (comando)
keywords: NuGet Agregar referencia, agregue el comando del paquete
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: bf9a6e51dfbf1716ba40273487b76ae04c18e948
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="add-command-nuget-cli"></a><span data-ttu-id="003c9-104">Agregar comando (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="003c9-104">add command (NuGet CLI)</span></span>

<span data-ttu-id="003c9-105">**Se aplica a**: paquete de publicación &bullet; **versiones compatibles**: 3.3 +</span><span class="sxs-lookup"><span data-stu-id="003c9-105">**Applies to**: package publishing &bullet; **Supported versions**: 3.3+</span></span>

<span data-ttu-id="003c9-106">Agrega un paquete específico a un origen de paquete no son HTTP (una carpeta o ruta de acceso UNC) en un formato jerárquico y en el que se crean las carpetas para el número de identificador y la versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="003c9-106">Adds a specified package to a non-HTTP package source (a folder or UNC path) in a hierarchical layout, wherein folders are created for the package ID and version number.</span></span> <span data-ttu-id="003c9-107">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="003c9-107">For example:</span></span>

    \\myserver\packages
      └─<packageID>
        └─<version>
          ├─<packageID>.<version>.nupkg
          ├─<packageID>.<version>.nupkg.sha512
          └─<packageID>.nuspec

<span data-ttu-id="003c9-108">Al restaurar o actualizar en el origen del paquete, formato jerárquico proporciona un rendimiento significativamente mejor.</span><span class="sxs-lookup"><span data-stu-id="003c9-108">When restoring or updating against the package source, hierarchical layout provides significantly better performance.</span></span>

<span data-ttu-id="003c9-109">Para expandir todos los archivos en el paquete en el origen del paquete de destino, use el `-Expand` cambiar.</span><span class="sxs-lookup"><span data-stu-id="003c9-109">To expand all the files in the package to the destination package source, use the `-Expand` switch.</span></span> <span data-ttu-id="003c9-110">Normalmente esto tiene como resultado en subcarpetas adicionales que aparecen en el destino, como `tools` y `lib`.</span><span class="sxs-lookup"><span data-stu-id="003c9-110">This typically results in additional subfolders appearing in the destination, such as `tools` and `lib`.</span></span>

## <a name="usage"></a><span data-ttu-id="003c9-111">Uso</span><span class="sxs-lookup"><span data-stu-id="003c9-111">Usage</span></span>

```
nuget add <packagePath> -Source <sourcePath> [options]
```

<span data-ttu-id="003c9-112">donde `<packagePath>` es la ruta de acceso al paquete que se agregará y `<sourcePath>` especifica el origen del paquete basada en la carpeta a la que se agregará el paquete.</span><span class="sxs-lookup"><span data-stu-id="003c9-112">where `<packagePath>` is the pathname to the package to add, and `<sourcePath>` specifies the folder-based package source to which the package will be added.</span></span> <span data-ttu-id="003c9-113">No se admiten orígenes HTTP.</span><span class="sxs-lookup"><span data-stu-id="003c9-113">HTTP sources are not supported.</span></span>

## <a name="options"></a><span data-ttu-id="003c9-114">Opciones</span><span class="sxs-lookup"><span data-stu-id="003c9-114">Options</span></span>

| <span data-ttu-id="003c9-115">Opción</span><span class="sxs-lookup"><span data-stu-id="003c9-115">Option</span></span> | <span data-ttu-id="003c9-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="003c9-116">Description</span></span> |
| --- | --- |
| <span data-ttu-id="003c9-117">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="003c9-117">ConfigFile</span></span> | <span data-ttu-id="003c9-118">El archivo de configuración de NuGet para aplicar.</span><span class="sxs-lookup"><span data-stu-id="003c9-118">The NuGet configuration file to apply.</span></span> <span data-ttu-id="003c9-119">Si no se especifica, *%AppData%\NuGet\NuGet.Config* se utiliza.</span><span class="sxs-lookup"><span data-stu-id="003c9-119">If not specified, *%AppData%\NuGet\NuGet.Config* is used.</span></span>| 
| <span data-ttu-id="003c9-120">Expand</span><span class="sxs-lookup"><span data-stu-id="003c9-120">Expand</span></span> | <span data-ttu-id="003c9-121">Agrega todos los archivos en el paquete en el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="003c9-121">Adds all the files in the package to the package source.</span></span> |
| <span data-ttu-id="003c9-122">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="003c9-122">ForceEnglishOutput</span></span> | <span data-ttu-id="003c9-123">*(3.5 +)*  Fuerza nuget.exe ejecutándose con una referencia cultural invariable, basados en el inglés.</span><span class="sxs-lookup"><span data-stu-id="003c9-123">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="003c9-124">Ayuda</span><span class="sxs-lookup"><span data-stu-id="003c9-124">Help</span></span> | <span data-ttu-id="003c9-125">Muestra información de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="003c9-125">Displays help information for the command.</span></span> |
| <span data-ttu-id="003c9-126">No interactivo</span><span class="sxs-lookup"><span data-stu-id="003c9-126">NonInteractive</span></span> | <span data-ttu-id="003c9-127">Suprime los mensajes para la entrada de usuario o confirmaciones.</span><span class="sxs-lookup"><span data-stu-id="003c9-127">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="003c9-128">Nivel de detalle</span><span class="sxs-lookup"><span data-stu-id="003c9-128">Verbosity</span></span> | <span data-ttu-id="003c9-129">Especifica la cantidad de detalle que se muestra en la salida: *normal*, *quiet*, *detallada*.</span><span class="sxs-lookup"><span data-stu-id="003c9-129">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

<span data-ttu-id="003c9-130">Consulte también [variables de entorno](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="003c9-130">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="examples"></a><span data-ttu-id="003c9-131">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="003c9-131">Examples</span></span>

```
nuget add foo.nupkg -Source c:\bar\

nuget add foo.nupkg -Source \\bar\packages\
```