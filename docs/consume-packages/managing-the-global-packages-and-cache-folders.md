---
title: Cómo administrar las carpetas de paquetes globales, de caché y temporales en NuGet
description: Vea cómo administrar la carpeta de instalación de paquetes globales, la caché de paquetes y las carpetas temporales que existen en un equipo, que se utilizan al instalar, restaurar y actualizar paquetes.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 03/19/2018
ms.topic: conceptual
ms.openlocfilehash: 354a8ec80e2ba20abe27746dec8c8aaae9b6c96c
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="managing-the-global-packages-cache-and-temp-folders"></a><span data-ttu-id="5b2c0-103">Administración de las carpetas de paquetes globales, de caché y temporales</span><span class="sxs-lookup"><span data-stu-id="5b2c0-103">Managing the global packages, cache, and temp folders</span></span>

<span data-ttu-id="5b2c0-104">Cada vez que instala, actualiza o restaura un paquete, NuGet administra los paquetes y la información de paquete en varias externas a la estructura del proyecto:</span><span class="sxs-lookup"><span data-stu-id="5b2c0-104">Whenever you install, update, or restore a package, NuGet manages packages and package information in several folders outside of your project structure:</span></span>

| <span data-ttu-id="5b2c0-105">nombre</span><span class="sxs-lookup"><span data-stu-id="5b2c0-105">Name</span></span> | <span data-ttu-id="5b2c0-106">Descripción y ubicación (por usuario)</span><span class="sxs-lookup"><span data-stu-id="5b2c0-106">Description and Location (per user)</span></span>|
| --- | --- |
| <span data-ttu-id="5b2c0-107">global‑packages</span><span class="sxs-lookup"><span data-stu-id="5b2c0-107">global&#8209;packages</span></span> | <span data-ttu-id="5b2c0-108">La carpeta *global-packages* es donde NuGet instala los paquetes que se descargan.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-108">The *global-packages* folder is where NuGet installs any downloaded package.</span></span> <span data-ttu-id="5b2c0-109">Cada paquete se expande totalmente en una subcarpeta que coincida con el identificador y el número de versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-109">Each package is fully expanded into a subfolder that matches the package identifier and version number.</span></span> <span data-ttu-id="5b2c0-110">Los proyectos con el formato PackageReference siempre usan los paquetes directamente de esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-110">Projects using the PackageReference format always use packages directly from this folder.</span></span> <span data-ttu-id="5b2c0-111">Cuando se usa `packages.config`, los paquetes se instalan en la carpeta *global-packages* y luego se copian en la carpeta `packages` del proyecto.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-111">When using the `packages.config`, packages are installed to the *global-packages* folder, then copied into the project's `packages` folder.</span></span><br/><ul><li><span data-ttu-id="5b2c0-112">Windows: `%userprofile%\.nuget\packages`</span><span class="sxs-lookup"><span data-stu-id="5b2c0-112">Windows: `%userprofile%\.nuget\packages`</span></span></li><li><span data-ttu-id="5b2c0-113">Mac/Linux: `~/.nuget/packages`</span><span class="sxs-lookup"><span data-stu-id="5b2c0-113">Mac/Linux: `~/.nuget/packages`</span></span></li><li><span data-ttu-id="5b2c0-114">Se invalida mediante la variable de entorno NUGET_PACKAGES, las [opciones de configuración](../reference/nuget-config-file.md#config-section) `globalPackagesFolder` o `repositoryPath` (cuando se usa PackageReference y `packages.config`, respectivamente) o la propiedad `RestorePackagesPath` de MSBuild (solo MSBuild).</span><span class="sxs-lookup"><span data-stu-id="5b2c0-114">Override using the NUGET_PACKAGES environment variable, the `globalPackagesFolder` or `repositoryPath` [configuration settings](../reference/nuget-config-file.md#config-section) (when using PackageReference and `packages.config`, respectively), or the `RestorePackagesPath` MSBuild property (MSBuild only).</span></span> <span data-ttu-id="5b2c0-115">La variable de entorno tiene prioridad sobre la opción de configuración.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-115">The environment variable takes precedence over the configuration setting.</span></span></li></ul> |
| <span data-ttu-id="5b2c0-116">http-cache</span><span class="sxs-lookup"><span data-stu-id="5b2c0-116">http&#8209;cache</span></span> | <span data-ttu-id="5b2c0-117">El Administrador de paquetes de Visual Studio (NuGet 3.x y versiones posteriores) y la herramienta `dotnet` almacenan copias de los paquetes descargados en esta caché (guardados como archivos `.dat`), organizados en subcarpetas para cada origen de paquete.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-117">The Visual Studio Package Manager (NuGet 3.x+) and the `dotnet` tool store copies of downloaded packages in this cache (saved as `.dat` files), organized into subfolders for each package source.</span></span> <span data-ttu-id="5b2c0-118">Los paquetes no se expanden y la caché tiene un plazo de expiración de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-118">Packages are not expanded, and the cache has an expiration time of 30 minutes.</span></span><br/><ul><li><span data-ttu-id="5b2c0-119">Windows: `%localappdata%\NuGet\v3-cache`</span><span class="sxs-lookup"><span data-stu-id="5b2c0-119">Windows: `%localappdata%\NuGet\v3-cache`</span></span></li><li><span data-ttu-id="5b2c0-120">Mac/Linux: `~/.local/share/NuGet/v3-cache`</span><span class="sxs-lookup"><span data-stu-id="5b2c0-120">Mac/Linux: `~/.local/share/NuGet/v3-cache`</span></span></li><li><span data-ttu-id="5b2c0-121">Se invalida mediante la variable de entorno NUGET_HTTP_CACHE_PATH.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-121">Override using the NUGET_HTTP_CACHE_PATH environment variable.</span></span></li></ul> |
| <span data-ttu-id="5b2c0-122">temp</span><span class="sxs-lookup"><span data-stu-id="5b2c0-122">temp</span></span> | <span data-ttu-id="5b2c0-123">Carpeta donde NuGet almacena los archivos temporales durante sus diversas operaciones.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-123">A folder where NuGet stores temporary files during its various operations.</span></span><br/><li><span data-ttu-id="5b2c0-124">Windows: `%temp%\NuGetScratch`</span><span class="sxs-lookup"><span data-stu-id="5b2c0-124">Windows: `%temp%\NuGetScratch`</span></span></li><li><span data-ttu-id="5b2c0-125">Mac/Linux: `/tmp/NuGetScratch`</span><span class="sxs-lookup"><span data-stu-id="5b2c0-125">Mac/Linux: `/tmp/NuGetScratch`</span></span></li></ul> |

> [!Note]
> <span data-ttu-id="5b2c0-126">NuGet 3.5 y versiones anteriores utilizan *packages-cache* en lugar de *http-cache*, que se encuentra en `%localappdata%\NuGet\Cache`.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-126">NuGet 3.5 and earlier uses *packages-cache* instead of the *http-cache*, which is located in `%localappdata%\NuGet\Cache`.</span></span>

<span data-ttu-id="5b2c0-127">Mediante las carpetas *global-packages* y de caché, NuGet generalmente evita descargar paquetes que ya existen en el equipo, lo que mejora el rendimiento de las operaciones de instalación, actualización y restauración.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-127">By using the cache and *global-packages* folders, NuGet generally avoids downloading packages that already exist on the computer, improving the performance of install, update, and restore operations.</span></span> <span data-ttu-id="5b2c0-128">Cuando se usa PackageReference, la carpeta *global-packages* también evita mantener paquetes descargados dentro de carpetas de proyecto, donde podrían accidentalmente agregarse al control de código fuente, y reduce el impacto general de NuGet en el almacenamiento en el equipo.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-128">When using PackageReference, the *global-packages* folder also avoids keeping downloaded packages inside project folders, where they might be inadvertently added to source control, and reduces NuGet's overall impact on computer storage.</span></span>

<span data-ttu-id="5b2c0-129">Cuando se le pide que recupere un paquete, NuGet busca primero en la carpeta *global-packages*.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-129">When asked to retrieve a package, NuGet first looks in the *global-packages* folder.</span></span> <span data-ttu-id="5b2c0-130">Si la versión exacta del paquete no está, NuGet comprueba todos los orígenes de paquetes que no sean HTTP.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-130">If the exact version of package is not there, then NuGet checks all non-HTTP package sources.</span></span> <span data-ttu-id="5b2c0-131">Si todavía no se encuentra el paquete, NuGet lo busca en *http-cache* a menos que especifique `--no-cache` con comandos `dotnet.exe` o `-NoCache` con comandos `nuget.exe`.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-131">If the package is still not found, NuGet looks for the package in the *http-cache* unless you specify `--no-cache` with `dotnet.exe` commands or `-NoCache` with `nuget.exe` commands.</span></span> <span data-ttu-id="5b2c0-132">Si el paquete no está en la caché o esta no se usa, NuGet recupera luego el paquete por HTTP.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-132">If the package is not in the cache, or the cache isn't used, NuGet then retrieves the package over HTTP .</span></span>

<span data-ttu-id="5b2c0-133">Para más información, vea [¿Qué ocurre cuando se instala un paquete?](ways-to-install-a-package.md#what-happens-when-a-package-is-installed).</span><span class="sxs-lookup"><span data-stu-id="5b2c0-133">For more information, see [What happens when a package is installed](ways-to-install-a-package.md#what-happens-when-a-package-is-installed).</span></span>

## <a name="viewing-folder-locations"></a><span data-ttu-id="5b2c0-134">Visualización de ubicaciones de carpeta</span><span class="sxs-lookup"><span data-stu-id="5b2c0-134">Viewing folder locations</span></span>

<span data-ttu-id="5b2c0-135">Puede ver las ubicaciones de carpeta mediante el [comando dotnet nuget locals](/dotnet/core/tools/dotnet-nuget-locals):</span><span class="sxs-lookup"><span data-stu-id="5b2c0-135">You can view folder locations using the [dotnet nuget locals command](/dotnet/core/tools/dotnet-nuget-locals):</span></span>

```cli
dotnet nuget locals all --list
```

<span data-ttu-id="5b2c0-136">Salida típica (Mac/Linux; "user1" es el nombre de usuario actual):</span><span class="sxs-lookup"><span data-stu-id="5b2c0-136">Typical output (Mac/Linux; "user1" is the current username):</span></span>

```output
info : http-cache: /home/user1/.local/share/NuGet/v3-cache
info : global-packages: /home/user1/.nuget/packages/
info : temp: /tmp/NuGetScratch
```

<span data-ttu-id="5b2c0-137">Para mostrar la ubicación de una sola carpeta, use `http-cache`, `global-packages` o `temp` en lugar de `all`.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-137">To display the location of a single folder, use `http-cache`, `global-packages`, or `temp` instead of `all`.</span></span> 

<span data-ttu-id="5b2c0-138">También se ven ubicaciones mediante el [comando nuget locals](../tools/cli-ref-locals.md):</span><span class="sxs-lookup"><span data-stu-id="5b2c0-138">You also view locations using the [nuget locals command](../tools/cli-ref-locals.md):</span></span>

```cli
# Display locals for all folders: global-packages, cache, and temp
nuget locals all -list
```

<span data-ttu-id="5b2c0-139">Salida típica (Windows; "user1" es el nombre de usuario actual):</span><span class="sxs-lookup"><span data-stu-id="5b2c0-139">Typical output (Windows; "user1" is the current username):</span></span>

```output
http-cache: C:\Users\user1\AppData\Local\NuGet\v3-cache
global-packages: C:\Users\user1\.nuget\packages\
temp: C:\Users\user1\AppData\Local\Temp\NuGetScratch
```

<span data-ttu-id="5b2c0-140">(`package-cache` se utiliza en NuGet 2.x y aparece con NuGet 3.5 y versiones anteriores).</span><span class="sxs-lookup"><span data-stu-id="5b2c0-140">(`package-cache` is used in NuGet 2.x and appears with NuGet 3.5 and earlier.)</span></span>

## <a name="clearing-local-folders"></a><span data-ttu-id="5b2c0-141">Borrado de carpetas locales</span><span class="sxs-lookup"><span data-stu-id="5b2c0-141">Clearing local folders</span></span>

<span data-ttu-id="5b2c0-142">Si detecta problemas de instalación de paquetes o quiere asegurarse de que está instalando paquetes de una galería remota, use la opción `locals --clear` (dotnet.exe) o `locals -clear` (nuget.exe) para especificar la carpeta que quiere borrar o `all` para borrar todas las carpetas:</span><span class="sxs-lookup"><span data-stu-id="5b2c0-142">If you encounter package installation problems or otherwise want to ensure that you're installing packages from a remote gallery, use the `locals --clear` option (dotnet.exe) or `locals -clear` (nuget.exe), specifying the folder to clear, or `all` to clear all folders:</span></span>

```cli
# Clear the 3.x+ cache (use either command)
dotnet nuget locals http-cache --clear
nuget locals http-cache -clear

# Clear the 2.x cache (NuGet CLI 3.5 and earlier only)
nuget locals packages-cache -clear

# Clear the global packages folder (use either command)
dotnet nuget locals global-packages --clear
nuget locals global-packages -clear

# Clear the temporary cache (use either command)
dotnet nuget locals temp --clear
nuget locals temp -clear

# Clear all caches (use either command)
dotnet nuget locals all --clear
nuget locals all -clear
```

<span data-ttu-id="5b2c0-143">Los paquetes que se usen en proyectos que están actualmente abiertos en Visual Studio no se borran de la carpeta *global-packages*.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-143">Any packages used by projects that are currently open in Visual Studio are not cleared from the *global-packages* folder.</span></span>

<span data-ttu-id="5b2c0-144">En Visual Studio 2017, use el comando de menú **Herramientas > Administrador de paquetes NuGet > Configuración del Administrador de paquetes** y luego seleccione **Borrar todas las cachés de NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-144">In Visual Studio 2017, use the **Tools > NuGet Package Manager > Package Manager Settings** menu command, then select **Clear All NuGet Cache(s)**.</span></span> <span data-ttu-id="5b2c0-145">La administración de la memoria caché no está actualmente disponible a través de la consola del Administrador de paquetes.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-145">Managing the cache isn't presently available through the Package Manager Console.</span></span> <span data-ttu-id="5b2c0-146">En Visual Studio 2015, en su lugar use los comandos de la CLI.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-146">In Visual Studio 2015, use the CLI commands instead.</span></span>

![Comando de opciones de NuGet para borrar memorias caché](media/options-clear-caches.png)

## <a name="troubleshooting-errors"></a><span data-ttu-id="5b2c0-148">Solución de problemas de errores</span><span class="sxs-lookup"><span data-stu-id="5b2c0-148">Troubleshooting errors</span></span>

<span data-ttu-id="5b2c0-149">Se pueden producir los siguientes errores al usar `nuget locals` o `dotnet nuget locals`:</span><span class="sxs-lookup"><span data-stu-id="5b2c0-149">The following errors can occur when using `nuget locals` or `dotnet nuget locals`:</span></span>

- <span data-ttu-id="5b2c0-150">*Error: El proceso no puede obtener acceso al archivo porque otro proceso <package> lo está utilizando* o *Error al borrar los recursos locales: no se pueden eliminar uno o varios archivos*.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-150">*Error: The process cannot access the file <package> because it is being used by another process* or *Clearing local resources failed: Unable to delete one or more files*</span></span>

    <span data-ttu-id="5b2c0-151">Uno o varios archivos de la carpeta están en uso por otro proceso; por ejemplo, se abre un proyecto de Visual Studio que hace referencia a paquetes de la carpeta *global-packages*.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-151">One or more files in the folder are in use by another process; for example, a Visual Studio project is open that refers to packages in the *global-packages* folder.</span></span> <span data-ttu-id="5b2c0-152">Cierre los procesos y e inténtelo de nuevo.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-152">Close those processes and try again.</span></span>

- <span data-ttu-id="5b2c0-153">*Error: se ha denegado el acceso a la ruta de acceso <path>* o *el directorio no está vacío*.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-153">*Error: Access to the path <path> is denied* or *The directory is not empty*</span></span>

    <span data-ttu-id="5b2c0-154">No tiene permiso para eliminar archivos en la caché.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-154">You don't have permission to delete files in the cache.</span></span> <span data-ttu-id="5b2c0-155">Si es posible, cambie los permisos de carpeta e inténtelo de nuevo.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-155">Change the folder permissions, if possible, and try again.</span></span> <span data-ttu-id="5b2c0-156">Si no, póngase en contacto con el administrador del sistema.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-156">Otherwise, contact your system administrator.</span></span>

- <span data-ttu-id="5b2c0-157">*Error: la ruta de acceso especificada, el nombre de archivo o ambos son demasiado largos. El nombre de archivo completo debe ser inferior a 260 caracteres y el nombre del directorio debe ser inferior a 248*.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-157">*Error: The specified path, file name, or both are too long. The fully qualified file name must be less than 260 characters, and the directory name must be less than 248 characters.*</span></span>

    <span data-ttu-id="5b2c0-158">Acorte los nombres de carpeta e inténtelo de nuevo.</span><span class="sxs-lookup"><span data-stu-id="5b2c0-158">Shorten the folder names and try again.</span></span>