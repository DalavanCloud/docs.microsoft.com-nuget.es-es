---
title: "Guía de introducción a la creación y publicación de un paquete NuGet de .NET Framework con Visual Studio | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 03/13/2018
ms.topic: get-started-article
ms.prod: nuget
ms.technology: 
description: "Tutorial sobre la creación y publicación de un paquete NuGet de .NET Framework con Visual Studio 2017."
keywords: "Creación de paquetes NuGet, publicación de paquetes NuGet, tutorial de NuGet, creación en Visual Studio, paquete de NuGet, paquete msbuild"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 613cb6e8cf5762f354d69aa271c1e2f0d4851c97
ms.sourcegitcommit: 74c21b406302288c158e8ae26057132b12960be8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="create-and-publish-a-package-using-visual-studio-net-framework"></a><span data-ttu-id="4f051-104">Creación y publicación de un paquete con Visual Studio (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="4f051-104">Create and publish a package using Visual Studio (.NET Framework)</span></span>

<span data-ttu-id="4f051-105">Crear un paquete NuGet desde una biblioteca de clases de .NET Framework implica crear el archivo DLL en Visual Studio y, después, usar la herramienta de línea de comandos nuget.exe para crear y publicar el paquete.</span><span class="sxs-lookup"><span data-stu-id="4f051-105">Creating a NuGet package from a .NET Framework Class Library involves creating the DLL in Visual Studio, then using the nuget.exe command line tool to create and publish the package.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f051-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="4f051-106">Prerequisites</span></span>

1. <span data-ttu-id="4f051-107">Instale cualquier edición de Visual Studio 2017 desde [visualstudio.com](https://www.visualstudio.com/) con cualquier carga de trabajo relacionada con .NET.</span><span class="sxs-lookup"><span data-stu-id="4f051-107">Install any edition of Visual Studio 2017 from [visualstudio.com](https://www.visualstudio.com/) with any .NET-related workload.</span></span> <span data-ttu-id="4f051-108">Visual Studio de 2017 incluye automáticamente funcionalidades de NuGet cuando se instala una carga de trabajo. NET.</span><span class="sxs-lookup"><span data-stu-id="4f051-108">Visual Studio 2017 automatically includes NuGet capabilities when a .NET workload is installed.</span></span>

1. <span data-ttu-id="4f051-109">Instale la CLI de `nuget.exe` descargándola desde [nuget.org](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe), guarde el archivo `.exe` en la carpeta adecuada y agregue esa carpeta a la variable de entorno PATH.</span><span class="sxs-lookup"><span data-stu-id="4f051-109">Install the `nuget.exe` CLI by downloading it from [nuget.org](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe), saving that `.exe` file to a suitable folder, and adding that folder to your PATH environment variable.</span></span>

1. <span data-ttu-id="4f051-110">[Registrar una cuenta gratuita en nuget.org](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) si aún no tiene uno.</span><span class="sxs-lookup"><span data-stu-id="4f051-110">[Register for a free account on nuget.org](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) if you don't have one already.</span></span> <span data-ttu-id="4f051-111">Al crear una cuenta se envía un correo electrónico de confirmación.</span><span class="sxs-lookup"><span data-stu-id="4f051-111">Creating a new account sends a confirmation email.</span></span> <span data-ttu-id="4f051-112">Debe confirmar la cuenta para poder cargar un paquete.</span><span class="sxs-lookup"><span data-stu-id="4f051-112">You must confirm the account before you can upload a package.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="4f051-113">Crear un proyecto de biblioteca de clases</span><span class="sxs-lookup"><span data-stu-id="4f051-113">Create a class library project</span></span>

<span data-ttu-id="4f051-114">Puede usar un proyecto de biblioteca de clases .NET Framework existente para el código que quiere empaquetar o crear uno simple tal y como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="4f051-114">You can use an existing .NET Framework Class Library project for the code you want to package, or create a simple one as follows:</span></span>

1. <span data-ttu-id="4f051-115">En Visual Studio, seleccione **Archivo > Nuevo > Proyecto**, seleccione el nodo **Visual C#**, seleccione la plantilla "Biblioteca de clases (.NET Framework)", denomine el proyecto AppLogger y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4f051-115">In Visual Studio, choose **File > New > Project**, select the **Visual C#** node, select the "Class Library (.NET Framework)" template, name the project AppLogger, and click **OK**.</span></span>

1. <span data-ttu-id="4f051-116">Haga clic con el botón derecho en el archivo de proyecto resultante y seleccione **Compilar** para asegurarse de que el proyecto se ha creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="4f051-116">Right-click on the resulting project file and select **Build** to make sure the project was created properly.</span></span> <span data-ttu-id="4f051-117">El archivo DLL se encuentra en la carpeta Debug (o Release si en su lugar compila esa configuración).</span><span class="sxs-lookup"><span data-stu-id="4f051-117">The DLL is found within the Debug folder (or Release if you build that configuration instead).</span></span>

<span data-ttu-id="4f051-118">Por supuesto, dentro de un paquete NuGet real, se implementan muchas características útiles con las que otros usuarios pueden compilar aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4f051-118">Within a real NuGet package, of course, you implement many useful features with which others can build applications.</span></span> <span data-ttu-id="4f051-119">También puede establecer los marcos de destino como quiera.</span><span class="sxs-lookup"><span data-stu-id="4f051-119">You can also set the target frameworks however you like.</span></span> <span data-ttu-id="4f051-120">Por ejemplo, vea las guías de [UWP](../guides/create-uwp-packages.md) y [Xamarin](../guides/create-packages-for-xamarin.md).</span><span class="sxs-lookup"><span data-stu-id="4f051-120">For example, see the guides for [UWP](../guides/create-uwp-packages.md) and [Xamarin](../guides/create-packages-for-xamarin.md).</span></span>

<span data-ttu-id="4f051-121">Pero en este tutorial no escribirá código adicional porque para crear un paquete es suficiente con una biblioteca de clases desde la plantilla.</span><span class="sxs-lookup"><span data-stu-id="4f051-121">For this walkthrough, however, you won't write any additional code because a class library from the template is sufficient to create a package.</span></span> <span data-ttu-id="4f051-122">No obstante, si desea algún código funcional para el paquete, use lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4f051-122">Still, if you'd like some functional code for the package, use the following:</span></span>

```cs
using System;

namespace AppLogger
{
    public class Logger
    {
        public void Log(string text)
        {
            Console.WriteLine(text);
        }
    }
}
```

> [!Tip]
> <span data-ttu-id="4f051-123">A menos que tenga una razón para elegir otro, .NET Standard es el destino preferido para los paquetes NuGet, ya que proporciona compatibilidad con la gama más amplia de proyectos de consumo.</span><span class="sxs-lookup"><span data-stu-id="4f051-123">Unless you have a reason to choose otherwise, .NET Standard is the preferred target for NuGet packages, as it provides compatibility with the widest range of consuming projects.</span></span> <span data-ttu-id="4f051-124">Vea [Creación y publicación de un paquete de .NET Standard](create-and-publish-a-package-using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4f051-124">See [Create and publish a package using Visual Studio (.NET Standard)](create-and-publish-a-package-using-visual-studio.md).</span></span>

## <a name="configure-project-properties-for-the-package"></a><span data-ttu-id="4f051-125">Configurar las propiedades del proyecto para el paquete</span><span class="sxs-lookup"><span data-stu-id="4f051-125">Configure project properties for the package</span></span>

<span data-ttu-id="4f051-126">Un paquete NuGet contiene un manifiesto (un archivo `.nuspec`), que contiene metadatos relevantes, como el identificador del paquete, el número de versión, la descripción y mucho más.</span><span class="sxs-lookup"><span data-stu-id="4f051-126">A NuGet package contains a manifest (a `.nuspec` file), that contains relevant metadata such as the package identifier, version number, description, and more.</span></span> <span data-ttu-id="4f051-127">Algunas de ellas se pueden dibujar desde las propiedades del proyecto directamente, lo que evita tener que actualizarlas por separado en el proyecto y el manifiesto.</span><span class="sxs-lookup"><span data-stu-id="4f051-127">Some of these can be drawn from the project properties directly, which avoids having to separately update them in both the project and the manifest.</span></span> <span data-ttu-id="4f051-128">En esta sección se describe dónde establecer las propiedades aplicables.</span><span class="sxs-lookup"><span data-stu-id="4f051-128">This section describes where to set the applicable properties.</span></span>

1. <span data-ttu-id="4f051-129">Seleccione el comando de menú **Proyecto > Propiedades** y luego la pestaña **Aplicación**.</span><span class="sxs-lookup"><span data-stu-id="4f051-129">Select the **Project > Properties** menu command, then select the **Application** tab.</span></span>

1. <span data-ttu-id="4f051-130">En el campo **Nombre del ensamblado** asigne un identificador único al paquete.</span><span class="sxs-lookup"><span data-stu-id="4f051-130">In the **Assembly name** field, give your package a unique identifier.</span></span>

    > [!Important]
    > <span data-ttu-id="4f051-131">Debe asignar al paquete un identificador que sea único en nuget.org o en el host que use.</span><span class="sxs-lookup"><span data-stu-id="4f051-131">You must give the package an identifier that's unique across nuget.org or whatever host you're using.</span></span> <span data-ttu-id="4f051-132">En este tutorial, se recomienda incluir "muestra" o "prueba" en el nombre porque el paso de publicación posterior hace que el paquete sea visible públicamente (aunque no es probable que nadie lo use realmente).</span><span class="sxs-lookup"><span data-stu-id="4f051-132">For this walkthrough we recommend including "Sample" or "Test" in the name as the later publishing step does make the package publicly visible (though it's unlikely anyone will actually use it).</span></span>
    >
    > <span data-ttu-id="4f051-133">Si intenta publicar un paquete con un nombre que ya existe, verá un error.</span><span class="sxs-lookup"><span data-stu-id="4f051-133">If you attempt to publish a package with a name that already exists, you see an error.</span></span>

1. <span data-ttu-id="4f051-134">Seleccione el botón **Información de ensamblado**, que muestra un cuadro de diálogo en el que puede especificar otras propiedades que llevan al manifiesto (vea la sección Tokens de reemplazo en [Referencia de .nuspec](../reference/nuspec.md#replacement-tokens)).</span><span class="sxs-lookup"><span data-stu-id="4f051-134">Select the **Assembly Information...** button, which brings up a dialog box in which you can enter other properties that carry into the manifest (see [.nuspec file reference - replacement tokens](../reference/nuspec.md#replacement-tokens)).</span></span> <span data-ttu-id="4f051-135">Los campos más usados son **Título**, **Descripción**, **Empresa**, **Copyright** y **Versión de ensamblado**.</span><span class="sxs-lookup"><span data-stu-id="4f051-135">The most commonly used fields are **Title**, **Description**, **Company**, **Copyright**, and **Assembly version**.</span></span> <span data-ttu-id="4f051-136">Estas propiedades aparecen en última instancia con el paquete en un host como nuget.org, así que asegúrese de que sean lo más descriptivas posible.</span><span class="sxs-lookup"><span data-stu-id="4f051-136">These properties ultimately appear with your package on a host like nuget.org, so make sure they're fully descriptive.</span></span>

    ![Información de ensamblado en un proyecto de .NET Framework en Visual Studio](media/qs_create-vs-01b-project-properties.png)

1. <span data-ttu-id="4f051-138">Opcional: para ver y editar las propiedades directamente, abra el archivo `Properties/AssemblyInfo.cs` en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4f051-138">Optional: to see and edit the properties directly, open the `Properties/AssemblyInfo.cs` file in the project.</span></span>

1. <span data-ttu-id="4f051-139">Cuando se hayan establecido las propiedades, establezca la configuración de proyecto en **Versión** y recompile el proyecto para generar la DLL actualizada.</span><span class="sxs-lookup"><span data-stu-id="4f051-139">When the properties are set, set the project configuration to **Release** and rebuild the project to generate the updated DLL.</span></span>

## <a name="generate-the-initial-manifest"></a><span data-ttu-id="4f051-140">Generación del manifiesto inicial</span><span class="sxs-lookup"><span data-stu-id="4f051-140">Generate the initial manifest</span></span>

<span data-ttu-id="4f051-141">Una vez que tiene un archivo DLL y un conjunto de propiedades del proyecto, ya puede usar el comando `nuget spec` para generar un archivo `.nuspec` inicial desde el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4f051-141">With a DLL in hand and project properties set, you now use the `nuget spec` command to generate an initial `.nuspec` file from the project.</span></span> <span data-ttu-id="4f051-142">Este paso incluye los tokens de reemplazo correspondientes para extraer información del archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="4f051-142">This step includes the relevant replacement tokens to draw information from the project file.</span></span>

<span data-ttu-id="4f051-143">Ejecute `nuget spec` solo una vez para generar el manifiesto inicial.</span><span class="sxs-lookup"><span data-stu-id="4f051-143">You run `nuget spec` only once to generate the initial manifest.</span></span> <span data-ttu-id="4f051-144">Al actualizar el paquete, puede cambiar los valores en el proyecto o editar el manifiesto directamente.</span><span class="sxs-lookup"><span data-stu-id="4f051-144">When updating the package, you either change values in your project or edit the manifest directly.</span></span>

1. <span data-ttu-id="4f051-145">Abra un símbolo del sistema y desplácese hasta la carpeta del proyecto que contiene el archivo `AppLogger.csproj`.</span><span class="sxs-lookup"><span data-stu-id="4f051-145">Open a command prompt and navigate to the project folder containing `AppLogger.csproj` file.</span></span>

1. <span data-ttu-id="4f051-146">Ejecute el comando siguiente: `nuget spec AppLogger.csproj`.</span><span class="sxs-lookup"><span data-stu-id="4f051-146">Run the following command: `nuget spec AppLogger.csproj`.</span></span> <span data-ttu-id="4f051-147">Mediante la especificación de un proyecto, NuGet crea un manifiesto que coincide con el nombre del proyecto, en este caso `AppLogger.nuspec`.</span><span class="sxs-lookup"><span data-stu-id="4f051-147">By specifying a project, NuGet creates a manifest that matches the name of the project, in this case `AppLogger.nuspec`.</span></span> <span data-ttu-id="4f051-148">También se incluyen los tokens de reemplazo en el manifiesto.</span><span class="sxs-lookup"><span data-stu-id="4f051-148">It also include replacement tokens in the manifest.</span></span>

1. <span data-ttu-id="4f051-149">Abra `AppLogger.nuspec` en un editor de texto para examinar su contenido, que debería aparecer como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="4f051-149">Open `AppLogger.nuspec` in a text editor to examine its contents, which should appear as follows:</span></span>

    ```xml
    <?xml version="1.0"?>
    <package >
      <metadata>
        <id>$id$</id>
        <version>$version$</version>
        <title>$title$</title>
        <authors>$author$</authors>
        <owners>$author$</owners>
        <licenseUrl>http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE</licenseUrl>
        <projectUrl>http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE</projectUrl>
        <iconUrl>http://ICON_URL_HERE_OR_DELETE_THIS_LINE</iconUrl>
        <requireLicenseAcceptance>false</requireLicenseAcceptance>
        <description>$description$</description>
        <releaseNotes>Summary of changes made in this release of the package.</releaseNotes>
        <copyright>Copyright 2018</copyright>
        <tags>Tag1 Tag2</tags>
      </metadata>
    </package>
    ```

## <a name="edit-the-manifest"></a><span data-ttu-id="4f051-150">Edición del manifiesto</span><span class="sxs-lookup"><span data-stu-id="4f051-150">Edit the manifest</span></span>

1. <span data-ttu-id="4f051-151">NuGet genera un error si intenta crear un paquete con valores predeterminados en el archivo `.nuspec`, por lo que debe editar los campos que aquí se indican antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4f051-151">NuGet produces an error if you try to create a package with default values in your `.nuspec` file, so you must edit the following fields before proceeding.</span></span> <span data-ttu-id="4f051-152">Para una descripción de cómo se usan, vea el apartado Elementos únicos del tema [Referencia de .nuspec](../reference/nuspec.md#single-elements).</span><span class="sxs-lookup"><span data-stu-id="4f051-152">See [.nuspec file reference - single elements](../reference/nuspec.md#single-elements) for a description of how these are used.</span></span>

    - <span data-ttu-id="4f051-153">licenseUrl</span><span class="sxs-lookup"><span data-stu-id="4f051-153">licenseUrl</span></span>
    - <span data-ttu-id="4f051-154">projectUrl</span><span class="sxs-lookup"><span data-stu-id="4f051-154">projectUrl</span></span>
    - <span data-ttu-id="4f051-155">iconUrl</span><span class="sxs-lookup"><span data-stu-id="4f051-155">iconUrl</span></span>
    - <span data-ttu-id="4f051-156">releaseNotes</span><span class="sxs-lookup"><span data-stu-id="4f051-156">releaseNotes</span></span>
    - <span data-ttu-id="4f051-157">etiquetas</span><span class="sxs-lookup"><span data-stu-id="4f051-157">tags</span></span>

1. <span data-ttu-id="4f051-158">En el caso de los paquetes creados para consumo público, preste especial atención a la propiedad **Tags**, dado que estas etiquetas ayudan a otros usuarios a encontrar el paquete en orígenes como nuget.org y comprender lo que hace.</span><span class="sxs-lookup"><span data-stu-id="4f051-158">For packages built for public consumption, pay special attention to the **Tags** property, as tags help others find your package on sources like nuget.org and understand what it does.</span></span>

1. <span data-ttu-id="4f051-159">También puede agregar otros elementos para el manifiesto en este momento, como se describe en el tema [Referencia de .nuspec](../reference/nuspec.md).</span><span class="sxs-lookup"><span data-stu-id="4f051-159">You can also add any other elements to the manifest at this time, as described on [.nuspec file reference](../reference/nuspec.md).</span></span>

1. <span data-ttu-id="4f051-160">Guarde el archivo antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4f051-160">Save the file before proceeding.</span></span>

## <a name="run-the-pack-command"></a><span data-ttu-id="4f051-161">Ejecutar el comando pack</span><span class="sxs-lookup"><span data-stu-id="4f051-161">Run the pack command</span></span>

1. <span data-ttu-id="4f051-162">Desde un símbolo del sistema en la carpeta que contiene el archivo `.nuspec`, ejecute el comando `nuget pack`.</span><span class="sxs-lookup"><span data-stu-id="4f051-162">From a command prompt in the folder containing your `.nuspec` file, run the command `nuget pack`.</span></span>

1. <span data-ttu-id="4f051-163">NuGet genera un archivo `.nupkg` con el formato *versión-identificador.nupkg*, que encontrará en la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="4f051-163">NuGet generates a `.nupkg` file in the form of *identifier-version.nupkg*, which you'll find in the current folder.</span></span>

## <a name="publish-the-package"></a><span data-ttu-id="4f051-164">Publicar el paquete</span><span class="sxs-lookup"><span data-stu-id="4f051-164">Publish the package</span></span>

<span data-ttu-id="4f051-165">Cuando tenga un archivo `.nupkg`, publíquelo en nuget.org con el comando `nuget.exe` y una clave de API adquirida de nuget.org. Para nuget.org debe usar `nuget.exe` 4.1.0 o superior.</span><span class="sxs-lookup"><span data-stu-id="4f051-165">Once you have a `.nupkg` file, you publish it to nuget.org using `nuget.exe` with an API key acquired from nuget.org. For nuget.org you must use `nuget.exe` 4.1.0 or higher.</span></span>

[!INCLUDE[publish-notes](includes/publish-notes.md)]

### <a name="acquire-your-api-key"></a><span data-ttu-id="4f051-166">Adquirir la clave de API</span><span class="sxs-lookup"><span data-stu-id="4f051-166">Acquire your API key</span></span>

[!INCLUDE[publish-api-key](includes/publish-api-key.md)]

### <a name="publish-with-nuget-push"></a><span data-ttu-id="4f051-167">Publicar con nuget push</span><span class="sxs-lookup"><span data-stu-id="4f051-167">Publish with nuget push</span></span>

1. <span data-ttu-id="4f051-168">Cambie a la carpeta que contiene el archivo `.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="4f051-168">Change to the folder containing the `.nupkg` file.</span></span>

1. <span data-ttu-id="4f051-169">Ejecute el comando siguiente, especificando el nombre del paquete y reemplazando el valor de clave por la clave de API:</span><span class="sxs-lookup"><span data-stu-id="4f051-169">Run the following command, specifying your package name and replacing the key value with your API key:</span></span>

    ```cli
    nuget push AppLogger.1.0.0.nupkg qz2jga8pl3dvn2akksyquwcs9ygggg4exypy3bhxy6w6x6 -Source https://api.nuget.org/v3/index.json
    ```

1. <span data-ttu-id="4f051-170">nuget.exe muestra los resultados del proceso de publicación:</span><span class="sxs-lookup"><span data-stu-id="4f051-170">nuget.exe displays the results of the publishing process:</span></span>

    ```output
    Pushing AppLogger.1.0.0.nupkg to 'https://www.nuget.org/api/v2/package'...
        PUT https://www.nuget.org/api/v2/package/
        Created https://www.nuget.org/api/v2/package/ 6829ms
    Your package was pushed.
    ```

<span data-ttu-id="4f051-171">Vea [nuget push](../tools/cli-ref-push.md).</span><span class="sxs-lookup"><span data-stu-id="4f051-171">See [nuget push](../tools/cli-ref-push.md).</span></span>

### <a name="publish-errors"></a><span data-ttu-id="4f051-172">Errores de publicación</span><span class="sxs-lookup"><span data-stu-id="4f051-172">Publish errors</span></span>

[!INCLUDE[publish-errors](includes/publish-errors.md)]

### <a name="manage-the-published-package"></a><span data-ttu-id="4f051-173">Administrar el paquete publicado</span><span class="sxs-lookup"><span data-stu-id="4f051-173">Manage the published package</span></span>

[!INCLUDE[publish-manage](includes/publish-manage.md)]

## <a name="related-topics"></a><span data-ttu-id="4f051-174">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="4f051-174">Related topics</span></span>

- [<span data-ttu-id="4f051-175">Crear un paquete</span><span class="sxs-lookup"><span data-stu-id="4f051-175">Create a Package</span></span>](../create-packages/creating-a-package.md)
- [<span data-ttu-id="4f051-176">Publicar un paquete</span><span class="sxs-lookup"><span data-stu-id="4f051-176">Publish a Package</span></span>](../create-packages/publish-a-package.md)
- [<span data-ttu-id="4f051-177">Admitir varias plataformas de destino</span><span class="sxs-lookup"><span data-stu-id="4f051-177">Support multiple target frameworks</span></span>](../create-packages/supporting-multiple-target-frameworks.md)
- [<span data-ttu-id="4f051-178">Control de versiones del paquete</span><span class="sxs-lookup"><span data-stu-id="4f051-178">Package versioning</span></span>](../reference/package-versioning.md)
- [<span data-ttu-id="4f051-179">Creación de paquetes localizados</span><span class="sxs-lookup"><span data-stu-id="4f051-179">Creating localized packages</span></span>](../create-packages/creating-localized-packages.md)