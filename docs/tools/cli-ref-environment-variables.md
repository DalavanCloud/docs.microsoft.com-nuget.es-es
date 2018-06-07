---
title: Variables de entorno de NuGet CLI
description: Referencia para las variables de entorno nuget.exe
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 50bf8b469eda423db7665323823a2daf3f3aa41d
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34817078"
---
# <a name="nuget-cli-environment-variables"></a><span data-ttu-id="0dbff-103">Variables de entorno de NuGet CLI</span><span class="sxs-lookup"><span data-stu-id="0dbff-103">NuGet CLI environment variables</span></span>

<span data-ttu-id="0dbff-104">El comportamiento de la CLI nuget.exe puede configurarse a través de una serie de variables de entorno, que afectan a nuget.exe en todo el equipo, usuario o proceso niveles.</span><span class="sxs-lookup"><span data-stu-id="0dbff-104">The behavior of the nuget.exe CLI can be configured through a number of environment variables, which affect nuget.exe on computer-wide, user, or process levels.</span></span> <span data-ttu-id="0dbff-105">Las variables de entorno siempre reemplazan la configuración en `NuGet.Config` archivos, lo que permite crear servidores para cambiar la configuración adecuada sin modificar los archivos.</span><span class="sxs-lookup"><span data-stu-id="0dbff-105">Environment variables always override any settings in `NuGet.Config` files, allowing build servers to change appropriate settings without modifying any files.</span></span>

<span data-ttu-id="0dbff-106">En general, las opciones especificadas directamente en la línea de comandos o en archivos de configuración de NuGet tienen prioridad, pero hay unas pocas excepciones, como *FORCE_NUGET_EXE_INTERACTIVE*.</span><span class="sxs-lookup"><span data-stu-id="0dbff-106">In general, options specified directly on the command line or in NuGet configuration files have precedence, but there are a few exceptions such as *FORCE_NUGET_EXE_INTERACTIVE*.</span></span> <span data-ttu-id="0dbff-107">Si encuentra que nuget.exe tiene un comportamiento diferente entre equipos diferentes, una variable de entorno podría ser la causa.</span><span class="sxs-lookup"><span data-stu-id="0dbff-107">If you find that nuget.exe behaves differently between different computers, an environment variable could be the cause.</span></span> <span data-ttu-id="0dbff-108">Por ejemplo, Kudu de aplicaciones Web de Azure (se usa durante la implementación) tiene *NUGET_XMLDOC_MODE* establecido en *omitir* para acelerar el rendimiento de la restauración de paquete y ahorrar espacio en disco.</span><span class="sxs-lookup"><span data-stu-id="0dbff-108">For example, Azure Web Apps Kudu (used during deployment) has *NUGET_XMLDOC_MODE* set to *skip* to speed up package restore performance and save disk space.</span></span>

| <span data-ttu-id="0dbff-109">Variable</span><span class="sxs-lookup"><span data-stu-id="0dbff-109">Variable</span></span> | <span data-ttu-id="0dbff-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dbff-110">Description</span></span> | <span data-ttu-id="0dbff-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="0dbff-111">Remarks</span></span> |
| --- | --- | --- |
| <span data-ttu-id="0dbff-112">http_proxy</span><span class="sxs-lookup"><span data-stu-id="0dbff-112">http_proxy</span></span> | <span data-ttu-id="0dbff-113">Proxy de HTTP que se utiliza para operaciones HTTP de NuGet.</span><span class="sxs-lookup"><span data-stu-id="0dbff-113">Http proxy used for NuGet HTTP operations.</span></span> | <span data-ttu-id="0dbff-114">Esto se especificarían como `http://<username>:<password>@proxy.com`.</span><span class="sxs-lookup"><span data-stu-id="0dbff-114">This would be specified as `http://<username>:<password>@proxy.com`.</span></span> |
| <span data-ttu-id="0dbff-115">no_proxy</span><span class="sxs-lookup"><span data-stu-id="0dbff-115">no_proxy</span></span> | <span data-ttu-id="0dbff-116">Configura los dominios se omitirá del uso de proxy.</span><span class="sxs-lookup"><span data-stu-id="0dbff-116">Configures domains to bypass from using proxy.</span></span> | <span data-ttu-id="0dbff-117">Especificar como dominios separados por coma (,).</span><span class="sxs-lookup"><span data-stu-id="0dbff-117">Specified as domains separated by comma (,).</span></span> |
| <span data-ttu-id="0dbff-118">EnableNuGetPackageRestore</span><span class="sxs-lookup"><span data-stu-id="0dbff-118">EnableNuGetPackageRestore</span></span> | <span data-ttu-id="0dbff-119">Marca si NuGet implícitamente debe conceder consentimiento si es necesaria por el paquete en la restauración.</span><span class="sxs-lookup"><span data-stu-id="0dbff-119">Flag for if NuGet should implicitly grant consent if that's required by package on restore.</span></span> | <span data-ttu-id="0dbff-120">Marca especificada se trata como *true* o *1*, cualquier otro valor que se tratan como marca no establecido.</span><span class="sxs-lookup"><span data-stu-id="0dbff-120">Specified flag is treated as *true* or *1*, any other value treated as flag not set.</span></span> |
| <span data-ttu-id="0dbff-121">NUGET_EXE_NO_PROMPT</span><span class="sxs-lookup"><span data-stu-id="0dbff-121">NUGET_EXE_NO_PROMPT</span></span> | <span data-ttu-id="0dbff-122">Impide que el archivo ejecutable para solicitar las credenciales.</span><span class="sxs-lookup"><span data-stu-id="0dbff-122">Prevents the exe for prompting for credentials.</span></span> | <span data-ttu-id="0dbff-123">Cualquier valor excepto una cadena nula o vacía se tratará como esta marca conjunto/true.</span><span class="sxs-lookup"><span data-stu-id="0dbff-123">Any value except null or empty string will be treated as this flag set/true.</span></span> |
| <span data-ttu-id="0dbff-124">FORCE_NUGET_EXE_INTERACTIVE</span><span class="sxs-lookup"><span data-stu-id="0dbff-124">FORCE_NUGET_EXE_INTERACTIVE</span></span> | <span data-ttu-id="0dbff-125">Variable de entorno global para forzar el modo interactivo.</span><span class="sxs-lookup"><span data-stu-id="0dbff-125">Global environment variable to force interactive mode.</span></span> | <span data-ttu-id="0dbff-126">Cualquier valor excepto una cadena nula o vacía se tratará como esta marca conjunto/true.</span><span class="sxs-lookup"><span data-stu-id="0dbff-126">Any value except null or empty string will be treated as this flag set/true.</span></span> |
| <span data-ttu-id="0dbff-127">NUGET_PACKAGES</span><span class="sxs-lookup"><span data-stu-id="0dbff-127">NUGET_PACKAGES</span></span> | <span data-ttu-id="0dbff-128">Ruta de acceso que se utilizará para la *global paquetes* carpeta tal como se describe en [administrar los paquetes globales y las carpetas de caché](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span><span class="sxs-lookup"><span data-stu-id="0dbff-128">Path to use for the *global-packages* folder as described on [Managing the global packages and cache folders](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span></span> | <span data-ttu-id="0dbff-129">Especificar como ruta de acceso absoluta.</span><span class="sxs-lookup"><span data-stu-id="0dbff-129">Specified as absolute path.</span></span> |
| <span data-ttu-id="0dbff-130">NUGET_FALLBACK_PACKAGES</span><span class="sxs-lookup"><span data-stu-id="0dbff-130">NUGET_FALLBACK_PACKAGES</span></span> | <span data-ttu-id="0dbff-131">Carpetas de paquetes de reserva global.</span><span class="sxs-lookup"><span data-stu-id="0dbff-131">Global fallback packages folders.</span></span> | <span data-ttu-id="0dbff-132">Rutas de acceso de carpeta absoluto separados por punto y coma (;).</span><span class="sxs-lookup"><span data-stu-id="0dbff-132">Absolute folder paths separated by semicolon (;).</span></span> |
| <span data-ttu-id="0dbff-133">NUGET_HTTP_CACHE_PATH</span><span class="sxs-lookup"><span data-stu-id="0dbff-133">NUGET_HTTP_CACHE_PATH</span></span> | <span data-ttu-id="0dbff-134">Ruta de acceso que se utilizará para la *caché http* carpeta tal como se describe en [administrar los paquetes globales y las carpetas de caché](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span><span class="sxs-lookup"><span data-stu-id="0dbff-134">Path to use for the *http-cache* folder as described on [Managing the global packages and cache folders](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span></span> | <span data-ttu-id="0dbff-135">Especificar como ruta de acceso absoluta.</span><span class="sxs-lookup"><span data-stu-id="0dbff-135">Specified as absolute path.</span></span> |
| <span data-ttu-id="0dbff-136">NUGET_PERSIST_DG</span><span class="sxs-lookup"><span data-stu-id="0dbff-136">NUGET_PERSIST_DG</span></span> | <span data-ttu-id="0dbff-137">Marca que indica si se deben almacenar los archivos de grupo de distribución (los datos recopilados de MSBuild).</span><span class="sxs-lookup"><span data-stu-id="0dbff-137">Flag indicating if dg files (data collected from MSBuild) should be persisted.</span></span> | <span data-ttu-id="0dbff-138">Especificado como *true* o *false* (valor predeterminado), si no establece NUGET_PERSIST_DG_PATH se almacenará en el directorio temporal (carpeta de NuGetScratch en el directorio temporal de entorno actual).</span><span class="sxs-lookup"><span data-stu-id="0dbff-138">Specified as *true* or *false* (default), if NUGET_PERSIST_DG_PATH not set will be stored to temporary directory (NuGetScratch folder in current environment temp directory).</span></span> |
| <span data-ttu-id="0dbff-139">NUGET_PERSIST_DG_PATH</span><span class="sxs-lookup"><span data-stu-id="0dbff-139">NUGET_PERSIST_DG_PATH</span></span> | <span data-ttu-id="0dbff-140">Ruta de acceso para conservar los archivos de grupo de distribución.</span><span class="sxs-lookup"><span data-stu-id="0dbff-140">Path to persist dg files.</span></span> | <span data-ttu-id="0dbff-141">Especificado como ruta de acceso absoluta, esta opción es utiliza únicamente cuando *NUGET_PERSIST_DG* está establecido en true.</span><span class="sxs-lookup"><span data-stu-id="0dbff-141">Specified as absolute path, this option is only used when *NUGET_PERSIST_DG* is set to true.</span></span> |
| <span data-ttu-id="0dbff-142">NUGET_RESTORE_MSBUILD_ARGS</span><span class="sxs-lookup"><span data-stu-id="0dbff-142">NUGET_RESTORE_MSBUILD_ARGS</span></span> | <span data-ttu-id="0dbff-143">Establece los argumentos de MSBuild adicionales.</span><span class="sxs-lookup"><span data-stu-id="0dbff-143">Sets additional MSBuild arguments.</span></span> | |
| <span data-ttu-id="0dbff-144">NUGET_RESTORE_MSBUILD_VERBOSITY</span><span class="sxs-lookup"><span data-stu-id="0dbff-144">NUGET_RESTORE_MSBUILD_VERBOSITY</span></span> | <span data-ttu-id="0dbff-145">Establece el nivel de detalle del registro de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0dbff-145">Sets the MSBuild log verbosity.</span></span> | <span data-ttu-id="0dbff-146">Valor predeterminado es *silencioso* ("/ v: q").</span><span class="sxs-lookup"><span data-stu-id="0dbff-146">Default is *quiet* ("/v:q").</span></span> <span data-ttu-id="0dbff-147">Los valores posibles *q [uiet]*, *m [inimal]*, *n [ormal]*, *d. [detallado]*, y *diag [nostic]*.</span><span class="sxs-lookup"><span data-stu-id="0dbff-147">Possible values *q[uiet]*, *m[inimal]*, *n[ormal]*, *d[etailed]*, and *diag[nostic]*.</span></span> |
| <span data-ttu-id="0dbff-148">NUGET_SHOW_STACK</span><span class="sxs-lookup"><span data-stu-id="0dbff-148">NUGET_SHOW_STACK</span></span> | <span data-ttu-id="0dbff-149">Determina si la excepción completa (incluido el seguimiento de la pila) se debe mostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="0dbff-149">Determines whether the full exception (including stack trace) should be displayed to the user.</span></span> | <span data-ttu-id="0dbff-150">Especificado como *true* o *false* (valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="0dbff-150">Specified as *true* or *false* (default).</span></span> |
| <span data-ttu-id="0dbff-151">NUGET_XMLDOC_MODE</span><span class="sxs-lookup"><span data-stu-id="0dbff-151">NUGET_XMLDOC_MODE</span></span> | <span data-ttu-id="0dbff-152">Determina cómo debe controlarse la extracción de archivos de documentación de XML de ensamblados.</span><span class="sxs-lookup"><span data-stu-id="0dbff-152">Determines how assemblies XML documentation file extraction should be handled.</span></span> | <span data-ttu-id="0dbff-153">Los modos compatibles son *omitir* (no extraiga los archivos de documentación XML), *comprimir* (almacenar archivos de documento XML como un archivo zip) o *ninguno* (valor predeterminado, tratar los archivos de documento XML como normal archivos).</span><span class="sxs-lookup"><span data-stu-id="0dbff-153">Supported modes are *skip* (do not extract XML documentation files), *compress* (store XML doc files as a zip archive) or *none* (default, treat XML doc files as regular files).</span></span> |