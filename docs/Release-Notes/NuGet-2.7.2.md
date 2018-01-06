---
title: "Notas de la versión de NuGet 2.7.2 | Documentos de Microsoft"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: c775d1d7-de26-476c-bf9e-0cf95986a22f
description: "Notas de la versión de NuGet 2.7.2 incluidos problemas conocidos, correcciones de errores, las funciones agregadas y dcr."
keywords: "NuGet 2.7.2 notas de la versión, correcciones de errores, problemas, conocidos agregan características, DCR"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 5bb1eb346666c5d5ee790fcdcd7d844bfd37b22e
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-272-release-notes"></a><span data-ttu-id="cd23a-104">Notas de la versión de NuGet 2.7.2</span><span class="sxs-lookup"><span data-stu-id="cd23a-104">NuGet 2.7.2 Release Notes</span></span>

<span data-ttu-id="cd23a-105">[Notas de la versión de NuGet 2.7.1](../release-notes/nuget-2.7.1.md) | [notas de la versión de NuGet 2.8](../release-notes/nuget-2.8.md)</span><span class="sxs-lookup"><span data-stu-id="cd23a-105">[NuGet 2.7.1 Release Notes](../release-notes/nuget-2.7.1.md) | [NuGet 2.8 Release Notes](../release-notes/nuget-2.8.md)</span></span>

<span data-ttu-id="cd23a-106">NuGet 2.7.2 se publicó en el 11 de noviembre de 2013.</span><span class="sxs-lookup"><span data-stu-id="cd23a-106">NuGet 2.7.2 was released on November 11, 2013.</span></span>

## <a name="noteworthy-bug-fixes-and-features"></a><span data-ttu-id="cd23a-107">Merece la pena comentar correcciones de errores y características</span><span class="sxs-lookup"><span data-stu-id="cd23a-107">Noteworthy Bug Fixes and Features</span></span>

### <a name="license-text"></a><span data-ttu-id="cd23a-108">Texto de licencia</span><span class="sxs-lookup"><span data-stu-id="cd23a-108">License Text</span></span>
<span data-ttu-id="cd23a-109">Durante bastante tiempo, Microsoft ha incluido los paquetes de NuGet para varias bibliotecas de código abierto populares como parte de las plantillas predeterminadas para los proyectos de aplicación Web en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd23a-109">For quite some time, Microsoft has included the NuGet packages for several popular open-source libraries as a part of the default templates for Web application projects in Visual Studio.</span></span> <span data-ttu-id="cd23a-110">jQuery es probablemente el ejemplo más conocido de este tipo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="cd23a-110">jQuery is probably the most well-known example of this type of library.</span></span> <span data-ttu-id="cd23a-111">Por el contrato de soporte técnico asociado con los componentes que se entregan junto con un producto, archivo de script del paquete contiene el texto de licencias distinto que el archivo de script que se encuentra en el mismo paquete en la Galería de nuget.org pública.</span><span class="sxs-lookup"><span data-stu-id="cd23a-111">Because of the support agreement associated with components that are delivered along with a product, the package's script file contains different license text than the script file found in the same package on the public nuget.org gallery.</span></span> <span data-ttu-id="cd23a-112">Esta diferencia de texto puede impedir que las actualizaciones de paquete continuar como resultado de los bloques de texto de licencias distinto haciendo que los archivos de script que tengan valores de hash de contenido diferente (y, por tanto ser tratados como modificación en el proyecto).</span><span class="sxs-lookup"><span data-stu-id="cd23a-112">This difference in text can prevent package updates from proceeding as a result of the different license text blocks causing the script files to have different content hash values (and therefore to be treated as modified within the project).</span></span>

<span data-ttu-id="cd23a-113">Para mitigar este problema, NuGet 2.7.2 permite al autor de la secuencia de comandos incluir el bloque de texto de licencia dentro de una sección marcado especialmente que tiene el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="cd23a-113">To mitigate this issue, NuGet 2.7.2 allows the script author to include the license text block within a specially marked section which looks as follows.</span></span>

    /************** NUGET: BEGIN LICENSE TEXT **************
     * The following code is licensed under the MIT license
     * Additional license information below is informational
     * only.
     ************** NUGET: END LICENSE TEXT ***************/

<span data-ttu-id="cd23a-114">Al actualizar paquetes con contenido de archivos que contienen este bloque, NuGet no separe el contenido del bloque en la comparación con la versión de la Galería de NuGet y puede, por tanto, eliminar y actualizar el archivo de contenido como si coincide con la copia original.</span><span class="sxs-lookup"><span data-stu-id="cd23a-114">When updating packages with content files containing this block, NuGet does not factor the contents of the block into the comparison with the version on the NuGet gallery, and can therefore delete and update the content file as though it matches the original copy.</span></span>

<span data-ttu-id="cd23a-115">Este bloque se identifica mediante el texto "NUGET: BEGIN licencia TEXT" y "NUGET: final licencia" que se producen en cualquier lugar en el principio y final de líneas.</span><span class="sxs-lookup"><span data-stu-id="cd23a-115">This block is identified by the text "NUGET: BEGIN LICENSE TEXT" and "NUGET: END LICENSE TEXT" occurring anywhere on the beginning and ending lines.</span></span>  <span data-ttu-id="cd23a-116">No existe ningún requisito de formato, lo que permite esta característica para usarse en cualquier tipo de archivo de texto independientemente del lenguaje.</span><span class="sxs-lookup"><span data-stu-id="cd23a-116">No other formatting requirements exist, allowing this feature to be used in any type of text file regardless of language.</span></span>

### <a name="add-binding-redirects-for-non-framework-assemblies"></a><span data-ttu-id="cd23a-117">Agrega redirecciones de enlace de ensamblados no Framework</span><span class="sxs-lookup"><span data-stu-id="cd23a-117">Add Binding Redirects for non-Framework Assemblies</span></span>
<span data-ttu-id="cd23a-118">Para los ensamblados que forman parte de .NET Framework, NuGet omite agregar redirecciones de enlace en el archivo de configuración de la aplicación al actualizar el paquete.</span><span class="sxs-lookup"><span data-stu-id="cd23a-118">For assemblies that are part of the .NET Framework, NuGet skips adding binding redirects into the application's configuration file when updating the package.</span></span> <span data-ttu-id="cd23a-119">Esta revisión corrige una regresión en 2.7 NuGet mediante el cual redirecciones de enlace no se agregaron para algunos ensamblados, incluso si esos ensamblados no forman considera parte de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd23a-119">This fix addresses a regression in NuGet 2.7 whereby binding redirects were not being added for some assemblies, even though those assemblies are not considered a part of the .NET Framework.</span></span> <span data-ttu-id="cd23a-120">NuGet 2.7.2 restaura el anterior NuGet 2.5 y comportamiento 2.6 y agrega las redirecciones de enlace.</span><span class="sxs-lookup"><span data-stu-id="cd23a-120">NuGet 2.7.2 restores the previous NuGet 2.5 and 2.6 behavior and adds the binding redirects.</span></span>

### <a name="installing-portable-libraries-with-xamarin-tools-installed"></a><span data-ttu-id="cd23a-121">Instalar las bibliotecas portátiles con instaladas las herramientas de Xamarin</span><span class="sxs-lookup"><span data-stu-id="cd23a-121">Installing portable libraries with Xamarin Tools installed</span></span>
<span data-ttu-id="cd23a-122">Cuando se instalan las herramientas de desarrollo de Xamarin en un equipo, modifican los datos de configuración de marcos admitidos para especificar la compatibilidad entre combinaciones de framework de destino existentes y marcos de trabajo de Xamarin.</span><span class="sxs-lookup"><span data-stu-id="cd23a-122">When Xamarin's development tools are installed on a machine, they modify the supported frameworks configuration data to specify compatibility between existing target framework combinations and Xamarin frameworks.</span></span> <span data-ttu-id="cd23a-123">Con la versión 2.7.2, ahora es compatible con estas reglas de compatibilidad implícita NuGet y, por tanto, facilita que los desarrolladores de Xamarin plataformas de destino instalar las bibliotecas portátiles que son compatibles con Xamarin, pero no explícitamente marquen como tal en el paquete metadatos de sí mismo.</span><span class="sxs-lookup"><span data-stu-id="cd23a-123">With version 2.7.2, NuGet is now aware of these implicit compatibility rules, and therefore makes it easy for developers targeting Xamarin platforms to install portable libraries that are Xamarin-compatible but not explicitly marked as such in the package metadata itself.</span></span>

### <a name="machine-wide-configuration-settings-honored"></a><span data-ttu-id="cd23a-124">Opciones de configuración de todo el equipo respetados</span><span class="sxs-lookup"><span data-stu-id="cd23a-124">Machine-wide configuration settings honored</span></span>
<span data-ttu-id="cd23a-125">Cuando se usan archivos de Nuget.Config jerárquicos, la clave de repositoryPath no se se ha respetado para los archivos de Nuget.Config más cercanos a la raíz de la solución.</span><span class="sxs-lookup"><span data-stu-id="cd23a-125">When using hierarchical Nuget.Config files, the repositoryPath key was not being honored for Nuget.Config files closest to the solution root.</span></span> <span data-ttu-id="cd23a-126">En Visual Studio 2013, NuGet instala un archivo Nuget.Config personalizado en %ProgramData%\NuGet\Config\VisualStudio\12.0\Microsoft.VisualStudio.config con el fin de agregar el origen del paquete "Microsoft y. NET".</span><span class="sxs-lookup"><span data-stu-id="cd23a-126">In Visual Studio 2013, NuGet installs a custom Nuget.Config file at %ProgramData%\NuGet\Config\VisualStudio\12.0\Microsoft.VisualStudio.config in order to add the "Microsoft and .NET" package source.</span></span> <span data-ttu-id="cd23a-127">Como resultado, la solución para usar un repositoryPath personalizado en una solución era eliminar Nuget.Config de nivel de equipo - lo que también significa quitar el origen del paquete "Microsoft y. NET".</span><span class="sxs-lookup"><span data-stu-id="cd23a-127">As a result, the work-around for using a custom repositoryPath in a solution was to delete the machine-level Nuget.Config - which also meant removing the "Microsoft and .NET" package source.</span></span> <span data-ttu-id="cd23a-128">NuGet 2.7.2 ahora respeta las reglas de precedencia de repositoryPath cuando se usan archivos de Nuget.Config jerárquicos.</span><span class="sxs-lookup"><span data-stu-id="cd23a-128">NuGet 2.7.2 now honors the precedence rules for repositoryPath when using hierarchical Nuget.Config files.</span></span>

## <a name="all-changes"></a><span data-ttu-id="cd23a-129">Todos los cambios</span><span class="sxs-lookup"><span data-stu-id="cd23a-129">All Changes</span></span>
<span data-ttu-id="cd23a-130">Para obtener una lista completa de trabajo elementos corregidos en NuGet 2.7.2, por favor, vista la [NuGet Issue Tracker para esta versión](https://nuget.codeplex.com/workitem/list/advanced?keyword=&status=All&type=All&priority=All&release=NuGet%202.7.2&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0&reasonClosed=Fixed).</span><span class="sxs-lookup"><span data-stu-id="cd23a-130">For a full list of work items fixed in NuGet 2.7.2, please view the [NuGet Issue Tracker for this release](https://nuget.codeplex.com/workitem/list/advanced?keyword=&status=All&type=All&priority=All&release=NuGet%202.7.2&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0&reasonClosed=Fixed).</span></span>