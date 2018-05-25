---
title: pack y restore de NuGet como destinos de MSBuild
description: pack y restore de NuGet pueden trabajar directamente como destinos de MSBuild con NuGet 4.0 y versiones posteriores.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 03/23/2018
ms.topic: conceptual
ms.openlocfilehash: 00d763bcfdd2f3db50378a1e7774eae7a2e1fcd1
ms.sourcegitcommit: 00c4c809c69c16fcf4d81012eb53ea22f0691d0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="nuget-pack-and-restore-as-msbuild-targets"></a><span data-ttu-id="c8f30-103">pack y restore de NuGet como destinos de MSBuild</span><span class="sxs-lookup"><span data-stu-id="c8f30-103">NuGet pack and restore as MSBuild targets</span></span>

<span data-ttu-id="c8f30-104">*NuGet 4.0 y versiones posteriores*</span><span class="sxs-lookup"><span data-stu-id="c8f30-104">*NuGet 4.0+*</span></span>

<span data-ttu-id="c8f30-105">Con el formato PackageReference, NuGet 4.0 + puede almacenar los metadatos de todos los manifiestos directamente en un archivo de proyecto, en lugar de usar un archivo `.nuspec` aparte.</span><span class="sxs-lookup"><span data-stu-id="c8f30-105">With the PackageReference format, NuGet 4.0+ can store all manifest metadata directly within a project file rather than using a separate `.nuspec` file.</span></span>

<span data-ttu-id="c8f30-106">Con MSBuild 15.1 y versiones posteriores, NuGet es también un ciudadano de MSBuild de primera clase con los destinos `pack` y `restore` como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="c8f30-106">With MSBuild 15.1+, NuGet is also a first-class MSBuild citizen with the `pack` and `restore` targets as described below.</span></span> <span data-ttu-id="c8f30-107">Estos destinos permiten trabajar con NuGet como lo haría con cualquier otra tarea o destino de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c8f30-107">These targets allow you to work with NuGet as you would with any other MSBuild task or target.</span></span> <span data-ttu-id="c8f30-108">(Para NuGet 3.x y versiones anteriores, los comandos [pack](../tools/cli-ref-pack.md) y [restore](../tools/cli-ref-restore.md) se usan a través de la CLI de NuGet en su lugar).</span><span class="sxs-lookup"><span data-stu-id="c8f30-108">(For NuGet 3.x and earlier, you use the [pack](../tools/cli-ref-pack.md) and [restore](../tools/cli-ref-restore.md) commands through the NuGet CLI instead.)</span></span>

## <a name="target-build-order"></a><span data-ttu-id="c8f30-109">Orden de compilación de destinos</span><span class="sxs-lookup"><span data-stu-id="c8f30-109">Target build order</span></span>

<span data-ttu-id="c8f30-110">Dado que `pack` y `restore` son destinos de MSBuild, puede tener acceso a ellos para mejorar el flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="c8f30-110">Because `pack` and `restore` are  MSBuild targets, you can access them to enhance your workflow.</span></span> <span data-ttu-id="c8f30-111">Por ejemplo, supongamos que quiere copiar el paquete en un recurso compartido de red después de empaquetarlo.</span><span class="sxs-lookup"><span data-stu-id="c8f30-111">For example, let’s say you want to copy your package to a network share after packing it.</span></span> <span data-ttu-id="c8f30-112">Puede hacer esto si agrega lo siguiente al archivo de proyecto:</span><span class="sxs-lookup"><span data-stu-id="c8f30-112">You can do that by adding the following in your project file:</span></span>

```xml
<Target Name="CopyPackage" AfterTargets="Pack">
  <Copy
    SourceFiles="$(OutputPath)..\$(PackageId).$(PackageVersion).nupkg"
    DestinationFolder="\\myshare\packageshare\"
    />
</Target>
```

<span data-ttu-id="c8f30-113">De forma similar, puede escribir una tarea de MSBuild, su propio destino y usar propiedades de NuGet en la tarea de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c8f30-113">Similarly, you can write an MSBuild task, write your own target and consume NuGet properties in the MSBuild task.</span></span>

## <a name="pack-target"></a><span data-ttu-id="c8f30-114">Destino de pack</span><span class="sxs-lookup"><span data-stu-id="c8f30-114">pack target</span></span>

<span data-ttu-id="c8f30-115">Para los proyectos de .NET estándar con el formato PackageReference, utilizando `msbuild /t:pack` dibuja entradas del archivo de proyecto debe utilizar para crear un paquete de NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8f30-115">For .NET Standard projects using the PackageReference format, using `msbuild /t:pack` draws inputs from the project file to use in creating a NuGet package.</span></span>

<span data-ttu-id="c8f30-116">En la tabla siguiente se describen las propiedades de MSBuild que se pueden agregar a un archivo de proyecto en el primer nodo `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-116">The table below describes the MSBuild properties that can be added to a project file within the first `<PropertyGroup>` node.</span></span> <span data-ttu-id="c8f30-117">Puede realizar estas modificaciones fácilmente en Visual Studio 2017 y después haciendo clic con el botón derecho en el proyecto y seleccionando **Editar {nombre_proyecto}** en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="c8f30-117">You can make these edits easily in Visual Studio 2017 and later by right-clicking the project and selecting **Edit {project_name}** on the context menu.</span></span> <span data-ttu-id="c8f30-118">Para mayor comodidad, la tabla se organiza por la propiedad equivalente en un [archivo `.nuspec`](../reference/nuspec.md).</span><span class="sxs-lookup"><span data-stu-id="c8f30-118">For convenience the table is organized by the equivalent property in a [`.nuspec` file](../reference/nuspec.md).</span></span>

<span data-ttu-id="c8f30-119">Tenga en cuenta que las propiedades `Owners` y `Summary` de `.nuspec` no son compatibles con MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c8f30-119">Note that the `Owners` and `Summary` properties from `.nuspec` are not supported with MSBuild.</span></span>

| <span data-ttu-id="c8f30-120">Valor de atributo/NuSpec</span><span class="sxs-lookup"><span data-stu-id="c8f30-120">Attribute/NuSpec Value</span></span> | <span data-ttu-id="c8f30-121">Propiedad de MSBuild</span><span class="sxs-lookup"><span data-stu-id="c8f30-121">MSBuild Property</span></span> | <span data-ttu-id="c8f30-122">Default</span><span class="sxs-lookup"><span data-stu-id="c8f30-122">Default</span></span> | <span data-ttu-id="c8f30-123">Notas</span><span class="sxs-lookup"><span data-stu-id="c8f30-123">Notes</span></span> |
|--------|--------|--------|--------|
| <span data-ttu-id="c8f30-124">Id.</span><span class="sxs-lookup"><span data-stu-id="c8f30-124">Id</span></span> | <span data-ttu-id="c8f30-125">PackageId</span><span class="sxs-lookup"><span data-stu-id="c8f30-125">PackageId</span></span> | <span data-ttu-id="c8f30-126">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="c8f30-126">AssemblyName</span></span> | <span data-ttu-id="c8f30-127">$(NombreDeEnsamblado) de MSBuild</span><span class="sxs-lookup"><span data-stu-id="c8f30-127">$(AssemblyName) from MSBuild</span></span> |
| <span data-ttu-id="c8f30-128">Versión</span><span class="sxs-lookup"><span data-stu-id="c8f30-128">Version</span></span> | <span data-ttu-id="c8f30-129">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="c8f30-129">PackageVersion</span></span> | <span data-ttu-id="c8f30-130">Versión</span><span class="sxs-lookup"><span data-stu-id="c8f30-130">Version</span></span> | <span data-ttu-id="c8f30-131">Esto es compatible con semver, por ejemplo, "1.0.0", "1.0.0-beta" o "1.0.0-beta-00345"</span><span class="sxs-lookup"><span data-stu-id="c8f30-131">This is semver compatible, for example “1.0.0”, “1.0.0-beta”, or “1.0.0-beta-00345”</span></span> |
| <span data-ttu-id="c8f30-132">VersionPrefix</span><span class="sxs-lookup"><span data-stu-id="c8f30-132">VersionPrefix</span></span> | <span data-ttu-id="c8f30-133">PackageVersionPrefix</span><span class="sxs-lookup"><span data-stu-id="c8f30-133">PackageVersionPrefix</span></span> | <span data-ttu-id="c8f30-134">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-134">empty</span></span> | <span data-ttu-id="c8f30-135">Al establecer PackageVersion se sobrescribe PackageVersionPrefix.</span><span class="sxs-lookup"><span data-stu-id="c8f30-135">Setting PackageVersion overwrites PackageVersionPrefix</span></span> |
| <span data-ttu-id="c8f30-136">VersionSuffix</span><span class="sxs-lookup"><span data-stu-id="c8f30-136">VersionSuffix</span></span> | <span data-ttu-id="c8f30-137">PackageVersionSuffix</span><span class="sxs-lookup"><span data-stu-id="c8f30-137">PackageVersionSuffix</span></span> | <span data-ttu-id="c8f30-138">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-138">empty</span></span> | <span data-ttu-id="c8f30-139">$(VersionSuffix) de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c8f30-139">$(VersionSuffix) from MSBuild.</span></span> <span data-ttu-id="c8f30-140">Al establecer PackageVersion se sobrescribe PackageVersionSuffix.</span><span class="sxs-lookup"><span data-stu-id="c8f30-140">Setting PackageVersion overwrites PackageVersionSuffix</span></span> |
| <span data-ttu-id="c8f30-141">Authors</span><span class="sxs-lookup"><span data-stu-id="c8f30-141">Authors</span></span> | <span data-ttu-id="c8f30-142">Authors</span><span class="sxs-lookup"><span data-stu-id="c8f30-142">Authors</span></span> | <span data-ttu-id="c8f30-143">Nombre del usuario actual</span><span class="sxs-lookup"><span data-stu-id="c8f30-143">Username of the current user</span></span> | |
| <span data-ttu-id="c8f30-144">Owners</span><span class="sxs-lookup"><span data-stu-id="c8f30-144">Owners</span></span> | <span data-ttu-id="c8f30-145">N/D</span><span class="sxs-lookup"><span data-stu-id="c8f30-145">N/A</span></span> | <span data-ttu-id="c8f30-146">No está presente en el archivo NuSpec</span><span class="sxs-lookup"><span data-stu-id="c8f30-146">Not present in NuSpec</span></span> | |
| <span data-ttu-id="c8f30-147">Title</span><span class="sxs-lookup"><span data-stu-id="c8f30-147">Title</span></span> | <span data-ttu-id="c8f30-148">Title</span><span class="sxs-lookup"><span data-stu-id="c8f30-148">Title</span></span> | <span data-ttu-id="c8f30-149">El identificador de paquete</span><span class="sxs-lookup"><span data-stu-id="c8f30-149">The PackageId</span></span>| |
| <span data-ttu-id="c8f30-150">Descripción</span><span class="sxs-lookup"><span data-stu-id="c8f30-150">Description</span></span> | <span data-ttu-id="c8f30-151">Descripción</span><span class="sxs-lookup"><span data-stu-id="c8f30-151">Description</span></span> | <span data-ttu-id="c8f30-152">"Descripción del paquete"</span><span class="sxs-lookup"><span data-stu-id="c8f30-152">"Package Description"</span></span> | |
| <span data-ttu-id="c8f30-153">Copyright</span><span class="sxs-lookup"><span data-stu-id="c8f30-153">Copyright</span></span> | <span data-ttu-id="c8f30-154">Copyright</span><span class="sxs-lookup"><span data-stu-id="c8f30-154">Copyright</span></span> | <span data-ttu-id="c8f30-155">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-155">empty</span></span> | |
| <span data-ttu-id="c8f30-156">RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="c8f30-156">RequireLicenseAcceptance</span></span> | <span data-ttu-id="c8f30-157">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="c8f30-157">PackageRequireLicenseAcceptance</span></span> | <span data-ttu-id="c8f30-158">False</span><span class="sxs-lookup"><span data-stu-id="c8f30-158">false</span></span> | |
| <span data-ttu-id="c8f30-159">LicenseUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-159">LicenseUrl</span></span> | <span data-ttu-id="c8f30-160">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-160">PackageLicenseUrl</span></span> | <span data-ttu-id="c8f30-161">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-161">empty</span></span> | |
| <span data-ttu-id="c8f30-162">ProjectUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-162">ProjectUrl</span></span> | <span data-ttu-id="c8f30-163">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-163">PackageProjectUrl</span></span> | <span data-ttu-id="c8f30-164">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-164">empty</span></span> | |
| <span data-ttu-id="c8f30-165">IconUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-165">IconUrl</span></span> | <span data-ttu-id="c8f30-166">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-166">PackageIconUrl</span></span> | <span data-ttu-id="c8f30-167">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-167">empty</span></span> | |
| <span data-ttu-id="c8f30-168">Etiquetas</span><span class="sxs-lookup"><span data-stu-id="c8f30-168">Tags</span></span> | <span data-ttu-id="c8f30-169">PackageTags</span><span class="sxs-lookup"><span data-stu-id="c8f30-169">PackageTags</span></span> | <span data-ttu-id="c8f30-170">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-170">empty</span></span> | <span data-ttu-id="c8f30-171">Las etiquetas están delimitadas mediante punto y coma.</span><span class="sxs-lookup"><span data-stu-id="c8f30-171">Tags are semi-colon delimited.</span></span> |
| <span data-ttu-id="c8f30-172">ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c8f30-172">ReleaseNotes</span></span> | <span data-ttu-id="c8f30-173">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c8f30-173">PackageReleaseNotes</span></span> | <span data-ttu-id="c8f30-174">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-174">empty</span></span> | |
| <span data-ttu-id="c8f30-175">Url del repositorio</span><span class="sxs-lookup"><span data-stu-id="c8f30-175">Repository/Url</span></span> | <span data-ttu-id="c8f30-176">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-176">RepositoryUrl</span></span> | <span data-ttu-id="c8f30-177">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-177">empty</span></span> | <span data-ttu-id="c8f30-178">Dirección URL de repositorio que se utiliza para clonar o recuperar el código fuente.</span><span class="sxs-lookup"><span data-stu-id="c8f30-178">Repository URL used to clone or retrieve source code.</span></span> <span data-ttu-id="c8f30-179">Ejemplo: *https://github.com/NuGet/NuGet.Client.git*</span><span class="sxs-lookup"><span data-stu-id="c8f30-179">Example: *https://github.com/NuGet/NuGet.Client.git*</span></span> |
| <span data-ttu-id="c8f30-180">/ Tipo de repositorio</span><span class="sxs-lookup"><span data-stu-id="c8f30-180">Repository/Type</span></span> | <span data-ttu-id="c8f30-181">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="c8f30-181">RepositoryType</span></span> | <span data-ttu-id="c8f30-182">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-182">empty</span></span> | <span data-ttu-id="c8f30-183">Tipo de repositorio.</span><span class="sxs-lookup"><span data-stu-id="c8f30-183">Repository type.</span></span> <span data-ttu-id="c8f30-184">Ejemplos: *git*, *tfs*.</span><span class="sxs-lookup"><span data-stu-id="c8f30-184">Examples: *git*, *tfs*.</span></span> |
| <span data-ttu-id="c8f30-185">Rama del repositorio</span><span class="sxs-lookup"><span data-stu-id="c8f30-185">Repository/Branch</span></span> | <span data-ttu-id="c8f30-186">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="c8f30-186">RepositoryBranch</span></span> | <span data-ttu-id="c8f30-187">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-187">empty</span></span> | <span data-ttu-id="c8f30-188">Información de rama del repositorio opcional.</span><span class="sxs-lookup"><span data-stu-id="c8f30-188">Optional repository branch information.</span></span> <span data-ttu-id="c8f30-189">*RepositoryUrl* también se debe especificar para que esta propiedad que se van a incluir.</span><span class="sxs-lookup"><span data-stu-id="c8f30-189">*RepositoryUrl* must also be specified for this property to be included.</span></span> <span data-ttu-id="c8f30-190">Ejemplo: *maestro* (NuGet 4.7.0+)</span><span class="sxs-lookup"><span data-stu-id="c8f30-190">Example: *master* (NuGet 4.7.0+)</span></span> |
| <span data-ttu-id="c8f30-191">Repositorio/Commit</span><span class="sxs-lookup"><span data-stu-id="c8f30-191">Repository/Commit</span></span> | <span data-ttu-id="c8f30-192">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="c8f30-192">RepositoryCommit</span></span> | <span data-ttu-id="c8f30-193">vacío</span><span class="sxs-lookup"><span data-stu-id="c8f30-193">empty</span></span> | <span data-ttu-id="c8f30-194">Confirmación de repositorio opcional o conjunto de cambios para indicar que el paquete de origen que se generó.</span><span class="sxs-lookup"><span data-stu-id="c8f30-194">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="c8f30-195">*RepositoryUrl* también se debe especificar para que esta propiedad que se van a incluir.</span><span class="sxs-lookup"><span data-stu-id="c8f30-195">*RepositoryUrl* must also be specified for this property to be included.</span></span> <span data-ttu-id="c8f30-196">Ejemplo: *0e4d1b598f350b3dc675018d539114d1328189ef* (NuGet 4.7.0+)</span><span class="sxs-lookup"><span data-stu-id="c8f30-196">Example: *0e4d1b598f350b3dc675018d539114d1328189ef* (NuGet 4.7.0+)</span></span> |
| <span data-ttu-id="c8f30-197">PackageType</span><span class="sxs-lookup"><span data-stu-id="c8f30-197">PackageType</span></span> | `<PackageType>DotNetCliTool, 1.0.0.0;Dependency, 2.0.0.0</PackageType>` | | |
| <span data-ttu-id="c8f30-198">Resumen</span><span class="sxs-lookup"><span data-stu-id="c8f30-198">Summary</span></span> | <span data-ttu-id="c8f30-199">No compatibles</span><span class="sxs-lookup"><span data-stu-id="c8f30-199">Not supported</span></span> | | |

### <a name="pack-target-inputs"></a><span data-ttu-id="c8f30-200">Entradas de destino de pack</span><span class="sxs-lookup"><span data-stu-id="c8f30-200">pack target inputs</span></span>

- <span data-ttu-id="c8f30-201">IsPackable</span><span class="sxs-lookup"><span data-stu-id="c8f30-201">IsPackable</span></span>
- <span data-ttu-id="c8f30-202">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="c8f30-202">PackageVersion</span></span>
- <span data-ttu-id="c8f30-203">PackageId</span><span class="sxs-lookup"><span data-stu-id="c8f30-203">PackageId</span></span>
- <span data-ttu-id="c8f30-204">Authors</span><span class="sxs-lookup"><span data-stu-id="c8f30-204">Authors</span></span>
- <span data-ttu-id="c8f30-205">Descripción</span><span class="sxs-lookup"><span data-stu-id="c8f30-205">Description</span></span>
- <span data-ttu-id="c8f30-206">Copyright</span><span class="sxs-lookup"><span data-stu-id="c8f30-206">Copyright</span></span>
- <span data-ttu-id="c8f30-207">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="c8f30-207">PackageRequireLicenseAcceptance</span></span>
- <span data-ttu-id="c8f30-208">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="c8f30-208">DevelopmentDependency</span></span>
- <span data-ttu-id="c8f30-209">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-209">PackageLicenseUrl</span></span>
- <span data-ttu-id="c8f30-210">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-210">PackageProjectUrl</span></span>
- <span data-ttu-id="c8f30-211">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-211">PackageIconUrl</span></span>
- <span data-ttu-id="c8f30-212">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c8f30-212">PackageReleaseNotes</span></span>
- <span data-ttu-id="c8f30-213">PackageTags</span><span class="sxs-lookup"><span data-stu-id="c8f30-213">PackageTags</span></span>
- <span data-ttu-id="c8f30-214">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="c8f30-214">PackageOutputPath</span></span>
- <span data-ttu-id="c8f30-215">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="c8f30-215">IncludeSymbols</span></span>
- <span data-ttu-id="c8f30-216">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="c8f30-216">IncludeSource</span></span>
- <span data-ttu-id="c8f30-217">PackageTypes</span><span class="sxs-lookup"><span data-stu-id="c8f30-217">PackageTypes</span></span>
- <span data-ttu-id="c8f30-218">IsTool</span><span class="sxs-lookup"><span data-stu-id="c8f30-218">IsTool</span></span>
- <span data-ttu-id="c8f30-219">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-219">RepositoryUrl</span></span>
- <span data-ttu-id="c8f30-220">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="c8f30-220">RepositoryType</span></span>
- <span data-ttu-id="c8f30-221">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="c8f30-221">RepositoryBranch</span></span>
- <span data-ttu-id="c8f30-222">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="c8f30-222">RepositoryCommit</span></span>
- <span data-ttu-id="c8f30-223">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="c8f30-223">NoPackageAnalysis</span></span>
- <span data-ttu-id="c8f30-224">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="c8f30-224">MinClientVersion</span></span>
- <span data-ttu-id="c8f30-225">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="c8f30-225">IncludeBuildOutput</span></span>
- <span data-ttu-id="c8f30-226">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="c8f30-226">IncludeContentInPack</span></span>
- <span data-ttu-id="c8f30-227">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="c8f30-227">BuildOutputTargetFolder</span></span>
- <span data-ttu-id="c8f30-228">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="c8f30-228">ContentTargetFolders</span></span>
- <span data-ttu-id="c8f30-229">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="c8f30-229">NuspecFile</span></span>
- <span data-ttu-id="c8f30-230">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="c8f30-230">NuspecBasePath</span></span>
- <span data-ttu-id="c8f30-231">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="c8f30-231">NuspecProperties</span></span>

## <a name="pack-scenarios"></a><span data-ttu-id="c8f30-232">Escenarios de pack</span><span class="sxs-lookup"><span data-stu-id="c8f30-232">pack scenarios</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="c8f30-233">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="c8f30-233">PackageIconUrl</span></span>

<span data-ttu-id="c8f30-234">Como parte del cambio para [NuGet problema 352](https://github.com/NuGet/Home/issues/352), `PackageIconUrl` finalmente se cambiarán a `PackageIconUri` y puede ser una ruta de acceso relativa a un archivo de icono que se incluirán en la raíz del paquete resultante.</span><span class="sxs-lookup"><span data-stu-id="c8f30-234">As part of the change for [NuGet Issue 352](https://github.com/NuGet/Home/issues/352), `PackageIconUrl` will eventually be changed to `PackageIconUri` and can be relative path to a icon file which will included at the root of the resulting package.</span></span>

### <a name="output-assemblies"></a><span data-ttu-id="c8f30-235">Ensamblados de salida</span><span class="sxs-lookup"><span data-stu-id="c8f30-235">Output assemblies</span></span>

<span data-ttu-id="c8f30-236">`nuget pack` copia los archivos de salida con las extensiones `.exe`, `.dll`, `.xml`, `.winmd`, `.json` y `.pri`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-236">`nuget pack` copies output files with extensions `.exe`, `.dll`, `.xml`, `.winmd`, `.json`, and `.pri`.</span></span> <span data-ttu-id="c8f30-237">Los archivos de salida que se copian dependen de lo que proporciona MSBuild desde el destino `BuiltOutputProjectGroup`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-237">The output files that are copied depend on what MSBuild provides from the `BuiltOutputProjectGroup` target.</span></span>

<span data-ttu-id="c8f30-238">Hay dos propiedades de MSBuild que se pueden usar en el archivo de proyecto o la línea de comandos para controlar dónde van los ensamblados de salida:</span><span class="sxs-lookup"><span data-stu-id="c8f30-238">There are two MSBuild  properties that you can use in your project file or command line to control where output assemblies go:</span></span>

- <span data-ttu-id="c8f30-239">`IncludeBuildOutput`: un valor booleano que determina si los ensamblados de salida de compilación deben incluirse en el paquete.</span><span class="sxs-lookup"><span data-stu-id="c8f30-239">`IncludeBuildOutput`: A boolean that determines whether the build output assemblies should be included in the package.</span></span>
- <span data-ttu-id="c8f30-240">`BuildOutputTargetFolder`: especifica la carpeta en la que se deben colocar los ensamblados de salida.</span><span class="sxs-lookup"><span data-stu-id="c8f30-240">`BuildOutputTargetFolder`: Specifies the folder in which the output assemblies should be placed.</span></span> <span data-ttu-id="c8f30-241">Los ensamblados de salida (y otros archivos de salida) se copian en sus respectivas carpetas de marco.</span><span class="sxs-lookup"><span data-stu-id="c8f30-241">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="package-references"></a><span data-ttu-id="c8f30-242">Referencias de paquete</span><span class="sxs-lookup"><span data-stu-id="c8f30-242">Package references</span></span>

<span data-ttu-id="c8f30-243">Vea [Referencias de paquete en archivos de proyecto](../consume-packages/package-references-in-project-files.md).</span><span class="sxs-lookup"><span data-stu-id="c8f30-243">See [Package References in Project Files](../consume-packages/package-references-in-project-files.md).</span></span>

### <a name="project-to-project-references"></a><span data-ttu-id="c8f30-244">Referencias entre proyectos</span><span class="sxs-lookup"><span data-stu-id="c8f30-244">Project to project references</span></span>

<span data-ttu-id="c8f30-245">Las referencias entre proyectos se consideran de forma predeterminada como referencias de paquetes NuGet, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c8f30-245">Project to project references are considered by default as nuget package references, for example:</span></span>

```xml
<ProjectReference Include="..\UwpLibrary2\UwpLibrary2.csproj"/>
```

<span data-ttu-id="c8f30-246">También puede agregar los metadatos siguientes a la referencia de proyecto:</span><span class="sxs-lookup"><span data-stu-id="c8f30-246">You can also add the following metadata to your project reference:</span></span>

```xml
<IncludeAssets>
<ExcludeAssets>
<PrivateAssets>
```

### <a name="including-content-in-a-package"></a><span data-ttu-id="c8f30-247">Inclusión de contenido en un paquete</span><span class="sxs-lookup"><span data-stu-id="c8f30-247">Including content in a package</span></span>

<span data-ttu-id="c8f30-248">Para incluir contenido, agregue metadatos adicionales al elemento `<Content>` existente.</span><span class="sxs-lookup"><span data-stu-id="c8f30-248">To include content, add extra metadata to the existing `<Content>` item.</span></span> <span data-ttu-id="c8f30-249">De forma predeterminada todos los elementos de tipo "Content" se incluyen en el paquete a menos que los reemplace con entradas como la siguiente:</span><span class="sxs-lookup"><span data-stu-id="c8f30-249">By default everything of type "Content" gets included in the package unless you override with entries like the following:</span></span>

 ```xml
<Content Include="..\win7-x64\libuv.txt">
  <Pack>false</Pack>
</Content>
 ```

<span data-ttu-id="c8f30-250">De forma predeterminada, todo el contenido se agrega a la raíz de la carpeta `content` y `contentFiles\any\<target_framework>` dentro de un paquete y se conserva la estructura de carpetas relativa, a menos que se especifique una ruta de acceso de paquete:</span><span class="sxs-lookup"><span data-stu-id="c8f30-250">By default, everything gets added to the root of the `content` and `contentFiles\any\<target_framework>` folder within a package and preserves the relative folder structure, unless you specify a package path:</span></span>

```xml
<Content Include="..\win7-x64\libuv.txt">
  <Pack>true</Pack>
  <PackagePath>content\myfiles\</PackagePath>
</Content>
```

<span data-ttu-id="c8f30-251">Si quiere copiar todo el contenido a una carpeta raíz determinada (en lugar de `content` y `contentFiles`), puede usar la propiedad `ContentTargetFolders` de MSBuild, cuyo valor predeterminado es "content;contentFiles", pero que se puede establecer en cualquier otro nombre de carpeta.</span><span class="sxs-lookup"><span data-stu-id="c8f30-251">If you want to copy all your content to only a specific root folder(s) (instead of `content` and `contentFiles` both), you can use the MSBuild property `ContentTargetFolders`, which defaults to "content;contentFiles" but can be set to any other folder names.</span></span> <span data-ttu-id="c8f30-252">Tenga en cuenta que si solo especifica "contentFiles" en `ContentTargetFolders`, los archivos se colocan en `contentFiles\any\<target_framework>` o `contentFiles\<language>\<target_framework>` en función de `buildAction`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-252">Note that just specifying "contentFiles" in `ContentTargetFolders` puts files under `contentFiles\any\<target_framework>` or `contentFiles\<language>\<target_framework>` based on `buildAction`.</span></span>

<span data-ttu-id="c8f30-253">`PackagePath` puede ser un conjunto de rutas de acceso de destino delimitadas por punto y coma.</span><span class="sxs-lookup"><span data-stu-id="c8f30-253">`PackagePath` can be a semicolon-delimited set of target paths.</span></span> <span data-ttu-id="c8f30-254">Especificar una ruta de acceso de paquete vacía agregaría el archivo a la raíz del paquete.</span><span class="sxs-lookup"><span data-stu-id="c8f30-254">Specifying an empty package path would add the file to the root of the package.</span></span> <span data-ttu-id="c8f30-255">Por ejemplo, en el ejemplo siguiente se agrega `libuv.txt` a `content\myfiles`, `content\samples` y la raíz del paquete:</span><span class="sxs-lookup"><span data-stu-id="c8f30-255">For example, the following adds `libuv.txt` to `content\myfiles`, `content\samples`, and the package root:</span></span>

```xml
<Content Include="..\win7-x64\libuv.txt">
  <Pack>true</Pack>
  <PackagePath>content\myfiles;content\sample;;</PackagePath>
</Content>
```

<span data-ttu-id="c8f30-256">También hay una propiedad `$(IncludeContentInPack)` de MSBuild, cuyo valor predeterminado es `true`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-256">There is also an MSBuild property `$(IncludeContentInPack)`, which defaults to `true`.</span></span> <span data-ttu-id="c8f30-257">Si esto se establece en `false` en cualquier proyecto, el contenido de ese proyecto no se incluye en el paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8f30-257">If this is set to `false` on any project, then the content from that project are not included in the nuget package.</span></span>

<span data-ttu-id="c8f30-258">Otros metadatos específicos del paquete que se pueden establecer en cualquiera de los elementos anteriores incluyen ```<PackageCopyToOutput>``` y ```<PackageFlatten>```, que establece los valores ```CopyToOutput``` y ```Flatten``` en la entrada ```contentFiles``` del archivo nuspec de salida.</span><span class="sxs-lookup"><span data-stu-id="c8f30-258">Other pack specific metadata that you can set on any of the above items includes ```<PackageCopyToOutput>``` and ```<PackageFlatten>``` which sets ```CopyToOutput``` and ```Flatten``` values on the ```contentFiles``` entry in the output nuspec.</span></span>

> [!Note]
> <span data-ttu-id="c8f30-259">Además de los elementos Content, los metadatos `<Pack>` y `<PackagePath>` también se pueden establecer en archivos con una acción de compilación Compile, EmbeddedResource, ApplicationDefinition, Page, Resource, SplashScreen, DesignData, DesignDataWithDesignTimeCreatableTypes, CodeAnalysisDictionary, AndroidAsset, AndroidResource, BundleResource o None.</span><span class="sxs-lookup"><span data-stu-id="c8f30-259">Apart from Content items, the `<Pack>` and `<PackagePath>` metadata can also be set on files with a build action of Compile, EmbeddedResource, ApplicationDefinition, Page, Resource, SplashScreen, DesignData, DesignDataWithDesignTimeCreateableTypes, CodeAnalysisDictionary, AndroidAsset, AndroidResource, BundleResource or None.</span></span>
>
> <span data-ttu-id="c8f30-260">Para que el comando pack anexe el nombre de archivo a la ruta de acceso del paquete cuando se usan patrones globales, la ruta de acceso del paquete debe terminar con el carácter separador de carpeta; en caso contrario, la ruta de acceso del paquete se trata como la ruta de acceso completa, incluido el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="c8f30-260">For pack to append the filename to your package path when using globbing patterns, your package path must end with the folder separator character, otherwise the package path is treated as the full path including the file name.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="c8f30-261">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="c8f30-261">IncludeSymbols</span></span>

<span data-ttu-id="c8f30-262">Cuando se usa `MSBuild /t:pack /p:IncludeSymbols=true`, se copian los archivos `.pdb` correspondientes junto con otros archivos de salida (`.dll`, `.exe`, `.winmd`, `.xml`, `.json`, `.pri`).</span><span class="sxs-lookup"><span data-stu-id="c8f30-262">When using `MSBuild /t:pack /p:IncludeSymbols=true`, the corresponding `.pdb` files are copied along with other output files (`.dll`, `.exe`, `.winmd`, `.xml`, `.json`, `.pri`).</span></span> <span data-ttu-id="c8f30-263">Tenga en cuenta que al establecer `IncludeSymbols=true` se crea un paquete estándar *y* un paquete de símbolos.</span><span class="sxs-lookup"><span data-stu-id="c8f30-263">Note that setting `IncludeSymbols=true` creates a regular package *and* a symbols package.</span></span>

### <a name="includesource"></a><span data-ttu-id="c8f30-264">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="c8f30-264">IncludeSource</span></span>

<span data-ttu-id="c8f30-265">Esto equivale a `IncludeSymbols`, salvo que también copia los archivos de código fuente junto con los archivos `.pdb`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-265">This is the same as `IncludeSymbols`, except that it copies source files along with `.pdb` files as well.</span></span> <span data-ttu-id="c8f30-266">Todos los archivos de tipo `Compile` se copian en `src\<ProjectName>\` conservando la estructura de carpetas de ruta de acceso relativa en el paquete resultante.</span><span class="sxs-lookup"><span data-stu-id="c8f30-266">All files of type `Compile` are copied over to `src\<ProjectName>\` preserving the relative path folder structure in the resulting package.</span></span> <span data-ttu-id="c8f30-267">Lo mismo sucede para los archivos de código fuente de cualquier `ProjectReference` en la que `TreatAsPackageReference` se establece en `false`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-267">The same also happens for source files of any `ProjectReference` which has `TreatAsPackageReference` set to `false`.</span></span>

<span data-ttu-id="c8f30-268">Si un archivo de tipo Compile está fuera de la carpeta de proyecto, simplemente se agrega a `src\<ProjectName>\`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-268">If a file of type Compile, is outside the project folder, then it's just added to `src\<ProjectName>\`.</span></span>

### <a name="istool"></a><span data-ttu-id="c8f30-269">IsTool</span><span class="sxs-lookup"><span data-stu-id="c8f30-269">IsTool</span></span>

<span data-ttu-id="c8f30-270">Cuando se usa `MSBuild /t:pack /p:IsTool=true`, todos los archivos de salida, como se especifica en el escenario [Ensamblados de salida](#output-assemblies), se copian en la carpeta `tools` en lugar de la carpeta `lib`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-270">When using `MSBuild /t:pack /p:IsTool=true`, all output files, as specified in the [Output Assemblies](#output-assemblies) scenario, are copied to the `tools` folder instead of the `lib` folder.</span></span> <span data-ttu-id="c8f30-271">Tenga en cuenta que esto es diferente de `DotNetCliTool`, que se especifica estableciendo `PackageType` en el archivo `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-271">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in `.csproj` file.</span></span>

### <a name="packing-using-a-nuspec"></a><span data-ttu-id="c8f30-272">Empaquetado mediante un archivo .nuspec</span><span class="sxs-lookup"><span data-stu-id="c8f30-272">Packing using a .nuspec</span></span>

<span data-ttu-id="c8f30-273">Puede usar un `.nuspec` archivo para empaquetar el proyecto siempre que tenga un archivo de proyecto SDK para importar `NuGet.Build.Tasks.Pack.targets` para que se puede ejecutar la tarea de módulo.</span><span class="sxs-lookup"><span data-stu-id="c8f30-273">You can use a `.nuspec` file to pack your project provided that you have a SDK project file to import `NuGet.Build.Tasks.Pack.targets` so that the pack task can be executed.</span></span> <span data-ttu-id="c8f30-274">Deberá restaurar el proyecto antes de que se puede empaquetar un archivo nuspec.</span><span class="sxs-lookup"><span data-stu-id="c8f30-274">You still need to restore the project before you can pack a nuspec file.</span></span> <span data-ttu-id="c8f30-275">La plataforma de destino del archivo del proyecto es irrelevante y no se utiliza cuando un nuspec de empaquetado.</span><span class="sxs-lookup"><span data-stu-id="c8f30-275">The target framework of the project file is irrelevant and not used when packing a nuspec.</span></span> <span data-ttu-id="c8f30-276">Las tres propiedades de MSBuild siguientes son relevantes para el empaquetado mediante un archivo `.nuspec`:</span><span class="sxs-lookup"><span data-stu-id="c8f30-276">The following three MSBuild properties are relevant to packing using a `.nuspec`:</span></span>

1. <span data-ttu-id="c8f30-277">`NuspecFile`: ruta de acceso relativa o absoluta al archivo `.nuspec` que se usa para el empaquetado.</span><span class="sxs-lookup"><span data-stu-id="c8f30-277">`NuspecFile`: relative or absolute path to the `.nuspec` file being used for packing.</span></span>
1. <span data-ttu-id="c8f30-278">`NuspecProperties`: lista de pares clave=valor separados por punto y coma.</span><span class="sxs-lookup"><span data-stu-id="c8f30-278">`NuspecProperties`: a semicolon-separated list of key=value pairs.</span></span> <span data-ttu-id="c8f30-279">Debido al funcionamiento del análisis de línea de comandos de MSBuild, se deben especificar varias propiedades como se indica a continuación: `/p:NuspecProperties=\"key1=value1;key2=value2\"`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-279">Due to the way MSBuild command-line parsing works, multiple properties must be specified as follows: `/p:NuspecProperties=\"key1=value1;key2=value2\"`.</span></span>  
1. <span data-ttu-id="c8f30-280">`NuspecBasePath`: ruta de acceso base para el archivo `.nuspec`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-280">`NuspecBasePath`: Base path for the `.nuspec` file.</span></span>

<span data-ttu-id="c8f30-281">Si se usa `dotnet.exe` para empaquetar el proyecto, use un comando similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="c8f30-281">If using `dotnet.exe` to pack your project, use a command like the following:</span></span>

```cli
dotnet pack <path to .csproj file> /p:NuspecFile=<path to nuspec file> /p:NuspecProperties=<> /p:NuspecBasePath=<Base path> 
```

<span data-ttu-id="c8f30-282">Si se usa MSBuild para empaquetar el proyecto, use un comando similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="c8f30-282">If using MSBuild to pack your project, use a command like the following:</span></span>

```cli
msbuild /t:pack <path to .csproj file> /p:NuspecFile=<path to nuspec file> /p:NuspecProperties=<> /p:NuspecBasePath=<Base path> 
```

<span data-ttu-id="c8f30-283">Tenga en cuenta que un archivo nuspec mediante dotnet.exe empaquetado o también provoca msbuild para compilar el proyecto de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="c8f30-283">Please note that packing a nuspec using dotnet.exe or msbuild also leads to building the project by default.</span></span> <span data-ttu-id="c8f30-284">Esto se puede evitar pasando ```--no-build``` propiedad dotnet.exe, que es equivalente a establecer ```<NoBuild>true</NoBuild> ``` en el archivo de proyecto, junto con la opción ```<IncludeBuildOutput>false</IncludeBuildOutput> ``` en el archivo de proyecto</span><span class="sxs-lookup"><span data-stu-id="c8f30-284">This can be avoided by passing ```--no-build``` property to dotnet.exe, which is the equivalent of setting ```<NoBuild>true</NoBuild> ``` in your project file, along with setting ```<IncludeBuildOutput>false</IncludeBuildOutput> ``` in the project file</span></span>

<span data-ttu-id="c8f30-285">Un ejemplo de un archivo csproj para empaquetar un archivo nuspec es:</span><span class="sxs-lookup"><span data-stu-id="c8f30-285">An example of a csproj file to pack a nuspec file is:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <NoBuild>true</NoBuild>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <NuspecFile>PATH_TO_NUSPEC_FILE</NuspecFile>
    <NuspecProperties>add nuspec properties here</NuspecProperties>
    <NuspecBasePath>optional to provide</NuspecBasePath>
  </PropertyGroup>
</Project>
```

### <a name="advanced-extension-points-to-create-customized-package"></a><span data-ttu-id="c8f30-286">Advanced puntos de extensión para crear el paquete personalizado</span><span class="sxs-lookup"><span data-stu-id="c8f30-286">Advanced extension points to create customized package</span></span>

<span data-ttu-id="c8f30-287">El `pack` destino proporciona dos puntos de extensión que se ejecutan en la compilación interna, de específicos de framework de destino.</span><span class="sxs-lookup"><span data-stu-id="c8f30-287">The `pack` target provides two extension points that run in the inner, target framework specific build.</span></span> <span data-ttu-id="c8f30-288">Los puntos de extensión se admiten incluido contenido específico de framework de destino y ensamblados en un paquete:</span><span class="sxs-lookup"><span data-stu-id="c8f30-288">The extension points support including target framework specific content and assemblies into a package:</span></span>

- <span data-ttu-id="c8f30-289">`TargetsForTfmSpecificBuildOutput` destino: uso de archivos dentro de la `lib` carpeta o una carpeta que se especifica utilizando `BuildOutputTargetFolder`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-289">`TargetsForTfmSpecificBuildOutput` target: Use for files inside the `lib` folder or a folder specified using `BuildOutputTargetFolder`.</span></span>
- <span data-ttu-id="c8f30-290">`TargetsForTfmSpecificContentInPackage` destino: uso de archivos que están fuera del `BuildOutputTargetFolder`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-290">`TargetsForTfmSpecificContentInPackage` target: Use for files outside the `BuildOutputTargetFolder`.</span></span>

#### <a name="targetsfortfmspecificbuildoutput"></a><span data-ttu-id="c8f30-291">TargetsForTfmSpecificBuildOutput</span><span class="sxs-lookup"><span data-stu-id="c8f30-291">TargetsForTfmSpecificBuildOutput</span></span>

<span data-ttu-id="c8f30-292">Escribir un destino personalizado y especificar este valor como el valor de la `$(TargetsForTfmSpecificBuildOutput)` propiedad.</span><span class="sxs-lookup"><span data-stu-id="c8f30-292">Write a custom target and specify it as the value of the `$(TargetsForTfmSpecificBuildOutput)` property.</span></span> <span data-ttu-id="c8f30-293">Para los archivos que deben entrar en el `BuildOutputTargetFolder` (lib de forma predeterminada), el destino debe escribir esos archivos en el elemento ItemGroup `BuildOutputInPackage` y establecer los dos valores de metadatos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c8f30-293">For any files that need to go into the `BuildOutputTargetFolder` (lib by default), the target should write those files into the ItemGroup `BuildOutputInPackage` and set the following two metadata values:</span></span>

- <span data-ttu-id="c8f30-294">`FinalOutputPath`: La ruta de acceso absoluta del archivo; Si no se proporciona, la identidad se utiliza para evaluar la ruta de acceso de origen.</span><span class="sxs-lookup"><span data-stu-id="c8f30-294">`FinalOutputPath`: The absolute path of the file; if not provided, the Identity is used to evaluate source path.</span></span>
- <span data-ttu-id="c8f30-295">`TargetPath`: (Opcional) establezca cuando el archivo se necesita para pasar a una subcarpeta en `lib\<TargetFramework>` , como ensamblados satélite que afectan en sus carpetas de referencia cultural correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c8f30-295">`TargetPath`:  (Optional) Set when the file needs to go into a subfolder within `lib\<TargetFramework>` , like satellite assemblies that go under their respective culture folders.</span></span> <span data-ttu-id="c8f30-296">El valor predeterminado es el nombre del archivo.</span><span class="sxs-lookup"><span data-stu-id="c8f30-296">Defaults to the name of the file.</span></span>

<span data-ttu-id="c8f30-297">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c8f30-297">Example:</span></span>

```xml
<PropertyGroup>
  <TargetsForTfmSpecificBuildOutput>$(TargetsForTfmSpecificBuildOutput);GetMyPackageFiles</TargetsForTfmSpecificBuildOutput>
</PropertyGroup>

<Target Name="GetMyPackageFiles">
  <ItemGroup>
    <BuildOutputInPackage Include="$(OutputPath)cs\$(AssemblyName).resources.dll">
        <TargetPath>cs</TargetPath>
    </BuildOutputInPackage>
  </ItemGroup>
</Target>
```

#### <a name="targetsfortfmspecificcontentinpackage"></a><span data-ttu-id="c8f30-298">TargetsForTfmSpecificContentInPackage</span><span class="sxs-lookup"><span data-stu-id="c8f30-298">TargetsForTfmSpecificContentInPackage</span></span>

<span data-ttu-id="c8f30-299">Escribir un destino personalizado y especificar este valor como el valor de la `$(TargetsForTfmSpecificContentInPackage)` propiedad.</span><span class="sxs-lookup"><span data-stu-id="c8f30-299">Write a custom target and specify it as the value of the `$(TargetsForTfmSpecificContentInPackage)` property.</span></span> <span data-ttu-id="c8f30-300">Para que los archivos que se incluirán en el paquete, el destino debe escribir esos archivos en el elemento ItemGroup `TfmSpecificPackageFile` y establecer los metadatos opcionales siguientes:</span><span class="sxs-lookup"><span data-stu-id="c8f30-300">For any files to include in the package, the target should write those files into the ItemGroup `TfmSpecificPackageFile` and set the following optional metadata:</span></span>

- <span data-ttu-id="c8f30-301">`PackagePath`: Ruta de acceso donde el archivo deben mostrarse en el paquete.</span><span class="sxs-lookup"><span data-stu-id="c8f30-301">`PackagePath`: Path where the file should be output in the package.</span></span> <span data-ttu-id="c8f30-302">NuGet emite una advertencia si se agrega más de un archivo a la misma ruta de acceso de paquete.</span><span class="sxs-lookup"><span data-stu-id="c8f30-302">NuGet issues a warning if more than one file is added to the same package path.</span></span>
- <span data-ttu-id="c8f30-303">`BuildAction`: La acción de compilación que se asigna al archivo, es necesario sólo si la ruta de acceso del paquete está en el `contentFiles` carpeta.</span><span class="sxs-lookup"><span data-stu-id="c8f30-303">`BuildAction`: The build action to assign to the file, required only if the package path is in the `contentFiles` folder.</span></span> <span data-ttu-id="c8f30-304">El valor predeterminado es "None".</span><span class="sxs-lookup"><span data-stu-id="c8f30-304">Defaults to "None".</span></span>

<span data-ttu-id="c8f30-305">Un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c8f30-305">An example:</span></span>
```xml
<PropertyGroup>
  <TargetsForTfmSpecificContentInPackage>$(TargetsForTfmSpecificContentInPackage);CustomContentTarget</TargetsForTfmSpecificContentInPackage>
</PropertyGroup>

<Target Name=""CustomContentTarget"">
  <ItemGroup>
    <TfmSpecificPackageFile Include=""abc.txt"">
      <PackagePath>mycontent/$(TargetFramework)</PackagePath>
    </TfmSpecificPackageFile>
    <TfmSpecificPackageFile Include=""Extensions/ext.txt"" Condition=""'$(TargetFramework)' == 'net46'"">
      <PackagePath>net46content</PackagePath>
    </TfmSpecificPackageFile>  
  </ItemGroup>
</Target>  
```

## <a name="restore-target"></a><span data-ttu-id="c8f30-306">Destino de restore</span><span class="sxs-lookup"><span data-stu-id="c8f30-306">restore target</span></span>

<span data-ttu-id="c8f30-307">`MSBuild /t:restore` (que `nuget restore` y `dotnet restore` usan con proyectos de .NET Core), restaura los paquetes a los que se hace referencia en el archivo de proyecto como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="c8f30-307">`MSBuild /t:restore` (which `nuget restore` and `dotnet restore` use with .NET Core projects), restores packages referenced in the project file as follows:</span></span>

1. <span data-ttu-id="c8f30-308">Leer todas las referencias entre proyectos</span><span class="sxs-lookup"><span data-stu-id="c8f30-308">Read all project to project references</span></span>
1. <span data-ttu-id="c8f30-309">Leer las propiedades del proyecto para buscar las carpetas y plataformas de destino intermedias</span><span class="sxs-lookup"><span data-stu-id="c8f30-309">Read the project properties to find the intermediate folder and target frameworks</span></span>
1. <span data-ttu-id="c8f30-310">Pasar datos de MSBuild a NuGet.Build.Tasks.dll</span><span class="sxs-lookup"><span data-stu-id="c8f30-310">Pass msbuild data to NuGet.Build.Tasks.dll</span></span>
1. <span data-ttu-id="c8f30-311">Ejecutar la restauración</span><span class="sxs-lookup"><span data-stu-id="c8f30-311">Run restore</span></span>
1. <span data-ttu-id="c8f30-312">Descargar los paquetes</span><span class="sxs-lookup"><span data-stu-id="c8f30-312">Download packages</span></span>
1. <span data-ttu-id="c8f30-313">Escribir el archivo de activos, destinos y propiedades</span><span class="sxs-lookup"><span data-stu-id="c8f30-313">Write assets file, targets, and props</span></span>

<span data-ttu-id="c8f30-314">El `restore` destino funciona **sólo** para los proyectos con el formato PackageReference.</span><span class="sxs-lookup"><span data-stu-id="c8f30-314">The `restore` target works **only** for projects using the PackageReference format.</span></span> <span data-ttu-id="c8f30-315">Lo hace **no** profesional de proyectos que usan el `packages.config` formato; use [restauración de nuget](../tools/cli-ref-restore.md) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="c8f30-315">It does **not** work for projects using the `packages.config` format; use [nuget restore](../tools/cli-ref-restore.md) instead.</span></span>

### <a name="restore-properties"></a><span data-ttu-id="c8f30-316">Restaurar las propiedades</span><span class="sxs-lookup"><span data-stu-id="c8f30-316">Restore properties</span></span>

<span data-ttu-id="c8f30-317">Otra configuración de restauración puede proceder de propiedades de MSBuild en el archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="c8f30-317">Additional restore settings may come from MSBuild properties in the project file.</span></span> <span data-ttu-id="c8f30-318">También se pueden establecer valores desde la línea de comandos mediante el modificador `/p:` (vea los ejemplos siguientes).</span><span class="sxs-lookup"><span data-stu-id="c8f30-318">Values can also be set from the command line using the `/p:` switch (see Examples below).</span></span>

| <span data-ttu-id="c8f30-319">Property</span><span class="sxs-lookup"><span data-stu-id="c8f30-319">Property</span></span> | <span data-ttu-id="c8f30-320">Descripción</span><span class="sxs-lookup"><span data-stu-id="c8f30-320">Description</span></span> |
|--------|--------|
| <span data-ttu-id="c8f30-321">RestoreSources</span><span class="sxs-lookup"><span data-stu-id="c8f30-321">RestoreSources</span></span> | <span data-ttu-id="c8f30-322">Lista delimitada por punto y coma de orígenes de paquetes.</span><span class="sxs-lookup"><span data-stu-id="c8f30-322">Semicolon-delimited list of package sources.</span></span> |
| <span data-ttu-id="c8f30-323">RestorePackagesPath</span><span class="sxs-lookup"><span data-stu-id="c8f30-323">RestorePackagesPath</span></span> | <span data-ttu-id="c8f30-324">Ruta de acceso de la carpeta de paquetes de usuario.</span><span class="sxs-lookup"><span data-stu-id="c8f30-324">User packages folder path.</span></span> |
| <span data-ttu-id="c8f30-325">RestoreDisableParallel</span><span class="sxs-lookup"><span data-stu-id="c8f30-325">RestoreDisableParallel</span></span> | <span data-ttu-id="c8f30-326">Limitar las descargas a una cada vez.</span><span class="sxs-lookup"><span data-stu-id="c8f30-326">Limit downloads to one at a time.</span></span> |
| <span data-ttu-id="c8f30-327">RestoreConfigFile</span><span class="sxs-lookup"><span data-stu-id="c8f30-327">RestoreConfigFile</span></span> | <span data-ttu-id="c8f30-328">Ruta de acceso a un archivo `Nuget.Config` que se va a aplicar.</span><span class="sxs-lookup"><span data-stu-id="c8f30-328">Path to a `Nuget.Config` file to apply.</span></span> |
| <span data-ttu-id="c8f30-329">RestoreNoCache</span><span class="sxs-lookup"><span data-stu-id="c8f30-329">RestoreNoCache</span></span> | <span data-ttu-id="c8f30-330">Si es true, evita el uso de paquetes almacenados en caché.</span><span class="sxs-lookup"><span data-stu-id="c8f30-330">If true, avoids using cached packages.</span></span> <span data-ttu-id="c8f30-331">Vea [administrar los paquetes globales y las carpetas de caché](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span><span class="sxs-lookup"><span data-stu-id="c8f30-331">See [Managing the global packages and cache folders](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span></span> |
| <span data-ttu-id="c8f30-332">RestoreIgnoreFailedSources</span><span class="sxs-lookup"><span data-stu-id="c8f30-332">RestoreIgnoreFailedSources</span></span> | <span data-ttu-id="c8f30-333">Si es true, ignora los orígenes de paquetes que producen errores o faltan.</span><span class="sxs-lookup"><span data-stu-id="c8f30-333">If true, ignores failing or missing package sources.</span></span> |
| <span data-ttu-id="c8f30-334">RestoreTaskAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="c8f30-334">RestoreTaskAssemblyFile</span></span> | <span data-ttu-id="c8f30-335">Ruta de acceso a `NuGet.Build.Tasks.dll`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-335">Path to `NuGet.Build.Tasks.dll`.</span></span> |
| <span data-ttu-id="c8f30-336">RestoreGraphProjectInput</span><span class="sxs-lookup"><span data-stu-id="c8f30-336">RestoreGraphProjectInput</span></span> | <span data-ttu-id="c8f30-337">Lista delimitada por punto y coma de proyectos para restaurar, que debe contener rutas de acceso absolutas.</span><span class="sxs-lookup"><span data-stu-id="c8f30-337">Semicolon-delimited list of projects to restore, which should contain absolute paths.</span></span> |
| <span data-ttu-id="c8f30-338">RestoreOutputPath</span><span class="sxs-lookup"><span data-stu-id="c8f30-338">RestoreOutputPath</span></span> | <span data-ttu-id="c8f30-339">Carpeta de salida, que de forma predeterminada es `obj`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-339">Output folder, defaulting to the `obj` folder.</span></span> |

#### <a name="examples"></a><span data-ttu-id="c8f30-340">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="c8f30-340">Examples</span></span>

<span data-ttu-id="c8f30-341">Línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="c8f30-341">Command line:</span></span>

```cli
msbuild /t:restore /p:RestoreConfigFile=<path>
```

<span data-ttu-id="c8f30-342">Archivo del proyecto:</span><span class="sxs-lookup"><span data-stu-id="c8f30-342">Project file:</span></span>

```xml
<PropertyGroup>
    <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

### <a name="restore-outputs"></a><span data-ttu-id="c8f30-343">Restaurar salidas</span><span class="sxs-lookup"><span data-stu-id="c8f30-343">Restore outputs</span></span>

<span data-ttu-id="c8f30-344">La restauración crea los archivos siguientes en la carpeta `obj` de compilación:</span><span class="sxs-lookup"><span data-stu-id="c8f30-344">Restore creates the following files in the build `obj` folder:</span></span>

| <span data-ttu-id="c8f30-345">Archivo</span><span class="sxs-lookup"><span data-stu-id="c8f30-345">File</span></span> | <span data-ttu-id="c8f30-346">Descripción</span><span class="sxs-lookup"><span data-stu-id="c8f30-346">Description</span></span> |
|--------|--------|
| `project.assets.json` | <span data-ttu-id="c8f30-347">Contiene el gráfico de dependencias de todas las referencias de paquete.</span><span class="sxs-lookup"><span data-stu-id="c8f30-347">Contains the dependency graph of all package references.</span></span> |
| `{projectName}.projectFileExtension.nuget.g.props` | <span data-ttu-id="c8f30-348">Referencias a propiedades de MSBuild incluidas en paquetes</span><span class="sxs-lookup"><span data-stu-id="c8f30-348">References to MSBuild props contained in packages</span></span> |
| `{projectName}.projectFileExtension.nuget.g.targets` | <span data-ttu-id="c8f30-349">Referencias a destinos de MSBuild incluidos en paquetes</span><span class="sxs-lookup"><span data-stu-id="c8f30-349">References to MSBuild targets contained in packages</span></span> |

### <a name="packagetargetfallback"></a><span data-ttu-id="c8f30-350">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c8f30-350">PackageTargetFallback</span></span>

<span data-ttu-id="c8f30-351">El elemento `PackageTargetFallback` permite especificar un conjunto de destinos compatibles que se usarán al restaurar los paquetes.</span><span class="sxs-lookup"><span data-stu-id="c8f30-351">The `PackageTargetFallback` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="c8f30-352">Está diseñado para permitir que los paquetes que usan un [TxM](../reference/target-frameworks.md) de dotnet funcionen con paquetes compatibles que no declaran un TxM de dotnet.</span><span class="sxs-lookup"><span data-stu-id="c8f30-352">It's designed to allow packages that use a dotnet [TxM](../reference/target-frameworks.md) to work with compatible packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="c8f30-353">Es decir, si el proyecto usa el TxM de dotnet, todos los paquetes de los que depende también deben tener un TxM de dotnet, a menos que agregue `<PackageTargetFallback>` al proyecto para permitir que las plataformas que no sean de dotnet sean compatibles con dotnet.</span><span class="sxs-lookup"><span data-stu-id="c8f30-353">That is, if your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="c8f30-354">Por ejemplo, si el proyecto usa el TxM `netstandard1.6` y un paquete dependiente solo contiene `lib/net45/a.dll` y `lib/portable-net45+win81/a.dll`, se producirá un error al compilar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c8f30-354">For example, if the project is using the `netstandard1.6` TxM, and a dependent package contains only `lib/net45/a.dll` and `lib/portable-net45+win81/a.dll`, then the project will fail to build.</span></span> <span data-ttu-id="c8f30-355">Si lo que quiere incluir es el último archivo DLL, puede agregar `PackageTargetFallback` como se indica a continuación para indicar que el archivo DLL `portable-net45+win81` es compatible:</span><span class="sxs-lookup"><span data-stu-id="c8f30-355">If what you want to bring in is the latter DLL, then you can add a `PackageTargetFallback` as follows to say that the `portable-net45+win81` DLL is compatible:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netstandard1.6'">
    portable-net45+win81
</PackageTargetFallback>
```

<span data-ttu-id="c8f30-356">Para declarar una reserva para todos los destinos del proyecto, excluya el atributo `Condition`.</span><span class="sxs-lookup"><span data-stu-id="c8f30-356">To declare a fallback for all targets in your project, leave off the `Condition` attribute.</span></span> <span data-ttu-id="c8f30-357">También puede extender cualquier `PackageTargetFallback` existente mediante la inclusión de `$(PackageTargetFallback)` como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="c8f30-357">You can also extend any existing `PackageTargetFallback` by including `$(PackageTargetFallback)` as shown here:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win81
</PackageTargetFallback >
```

### <a name="replacing-one-library-from-a-restore-graph"></a><span data-ttu-id="c8f30-358">Reemplazo de una biblioteca desde un gráfico de restauración</span><span class="sxs-lookup"><span data-stu-id="c8f30-358">Replacing one library from a restore graph</span></span>

<span data-ttu-id="c8f30-359">Si una restauración agrega el ensamblado equivocado, se puede excluir la opción predeterminada de ese paquete y reemplazarla por una de su propia elección.</span><span class="sxs-lookup"><span data-stu-id="c8f30-359">If a restore is bringing the wrong assembly, it's possible to exclude that packages default choice, and replace it with your own choice.</span></span> <span data-ttu-id="c8f30-360">En primer lugar, con una `PackageReference` de nivel superior, excluya todos los activos:</span><span class="sxs-lookup"><span data-stu-id="c8f30-360">First with a top level `PackageReference`, exclude all assets:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1">
  <ExcludeAssets>All</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="c8f30-361">Después, agregue su propia referencia a la copia local correspondiente del archivo DLL:</span><span class="sxs-lookup"><span data-stu-id="c8f30-361">Next, add your own reference to the appropriate local copy of the DLL:</span></span>

```xml
<Reference Include="Newtonsoft.Json.dll" />
```